---
title:   使用资源设计器工具
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 使用资源设计器工具

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

资源设计器工具是一组由 **xDscResourceDesigner** 模块公开的 cmdlet，它使 Windows PowerShell Desired State Configuration (DSC) 的创建更加轻松简单。 此资源中的 cmdlet 能帮助你创建新资源的 MOF 架构、脚本模块和目录结构。 有关 DSC 资源的详细信息，请参阅[构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)。
在本主题中，我们将创建一个管理 Active Directory 用户的 DSC 资源。
使用 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet 安装 **xDscResourceDesigner** 模块。

>**请注意**：**Install-Module** 包含在 **PowerShellGet** 模块中，后者纳入 PowerShell 5.0。 可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。

## 创建资源属性
我们首先要确定资源将公开的属性。 在此示例中，我们将通过以下属性来定义 Active Directory 用户。
 
参数名称  说明
* **UserName**：唯一标识用户的键属性。
* **Ensure**：指定用户帐户应该为 Present 还是 Absent。 此参数只有两个可能的值。
* **DomainCredential**：用户的域密码。
* **Password**：允许必要时配置对用户密码进行更改所需的用户密码。

我们使用 **New-xDscResourceProperty** cmdlet 来创建属性。 下面的 PowerShell 命令可以创建上述属性。

```powershell
PS C:\> $UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
PS C:\> $Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
PS C:\> $DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
PS C:\> $Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## 创建资源

创建好资源属性后，我们就可以调用 **New-xDscResource** cmdlet 来创建资源。 **New-xDscResource** cmdlet 采用了属性列表作为参数。 它还采用了应将模块创建于的路径、新资源的名称以及包含它的模块名称。 下面的 PowerShell 命令可以创建资源。

```powershell
PS C:\> New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

**New-xDscResource** cmdlet 创建 MOF 架构、主干资源脚本、新资源所需目录结构以及公开新资源的模块清单。

MOF 架构文件位于 **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**，其内容如下。

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
[Key] string UserName;
[Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
[Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
[Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

资源脚本位于 **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**。 资源脚本不包含实现资源的实际逻辑，你必须自己添加。 主干脚本的内容如下。

```powershell
function Get-TargetResource
{
[CmdletBinding()]
[OutputType([System.Collections.Hashtable])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$returnValue = @{
UserName = [System.String]
Ensure = [System.String]
DomainAdminCredential = [System.Management.Automation.PSCredential]
Password = [System.Management.Automation.PSCredential]
}

$returnValue
#>
}


function Set-TargetResource
{
[CmdletBinding()]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."

#Include this line if the resource requires a system reboot.
#$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[parameter(Mandatory = $true)]
[System.String]
$UserName,

[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[System.Management.Automation.PSCredential]
$DomainAdminCredential,

[System.Management.Automation.PSCredential]
$Password
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


<#
$result = [System.Boolean]

$result
#>
}


Export-ModuleMember -Function *-TargetResource
```

## 更新资源

如果需要添加或修改资源的参数列表，可以调用 **Update-xDscResource** cmdlet。 该 cmdlet 将使用新参数列表更新资源。 如果你已在资源脚本中添加逻辑，它将保持不变。

例如，假如你想为用户将最新日志包含在资源中。 你可以调用 **New-xDscResourceProperty** 创建新属性，然后调用 **Update-xDscResource** 并将新属性添加到属性列表，而不用重新编写资源。

```powershell
PS C:\> $lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
PS C:\> Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## 测试资源架构

资源设计器工具还公开了一个 cmdlet，可用于测试手动编写的 MOF 架构的有效性。 调用 **Test-xDscSchema** cmdlet，将 MOF 资源架构的路径作为参数传递。 该 cmdlet 将输出架构中的任何错误。

### 另请参阅

#### 概念
[构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)

#### 其他资源
[xDscResourceDesigner 模块](https://powershellgallery.com/packages/xDscResourceDesigner)



<!--HONumber=May16_HO3-->


