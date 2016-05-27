---
title:   配置数据中的凭据选项
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 配置数据中的凭据选项
>适用于：Windows PowerShell 5.0

## 纯文本密码和域用户

包含凭据但未加密的 DSC 配置会生成一条关于纯文本密码的错误信息。
此外，使用域凭据时 DSC 会生成一个警告。
要禁止显示这些错误和警告信息，可以使用 DSC 配置数据关键字：
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

## 在 DSC 中处理凭据

默认情况下，DSC 配置资源以 `Local System` 运行。
但某些资源需要凭据，例如 `Package` 资源需要使用特定用户帐户安装软件。

早期的资源使用硬编码 `Credential` 属性名称来处理此问题。
WMF 5.0 为所有资源都添加了自动 `PsDscRunAsCredential` 属性。 若要了解如何使用 `PsDscRunAsCredential`，请参阅[使用用户凭据运行 DSC](runAsUser.md)。
较新的资源和自定义资源可以使用此自动属性，而不必为凭据创建其自身属性。

*请注意，由于某种原因，某些资源的设计是使用多个凭据，这些资源有其自己的凭据属性。*

使用 ISE 中的 Intellisense (`CTRL+SPACE`) 或 `Get-DscResource -Name ResourceName -Syntax` 来查找资源的可用凭据属性。

```PowerShell
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

此示例使用来自 `PSDesiredStateConfiguration` 内置 DSC 资源模块中的 [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) 资源。
它可以创建本地组并添加或删除成员。
它同时接受 `Credential` 属性和自动 `PsDscRunAsCredential` 属性。
但是该资源只使用 `Credential` 属性。
阅读更多有关 `PsDscRunAsCredential` 的信息，请参阅 [WMF 发行说明](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_runas)。

## 示例：Group 资源 Credential 属性

DSC 在 `Local System` 下运行，因此它已经有权更改本地用户和组。
如果添加的成员是本地帐户，则无需凭据。
如果 `Group` 资源要添加一个域帐户到本地组，则需要凭据。

不允许匿名查询 Active Directory。
`Group` 资源的 `Credential` 属性是用于查询 Active Directory 的域帐户。
大多数情况下这是个一般用户帐户，因为默认情况下用户可以*读取* Active Directory 中的大多数对象。

## 示例配置

下面的示例代码使用 DSC 来填充带有域用户的本地组：

```PowerShell
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

此示例有两个问题：
1.  错误消息说明不推荐使用纯文本密码
2.  警告消息建议不要使用域凭据

## PsDscAllowPlainTextPassword

第一条错误消息具有一个带有文档的 URL。
此链接说明如何使用 [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) 结构和证书来加密密码。
有关证书和 DSC 的详细信息，[请阅读此文章](http://aka.ms/certs4dsc)。

要强制使用纯文本密码，资源需要下列配置数据部分中的 `PsDscAllowPlainTextPassword` 关键字：

```PowerShell
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

*请注意，`NodeName` 不等同于星号，必须指定具体的节点名称。*

**因为具有重大安全风险，Microsoft 建议避免使用纯文本密码。**

## 域凭据

再次运行示例配置脚本（加密或不加密），仍然生成警告消息说不推荐将域帐户用于凭据。
使用本地帐户可消除泄露可用于其他服务器的域凭据的可能性。

**对 DSC 资源使用凭据时，应尽可能选择本地帐户而非域帐户。**

如果凭据的 `Username` 属性中有 \' 或 @，则 DSC 会将该凭据视为域帐户。
用户名中域部分的“localhost”、“127.0.0.1”和“::1”除外。

## PSDscAllowDomainUser

在上述 DSC `Group` 资源示例中，查询 Active Directory 域*必须使用*域帐户。
在这种情况下，将 `PSDscAllowDomainUser` 属性添加到 `ConfigurationData` 块中，操作如下：

```PowerShell
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

现在配置脚本生成的 MOF 文件将不再出现错误或警告消息。



<!--HONumber=May16_HO3-->


