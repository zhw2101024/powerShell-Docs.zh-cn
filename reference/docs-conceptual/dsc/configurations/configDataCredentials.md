---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 配置数据中的凭据选项
ms.openlocfilehash: 660c3643f7eb2e9ccb91bd992747fb9d5da0ccdb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954534"
---
# <a name="credentials-options-in-configuration-data"></a>配置数据中的凭据选项

>适用于：Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>纯文本密码和域用户

包含凭据但未加密的 DSC 配置会生成一条关于纯文本密码的错误信息。
此外，使用域凭据时 DSC 会生成一个警告。
要禁止显示这些错误和警告信息，可以使用 DSC 配置数据关键字：

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> 存储/传输未加密的纯文本密码通常是不安全的。 建议使用此主题后面部分讨论的方法保护凭据。
> Azure Automation DSC 服务可用于集中管理要在配置中编译并安全存储的凭据。
> 相关信息，请参阅：[编译 DSC 配置/凭据资产](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>在 DSC 中处理凭据

默认情况下，DSC 配置资源以 `Local System` 运行。
但某些资源需要凭据，例如 `Package` 资源需要使用特定用户帐户安装软件。

早期的资源使用硬编码 `Credential` 属性名称来处理此问题。
WMF 5.0 为所有资源都添加了自动 `PsDscRunAsCredential` 属性。
若要了解如何使用 `PsDscRunAsCredential`，请参阅[使用用户凭据运行 DSC](runAsUser.md)。
较新的资源和自定义资源可以使用此自动属性，而不必为凭据创建其自身属性。

> [!NOTE]
> 由于某种原因，某些资源的设计将使用多个凭据，这些凭据有其自己的凭据属性。

使用 ISE 中的 Intellisense (`CTRL+SPACE`) 或 `Get-DscResource -Name ResourceName -Syntax` 来查找资源的可用凭据属性。

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

此示例使用来自 `PSDesiredStateConfiguration` 内置 DSC 资源模块中的 [Group](../resources/resources.md) 资源。
它可以创建本地组并添加或删除成员。
它同时接受 `Credential` 属性和自动 `PsDscRunAsCredential` 属性。
但是该资源只使用 `Credential` 属性。

有关 `PsDscRunAsCredential` 属性的详细信息，请参阅[使用用户凭据运行 DSC](runAsUser.md)。

## <a name="example-the-group-resource-credential-property"></a>例如：Group 资源 Credential 属性

DSC 在 `Local System` 下运行，因此它已经有权更改本地用户和组。
如果添加的成员是本地帐户，则无需凭据。
如果 `Group` 资源要添加一个域帐户到本地组，则需要凭据。

不允许匿名查询 Active Directory。
`Group` 资源的 `Credential` 属性是用于查询 Active Directory 的域帐户。
大多数情况下这是个一般用户帐户，因为默认情况下用户可以*读取* Active Directory 中的大多数对象。

## <a name="example-configuration"></a>示例配置

下面的示例代码使用 DSC 来填充带有域用户的本地组：

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

此代码生成了错误和警告消息：

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

此示例有两个问题：

1. 错误消息说明不推荐使用纯文本密码
2. 警告消息建议不要使用域凭据

标记 PSDSCAllowPlainTextPassword  和 PSDSCAllowDomainUser  禁止显示告知用户所涉及风险的错误和警告。

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

第一条错误消息具有一个带有文档的 URL。
此链接说明如何使用 [ConfigurationData](./configData.md) 结构和证书来加密密码。
有关证书和 DSC 的详细信息，[请阅读此文章](https://aka.ms/certs4dsc)。

要强制使用纯文本密码，资源需要下列配置数据部分中的 `PsDscAllowPlainTextPassword` 关键字：

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

### <a name="localhostmof"></a>localhost.mof

PSDSCAllowPlainTextPassword  标记要求用户确认将纯文本密码存储在 MOF 文件中的风险。 在生成的 MOF 文件中，即使使用了包含 SecureString  的 PSCredential  对象，密码仍以纯文本形式出现。 这是唯一一次公开凭据。 获得对此 MOF 文件的访问权限后，任何人都可以访问管理员帐户。

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

### <a name="credentials-in-transit-and-at-rest"></a>传输中的凭据和静止状态下的凭据

- PSDscAllowPlainTextPassword  标记允许编译包含明文形式密码的 MOF 文件。
  在存储包含明文密码的 MOF 文件时，应采取预防措施。
- 在推送  模式下将 MOF 文件传递给节点时，WinRM 会对通信进行加密，以保护明文密码，除非使用 AllowUnencrypted  参数覆盖默认值。
  - 使用证书加密 MOF 可以在将 MOF 文件应用于节点之前保护处于静止状态的 MOF 文件。
- 在拉取  模式下，可以配置 Windows 拉取服务器，以便通过 Internet 信息服务器中指定的协议使用 HTTPS 加密通信。 有关详细信息，请参阅文章[设置 DSC 拉取客户端](../pull-server/pullclient.md)和[使用证书保护 MOF 文件](../pull-server/secureMOF.md)。
  - 在 [Azure 自动化状态配置](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)服务中，始终加密拉取流量。
- 从 PowerShell 5.0 开始，节点上的 MOF 文件在静态时加密。
  - 在 PowerShell 4.0 中，MOF 文件在静态时不加密，除非它们在被推送或拉取到节点时使用证书加密。

**因为存在重大安全风险，Microsoft 建议避免使用纯文本密码。**

## <a name="domain-credentials"></a>域凭据

再次运行示例配置脚本（加密或不加密），仍然生成警告消息说不推荐将域帐户用于凭据。
使用本地帐户可消除泄露可用于其他服务器的域凭据的可能性。

**对 DSC 资源使用凭据时，应尽可能选择本地帐户而非域帐户。**

如果凭据的 `Username` 属性中有“\\”或“\@”，DSC 会将它视为域帐户。
用户名中域部分的“localhost”、“127.0.0.1”和“::1”除外。

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

在上述 DSC `Group` 资源示例中，查询 Active Directory 域*必须使用*域帐户。
在这种情况下，将 `PSDscAllowDomainUser` 属性添加到 `ConfigurationData` 块中，操作如下：

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

现在配置脚本生成的 MOF 文件将不再出现错误或警告消息。
