---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 配置数据中的凭据选项
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046635"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="94739-103">配置数据中的凭据选项</span><span class="sxs-lookup"><span data-stu-id="94739-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="94739-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="94739-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="94739-105">纯文本密码和域用户</span><span class="sxs-lookup"><span data-stu-id="94739-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="94739-106">包含凭据但未加密的 DSC 配置会生成一条关于纯文本密码的错误信息。</span><span class="sxs-lookup"><span data-stu-id="94739-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="94739-107">此外，使用域凭据时 DSC 会生成一个警告。</span><span class="sxs-lookup"><span data-stu-id="94739-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="94739-108">要禁止显示这些错误和警告信息，可以使用 DSC 配置数据关键字：</span><span class="sxs-lookup"><span data-stu-id="94739-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="94739-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="94739-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="94739-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="94739-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="94739-111">存储/传输未加密的纯文本密码通常是不安全的。</span><span class="sxs-lookup"><span data-stu-id="94739-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="94739-112">建议使用此主题后面部分讨论的方法保护凭据。</span><span class="sxs-lookup"><span data-stu-id="94739-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="94739-113">Azure Automation DSC 服务可用于集中管理要在配置中编译并安全存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="94739-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="94739-114">有关详细信息，请参阅：[编译 DSC 配置 / 凭据资产](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="94739-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="94739-115">下面是关于传递纯文本凭据的示例：</span><span class="sxs-lookup"><span data-stu-id="94739-115">The following is an example of passing plain text credentials:</span></span>

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
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $promptedCreds
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }
}

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

