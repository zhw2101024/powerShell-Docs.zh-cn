---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "创建域控制器"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 12fc529cfb21db260c9d1a2af87e2c3825d2ec4e

---

### 创建域控制器

本文档假定你的计算机已加入域。
如果你当前尚未加入域，这一部分可以帮助你使用 DSC 快速建立起域控制器。

#### 必备条件

1.  计算机位于内部网络上
2.  计算机未加入到现有域
3.  计算机正在运行 Windows Server 2016 或安装了 WMF 5.0

#### 安装 xActiveDirectory
如果你的计算机具有有效的 Internet 连接，请在提升的 PowerShell 窗口中输入以下命令：
```PowerShell
Install-Module xActiveDirectory -Force
```
如果没有 Internet 连接，请将 xActiveDirectory 安装到另一台计算机，然后将 xActiveDirectory 文件夹复制到你的计算机上的“C:\Program Files\WindowsPowerShell\Modules”文件夹。

若要确认安装成功，请运行以下命令：
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### 使用 DSC 设置域
将以下脚本复制到 PowerShell 中，使你的计算机成为新域中的域控制器。
**作者注释：不使用提供的凭据将导致已知问题。  为了安全起见，请勿忘记你的本地管理员密码。**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }

}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
你的计算机将重启数次。
看到包含“Domain has been created.”的名为“C:\temp.txt”的文件，表示过程已完成。

#### 设置用户和组
以下命令将在你的域中设置“操作员和技术支持人员”组以及身为该组成员的相应非管理员用户。
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```




<!--HONumber=Jun16_HO4-->


