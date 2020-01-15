---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 配置数据中的凭据选项
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870551"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="68af9-103">配置数据中的凭据选项</span><span class="sxs-lookup"><span data-stu-id="68af9-103">Credentials Options in Configuration Data</span></span>

> <span data-ttu-id="68af9-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="68af9-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="68af9-105">纯文本密码和域用户</span><span class="sxs-lookup"><span data-stu-id="68af9-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="68af9-106">包含凭据但未加密的 DSC 配置会生成一条关于纯文本密码的错误信息。</span><span class="sxs-lookup"><span data-stu-id="68af9-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span> <span data-ttu-id="68af9-107">此外，使用域凭据时 DSC 会生成一个警告。</span><span class="sxs-lookup"><span data-stu-id="68af9-107">Also, DSC will generate a warning when using domain credentials.</span></span> <span data-ttu-id="68af9-108">要禁止显示这些错误和警告信息，可以使用 DSC 配置数据关键字：</span><span class="sxs-lookup"><span data-stu-id="68af9-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="68af9-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="68af9-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="68af9-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="68af9-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="68af9-111">存储/传输未加密的纯文本密码通常是不安全的。</span><span class="sxs-lookup"><span data-stu-id="68af9-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="68af9-112">建议使用此主题后面部分讨论的方法保护凭据。</span><span class="sxs-lookup"><span data-stu-id="68af9-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span> <span data-ttu-id="68af9-113">Azure Automation DSC 服务可用于集中管理要在配置中编译并安全存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="68af9-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span> <span data-ttu-id="68af9-114">相关信息，请参阅：[编译 DSC 配置/凭据资产](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="68af9-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="68af9-115">在 DSC 中处理凭据</span><span class="sxs-lookup"><span data-stu-id="68af9-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="68af9-116">默认情况下，DSC 配置资源以 `Local System` 运行。</span><span class="sxs-lookup"><span data-stu-id="68af9-116">DSC configuration resources run as `Local System` by default.</span></span> <span data-ttu-id="68af9-117">但某些资源需要凭据，例如 `Package` 资源需要使用特定用户帐户安装软件。</span><span class="sxs-lookup"><span data-stu-id="68af9-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="68af9-118">早期的资源使用硬编码 `Credential` 属性名称来处理此问题。</span><span class="sxs-lookup"><span data-stu-id="68af9-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span> <span data-ttu-id="68af9-119">WMF 5.0 为所有资源都添加了自动 `PsDscRunAsCredential` 属性。</span><span class="sxs-lookup"><span data-stu-id="68af9-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="68af9-120">若要了解如何使用 `PsDscRunAsCredential`，请参阅[使用用户凭据运行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="68af9-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span> <span data-ttu-id="68af9-121">较新的资源和自定义资源可以使用此自动属性，而不必为凭据创建其自身属性。</span><span class="sxs-lookup"><span data-stu-id="68af9-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="68af9-122">由于某种原因，某些资源的设计将使用多个凭据，这些凭据有其自己的凭据属性。</span><span class="sxs-lookup"><span data-stu-id="68af9-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="68af9-123">使用 ISE 中的 Intellisense (`CTRL+SPACE`) 或 `Get-DscResource -Name ResourceName -Syntax` 来查找资源的可用凭据属性。</span><span class="sxs-lookup"><span data-stu-id="68af9-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
Get-DscResource -Name Group -Syntax
```

```Output
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

<span data-ttu-id="68af9-124">此示例使用来自 `PSDesiredStateConfiguration` 内置 DSC 资源模块中的 [Group](../resources/resources.md) 资源。</span><span class="sxs-lookup"><span data-stu-id="68af9-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span> <span data-ttu-id="68af9-125">它可以创建本地组并添加或删除成员。</span><span class="sxs-lookup"><span data-stu-id="68af9-125">It can create local groups and add or remove members.</span></span> <span data-ttu-id="68af9-126">它同时接受 `Credential` 属性和自动 `PsDscRunAsCredential` 属性。</span><span class="sxs-lookup"><span data-stu-id="68af9-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span> <span data-ttu-id="68af9-127">但是该资源只使用 `Credential` 属性。</span><span class="sxs-lookup"><span data-stu-id="68af9-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="68af9-128">有关 `PsDscRunAsCredential` 属性的详细信息，请参阅[使用用户凭据运行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="68af9-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="68af9-129">示例：Group 资源 Credential 属性</span><span class="sxs-lookup"><span data-stu-id="68af9-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="68af9-130">DSC 在 `Local System` 下运行，因此它已经有权更改本地用户和组。</span><span class="sxs-lookup"><span data-stu-id="68af9-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span> <span data-ttu-id="68af9-131">如果添加的成员是本地帐户，则无需凭据。</span><span class="sxs-lookup"><span data-stu-id="68af9-131">If the member added is a local account, then no credential is necessary.</span></span> <span data-ttu-id="68af9-132">如果 `Group` 资源要添加一个域帐户到本地组，则需要凭据。</span><span class="sxs-lookup"><span data-stu-id="68af9-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="68af9-133">不允许匿名查询 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="68af9-133">Anonymous queries to Active Directory are not allowed.</span></span> <span data-ttu-id="68af9-134">`Group` 资源的 `Credential` 属性是用于查询 Active Directory 的域帐户。</span><span class="sxs-lookup"><span data-stu-id="68af9-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span> <span data-ttu-id="68af9-135">大多数情况下这是个一般用户帐户，因为默认情况下用户可以*读取* Active Directory 中的大多数对象。</span><span class="sxs-lookup"><span data-stu-id="68af9-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="68af9-136">示例配置</span><span class="sxs-lookup"><span data-stu-id="68af9-136">Example Configuration</span></span>

<span data-ttu-id="68af9-137">下面的示例代码使用 DSC 来填充带有域用户的本地组：</span><span class="sxs-lookup"><span data-stu-id="68af9-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="68af9-138">此代码生成了错误和警告消息：</span><span class="sxs-lookup"><span data-stu-id="68af9-138">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

<span data-ttu-id="68af9-139">此示例有两个问题：</span><span class="sxs-lookup"><span data-stu-id="68af9-139">This example has two issues:</span></span>

1. <span data-ttu-id="68af9-140">错误消息说明不推荐使用纯文本密码</span><span class="sxs-lookup"><span data-stu-id="68af9-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="68af9-141">警告消息建议不要使用域凭据</span><span class="sxs-lookup"><span data-stu-id="68af9-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="68af9-142">标记 PSDSCAllowPlainTextPassword  和 PSDSCAllowDomainUser  禁止显示告知用户所涉及风险的错误和警告。</span><span class="sxs-lookup"><span data-stu-id="68af9-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="68af9-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="68af9-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="68af9-144">第一条错误消息具有一个带有文档的 URL。</span><span class="sxs-lookup"><span data-stu-id="68af9-144">The first error message has a URL with documentation.</span></span> <span data-ttu-id="68af9-145">此链接说明如何使用 [ConfigurationData](./configData.md) 结构和证书来加密密码。</span><span class="sxs-lookup"><span data-stu-id="68af9-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span> <span data-ttu-id="68af9-146">有关证书和 DSC 的详细信息，[请阅读此文章](https://aka.ms/certs4dsc)。</span><span class="sxs-lookup"><span data-stu-id="68af9-146">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="68af9-147">要强制使用纯文本密码，资源需要下列配置数据部分中的 `PsDscAllowPlainTextPassword` 关键字：</span><span class="sxs-lookup"><span data-stu-id="68af9-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
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

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a><span data-ttu-id="68af9-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="68af9-148">localhost.mof</span></span>

<span data-ttu-id="68af9-149">PSDSCAllowPlainTextPassword  标记要求用户确认将纯文本密码存储在 MOF 文件中的风险。</span><span class="sxs-lookup"><span data-stu-id="68af9-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="68af9-150">在生成的 MOF 文件中，即使使用了包含 SecureString  的 PSCredential  对象，密码仍以纯文本形式出现。</span><span class="sxs-lookup"><span data-stu-id="68af9-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="68af9-151">这是唯一一次公开凭据。</span><span class="sxs-lookup"><span data-stu-id="68af9-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="68af9-152">获得对此 MOF 文件的访问权限后，任何人都可以访问管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="68af9-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="68af9-153">传输中的凭据和静止状态下的凭据</span><span class="sxs-lookup"><span data-stu-id="68af9-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="68af9-154">PSDscAllowPlainTextPassword  标记允许编译包含明文形式密码的 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="68af9-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span> <span data-ttu-id="68af9-155">在存储包含明文密码的 MOF 文件时，应采取预防措施。</span><span class="sxs-lookup"><span data-stu-id="68af9-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="68af9-156">在推送  模式下将 MOF 文件传递给节点时，WinRM 会对通信进行加密，以保护明文密码，除非使用 AllowUnencrypted  参数覆盖默认值。</span><span class="sxs-lookup"><span data-stu-id="68af9-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="68af9-157">使用证书加密 MOF 可以在将 MOF 文件应用于节点之前保护处于静止状态的 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="68af9-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="68af9-158">在拉取  模式下，可以配置 Windows 拉取服务器，以便通过 Internet 信息服务器中指定的协议使用 HTTPS 加密通信。</span><span class="sxs-lookup"><span data-stu-id="68af9-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="68af9-159">有关详细信息，请参阅文章[设置 DSC 拉取客户端](../pull-server/pullclient.md)和[使用证书保护 MOF 文件](../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="68af9-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="68af9-160">在 [Azure 自动化状态配置](/azure/automation/automation-dsc-overview)服务中，始终加密拉取流量。</span><span class="sxs-lookup"><span data-stu-id="68af9-160">In the [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="68af9-161">从 PowerShell 5.0 开始，节点上的 MOF 文件在静态时加密。</span><span class="sxs-lookup"><span data-stu-id="68af9-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="68af9-162">在 PowerShell 4.0 中，MOF 文件在静态时不加密，除非它们在被推送或拉取到节点时使用证书加密。</span><span class="sxs-lookup"><span data-stu-id="68af9-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="68af9-163">**因为存在重大安全风险，Microsoft 建议避免使用纯文本密码。**</span><span class="sxs-lookup"><span data-stu-id="68af9-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="68af9-164">域凭据</span><span class="sxs-lookup"><span data-stu-id="68af9-164">Domain Credentials</span></span>

<span data-ttu-id="68af9-165">再次运行示例配置脚本（加密或不加密），仍然生成警告消息说不推荐将域帐户用于凭据。</span><span class="sxs-lookup"><span data-stu-id="68af9-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span> <span data-ttu-id="68af9-166">使用本地帐户可消除泄露可用于其他服务器的域凭据的可能性。</span><span class="sxs-lookup"><span data-stu-id="68af9-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="68af9-167">**对 DSC 资源使用凭据时，应尽可能选择本地帐户而非域帐户。**</span><span class="sxs-lookup"><span data-stu-id="68af9-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="68af9-168">如果凭据的 `Username` 属性中有“\\”或“\@”，DSC 会将它视为域帐户。</span><span class="sxs-lookup"><span data-stu-id="68af9-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span> <span data-ttu-id="68af9-169">用户名中域部分的“localhost”、“127.0.0.1”和“::1”除外。</span><span class="sxs-lookup"><span data-stu-id="68af9-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="68af9-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="68af9-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="68af9-171">在上述 DSC `Group` 资源示例中，查询 Active Directory 域*必须使用*域帐户。</span><span class="sxs-lookup"><span data-stu-id="68af9-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span> <span data-ttu-id="68af9-172">在这种情况下，将 `PSDscAllowDomainUser` 属性添加到 `ConfigurationData` 块中，操作如下：</span><span class="sxs-lookup"><span data-stu-id="68af9-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

<span data-ttu-id="68af9-173">现在配置脚本生成的 MOF 文件将不再出现错误或警告消息。</span><span class="sxs-lookup"><span data-stu-id="68af9-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