<span data-ttu-id="94739-116">这是一段摘录"TestMachine1"的配置生成的".mof"文件。</span><span class="sxs-lookup"><span data-stu-id="94739-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="94739-117">`System.Security.SecureString`中使用配置被转换为纯文本，且存储在".mof"文件作为`MSF_Credential`。</span><span class="sxs-lookup"><span data-stu-id="94739-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="94739-118">一个`SecureString`使用当前用户配置文件进行加密。</span><span class="sxs-lookup"><span data-stu-id="94739-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="94739-119">这适用于 PowerShell 远程管理的所有窗体。</span><span class="sxs-lookup"><span data-stu-id="94739-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="94739-120">".Mof"文件被旨在作为一个独立单独配置机制。</span><span class="sxs-lookup"><span data-stu-id="94739-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="94739-121">从 PowerShell 5.0 开始，在节点上的".mof"文件进行加密静态，但不是在传输到的节点。</span><span class="sxs-lookup"><span data-stu-id="94739-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="94739-122">这意味着".mof"文件中的密码会以明文形式公开，当应用于节点。</span><span class="sxs-lookup"><span data-stu-id="94739-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="94739-123">若要加密的凭据，您需要使用**拉服务器**。</span><span class="sxs-lookup"><span data-stu-id="94739-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="94739-124">有关详细信息，请参阅[使用证书保护 MOF 文件](../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="94739-124">For more information, see [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="94739-125">在 DSC 中处理凭据</span><span class="sxs-lookup"><span data-stu-id="94739-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="94739-126">默认情况下，DSC 配置资源以 `Local System` 运行。</span><span class="sxs-lookup"><span data-stu-id="94739-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="94739-127">但某些资源需要凭据，例如 `Package` 资源需要使用特定用户帐户安装软件。</span><span class="sxs-lookup"><span data-stu-id="94739-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="94739-128">早期的资源使用硬编码 `Credential` 属性名称来处理此问题。</span><span class="sxs-lookup"><span data-stu-id="94739-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="94739-129">WMF 5.0 为所有资源都添加了自动 `PsDscRunAsCredential` 属性。</span><span class="sxs-lookup"><span data-stu-id="94739-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="94739-130">若要了解如何使用 `PsDscRunAsCredential`，请参阅[使用用户凭据运行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="94739-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="94739-131">较新的资源和自定义资源可以使用此自动属性，而不必为凭据创建其自身属性。</span><span class="sxs-lookup"><span data-stu-id="94739-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="94739-132">由于某种原因，某些资源的设计将使用多个凭据，这些凭据有其自己的凭据属性。</span><span class="sxs-lookup"><span data-stu-id="94739-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="94739-133">使用 ISE 中的 Intellisense (`CTRL+SPACE`) 或 `Get-DscResource -Name ResourceName -Syntax` 来查找资源的可用凭据属性。</span><span class="sxs-lookup"><span data-stu-id="94739-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="94739-134">此示例使用来自 `PSDesiredStateConfiguration` 内置 DSC 资源模块中的 [Group](../resources/resources.md) 资源。</span><span class="sxs-lookup"><span data-stu-id="94739-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="94739-135">它可以创建本地组并添加或删除成员。</span><span class="sxs-lookup"><span data-stu-id="94739-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="94739-136">它同时接受 `Credential` 属性和自动 `PsDscRunAsCredential` 属性。</span><span class="sxs-lookup"><span data-stu-id="94739-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="94739-137">但是该资源只使用 `Credential` 属性。</span><span class="sxs-lookup"><span data-stu-id="94739-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="94739-138">有关 `PsDscRunAsCredential` 属性的详细信息，请参阅[使用用户凭据运行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="94739-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="94739-139">例如：Group 资源 Credential 属性</span><span class="sxs-lookup"><span data-stu-id="94739-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="94739-140">DSC 在 `Local System` 下运行，因此它已经有权更改本地用户和组。</span><span class="sxs-lookup"><span data-stu-id="94739-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="94739-141">如果添加的成员是本地帐户，则无需凭据。</span><span class="sxs-lookup"><span data-stu-id="94739-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="94739-142">如果 `Group` 资源要添加一个域帐户到本地组，则需要凭据。</span><span class="sxs-lookup"><span data-stu-id="94739-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="94739-143">不允许匿名查询 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="94739-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="94739-144">`Group` 资源的 `Credential` 属性是用于查询 Active Directory 的域帐户。</span><span class="sxs-lookup"><span data-stu-id="94739-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="94739-145">大多数情况下这是个一般用户帐户，因为默认情况下用户可以*读取* Active Directory 中的大多数对象。</span><span class="sxs-lookup"><span data-stu-id="94739-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="94739-146">示例配置</span><span class="sxs-lookup"><span data-stu-id="94739-146">Example Configuration</span></span>

<span data-ttu-id="94739-147">下面的示例代码使用 DSC 来填充带有域用户的本地组：</span><span class="sxs-lookup"><span data-stu-id="94739-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="94739-148">此代码生成了错误和警告消息：</span><span class="sxs-lookup"><span data-stu-id="94739-148">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="94739-149">此示例有两个问题：</span><span class="sxs-lookup"><span data-stu-id="94739-149">This example has two issues:</span></span>
1. <span data-ttu-id="94739-150">错误消息说明不推荐使用纯文本密码</span><span class="sxs-lookup"><span data-stu-id="94739-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="94739-151">警告消息建议不要使用域凭据</span><span class="sxs-lookup"><span data-stu-id="94739-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="94739-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="94739-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="94739-153">第一条错误消息具有一个带有文档的 URL。</span><span class="sxs-lookup"><span data-stu-id="94739-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="94739-154">此链接说明如何使用 [ConfigurationData](./configData.md) 结构和证书来加密密码。</span><span class="sxs-lookup"><span data-stu-id="94739-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="94739-155">有关证书和 DSC 的详细信息，[请阅读此文章](http://aka.ms/certs4dsc)。</span><span class="sxs-lookup"><span data-stu-id="94739-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="94739-156">要强制使用纯文本密码，资源需要下列配置数据部分中的 `PsDscAllowPlainTextPassword` 关键字：</span><span class="sxs-lookup"><span data-stu-id="94739-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="94739-157">`NodeName` 不等同于星号，必须指定具体的节点名称。</span><span class="sxs-lookup"><span data-stu-id="94739-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="94739-158">**因为存在重大安全风险，Microsoft 建议避免使用纯文本密码。**</span><span class="sxs-lookup"><span data-stu-id="94739-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="94739-159">域凭据</span><span class="sxs-lookup"><span data-stu-id="94739-159">Domain Credentials</span></span>

<span data-ttu-id="94739-160">再次运行示例配置脚本（加密或不加密），仍然生成警告消息说不推荐将域帐户用于凭据。</span><span class="sxs-lookup"><span data-stu-id="94739-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="94739-161">使用本地帐户可消除泄露可用于其他服务器的域凭据的可能性。</span><span class="sxs-lookup"><span data-stu-id="94739-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="94739-162">**对 DSC 资源使用凭据时，应尽可能选择本地帐户而非域帐户。**</span><span class="sxs-lookup"><span data-stu-id="94739-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="94739-163">如果凭据的 `Username` 属性中有 \' 或 @，则 DSC 会将该凭据视为域帐户。</span><span class="sxs-lookup"><span data-stu-id="94739-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="94739-164">用户名中域部分的“localhost”、“127.0.0.1”和“::1”除外。</span><span class="sxs-lookup"><span data-stu-id="94739-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="94739-165">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="94739-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="94739-166">在上述 DSC `Group` 资源示例中，查询 Active Directory 域*必须使用*域帐户。</span><span class="sxs-lookup"><span data-stu-id="94739-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="94739-167">在这种情况下，将 `PSDscAllowDomainUser` 属性添加到 `ConfigurationData` 块中，操作如下：</span><span class="sxs-lookup"><span data-stu-id="94739-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="94739-168">现在配置脚本生成的 MOF 文件将不再出现错误或警告消息。</span><span class="sxs-lookup"><span data-stu-id="94739-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
