---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 配置数据中的凭据选项
ms.openlocfilehash: 2c6685f3b6992537d1652f172cf926b85dd634c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="62460-103">配置数据中的凭据选项</span><span class="sxs-lookup"><span data-stu-id="62460-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="62460-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="62460-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="62460-105">纯文本密码和域用户</span><span class="sxs-lookup"><span data-stu-id="62460-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="62460-106">包含凭据但未加密的 DSC 配置会生成一条关于纯文本密码的错误信息。</span><span class="sxs-lookup"><span data-stu-id="62460-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="62460-107">此外，使用域凭据时 DSC 会生成一个警告。</span><span class="sxs-lookup"><span data-stu-id="62460-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="62460-108">要禁止显示这些错误和警告信息，可以使用 DSC 配置数据关键字：</span><span class="sxs-lookup"><span data-stu-id="62460-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="62460-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="62460-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="62460-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="62460-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="62460-111">存储/传输未加密的纯文本密码通常是不安全的。</span><span class="sxs-lookup"><span data-stu-id="62460-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="62460-112">建议使用此主题后面部分讨论的方法保护凭据。</span><span class="sxs-lookup"><span data-stu-id="62460-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="62460-113">Azure Automation DSC 服务可用于集中管理要在配置中编译并安全存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="62460-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="62460-114">相关信息，请参阅：[编译 DSC 配置/凭据资产](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="62460-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="62460-115">下面是关于传递纯文本凭据的示例：</span><span class="sxs-lookup"><span data-stu-id="62460-115">The following is an example of passing plain text credentials:</span></span>

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="62460-116">在 DSC 中处理凭据</span><span class="sxs-lookup"><span data-stu-id="62460-116">Handling Credentials in DSC</span></span>

<span data-ttu-id="62460-117">默认情况下，DSC 配置资源以 `Local System` 运行。</span><span class="sxs-lookup"><span data-stu-id="62460-117">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="62460-118">但某些资源需要凭据，例如 `Package` 资源需要使用特定用户帐户安装软件。</span><span class="sxs-lookup"><span data-stu-id="62460-118">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="62460-119">早期的资源使用硬编码 `Credential` 属性名称来处理此问题。</span><span class="sxs-lookup"><span data-stu-id="62460-119">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="62460-120">WMF 5.0 为所有资源都添加了自动 `PsDscRunAsCredential` 属性。</span><span class="sxs-lookup"><span data-stu-id="62460-120">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="62460-121">若要了解如何使用 `PsDscRunAsCredential`，请参阅[使用用户凭据运行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="62460-121">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="62460-122">较新的资源和自定义资源可以使用此自动属性，而不必为凭据创建其自身属性。</span><span class="sxs-lookup"><span data-stu-id="62460-122">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="62460-123">由于某种原因，某些资源的设计将使用多个凭据，这些凭据有其自己的凭据属性。</span><span class="sxs-lookup"><span data-stu-id="62460-123">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="62460-124">使用 ISE 中的 Intellisense (`CTRL+SPACE`) 或 `Get-DscResource -Name ResourceName -Syntax` 来查找资源的可用凭据属性。</span><span class="sxs-lookup"><span data-stu-id="62460-124">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="62460-125">此示例使用来自 `PSDesiredStateConfiguration` 内置 DSC 资源模块中的 [Group](https://msdn.microsoft.com/powershell/dsc/groupresource) 资源。</span><span class="sxs-lookup"><span data-stu-id="62460-125">This example uses a [Group](https://msdn.microsoft.com/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="62460-126">它可以创建本地组并添加或删除成员。</span><span class="sxs-lookup"><span data-stu-id="62460-126">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="62460-127">它同时接受 `Credential` 属性和自动 `PsDscRunAsCredential` 属性。</span><span class="sxs-lookup"><span data-stu-id="62460-127">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="62460-128">但是该资源只使用 `Credential` 属性。</span><span class="sxs-lookup"><span data-stu-id="62460-128">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="62460-129">有关 `PsDscRunAsCredential` 属性的详细信息，请参阅[使用用户凭据运行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="62460-129">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="62460-130">示例：Group 资源 Credential 属性</span><span class="sxs-lookup"><span data-stu-id="62460-130">Example: The Group resource Credential property</span></span>

<span data-ttu-id="62460-131">DSC 在 `Local System` 下运行，因此它已经有权更改本地用户和组。</span><span class="sxs-lookup"><span data-stu-id="62460-131">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="62460-132">如果添加的成员是本地帐户，则无需凭据。</span><span class="sxs-lookup"><span data-stu-id="62460-132">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="62460-133">如果 `Group` 资源要添加一个域帐户到本地组，则需要凭据。</span><span class="sxs-lookup"><span data-stu-id="62460-133">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="62460-134">不允许匿名查询 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="62460-134">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="62460-135">`Group` 资源的 `Credential` 属性是用于查询 Active Directory 的域帐户。</span><span class="sxs-lookup"><span data-stu-id="62460-135">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="62460-136">大多数情况下这是个一般用户帐户，因为默认情况下用户可以*读取* Active Directory 中的大多数对象。</span><span class="sxs-lookup"><span data-stu-id="62460-136">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="62460-137">示例配置</span><span class="sxs-lookup"><span data-stu-id="62460-137">Example Configuration</span></span>

<span data-ttu-id="62460-138">下面的示例代码使用 DSC 来填充带有域用户的本地组：</span><span class="sxs-lookup"><span data-stu-id="62460-138">The following example code uses DSC to populate a local group with a domain user:</span></span>

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

<span data-ttu-id="62460-139">此代码生成了错误和警告消息：</span><span class="sxs-lookup"><span data-stu-id="62460-139">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

<span data-ttu-id="62460-140">此示例有两个问题：</span><span class="sxs-lookup"><span data-stu-id="62460-140">This example has two issues:</span></span>
1. <span data-ttu-id="62460-141">错误消息说明不推荐使用纯文本密码</span><span class="sxs-lookup"><span data-stu-id="62460-141">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="62460-142">警告消息建议不要使用域凭据</span><span class="sxs-lookup"><span data-stu-id="62460-142">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="62460-143">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="62460-143">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="62460-144">第一条错误消息具有一个带有文档的 URL。</span><span class="sxs-lookup"><span data-stu-id="62460-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="62460-145">此链接说明如何使用 [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) 结构和证书来加密密码。</span><span class="sxs-lookup"><span data-stu-id="62460-145">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="62460-146">有关证书和 DSC 的详细信息，[请阅读此文章](http://aka.ms/certs4dsc)。</span><span class="sxs-lookup"><span data-stu-id="62460-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="62460-147">要强制使用纯文本密码，资源需要下列配置数据部分中的 `PsDscAllowPlainTextPassword` 关键字：</span><span class="sxs-lookup"><span data-stu-id="62460-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="62460-148">`NodeName` 不等同于星号，必须指定具体的节点名称。</span><span class="sxs-lookup"><span data-stu-id="62460-148">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="62460-149">**因为存在重大安全风险，Microsoft 建议避免使用纯文本密码。**</span><span class="sxs-lookup"><span data-stu-id="62460-149">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

<span data-ttu-id="62460-150">使用 Azure Automation DSC 服务时例外，原因是数据始终加密存储（传输中、服务中静态或节点中静态）。</span><span class="sxs-lookup"><span data-stu-id="62460-150">An exception would be when using the Azure Automation DSC service, only because the data is always stored encrypted (in transit, at rest in the service, and at rest on the node).</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="62460-151">域凭据</span><span class="sxs-lookup"><span data-stu-id="62460-151">Domain Credentials</span></span>

<span data-ttu-id="62460-152">再次运行示例配置脚本（加密或不加密），仍然生成警告消息说不推荐将域帐户用于凭据。</span><span class="sxs-lookup"><span data-stu-id="62460-152">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="62460-153">使用本地帐户可消除泄露可用于其他服务器的域凭据的可能性。</span><span class="sxs-lookup"><span data-stu-id="62460-153">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="62460-154">**对 DSC 资源使用凭据时，应尽可能选择本地帐户而非域帐户。**</span><span class="sxs-lookup"><span data-stu-id="62460-154">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="62460-155">如果凭据的 `Username` 属性中有 \' 或 @，则 DSC 会将该凭据视为域帐户。</span><span class="sxs-lookup"><span data-stu-id="62460-155">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="62460-156">用户名中域部分的“localhost”、“127.0.0.1”和“::1”除外。</span><span class="sxs-lookup"><span data-stu-id="62460-156">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="62460-157">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="62460-157">PSDscAllowDomainUser</span></span>

<span data-ttu-id="62460-158">在上述 DSC `Group` 资源示例中，查询 Active Directory 域*必须使用*域帐户。</span><span class="sxs-lookup"><span data-stu-id="62460-158">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="62460-159">在这种情况下，将 `PSDscAllowDomainUser` 属性添加到 `ConfigurationData` 块中，操作如下：</span><span class="sxs-lookup"><span data-stu-id="62460-159">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

<span data-ttu-id="62460-160">现在配置脚本生成的 MOF 文件将不再出现错误或警告消息。</span><span class="sxs-lookup"><span data-stu-id="62460-160">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>