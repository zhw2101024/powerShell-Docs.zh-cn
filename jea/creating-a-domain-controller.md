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
ms.openlocfilehash: 80b957ed666ca626c6083041cf99c263e2e0dc27
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
### <a name="creating-a-domain-controller"></a><span data-ttu-id="72dce-103">创建域控制器</span><span class="sxs-lookup"><span data-stu-id="72dce-103">Creating a Domain Controller</span></span>

<span data-ttu-id="72dce-104">本文档假定你的计算机已加入域。</span><span class="sxs-lookup"><span data-stu-id="72dce-104">This document assumes that your machine is domain joined.</span></span>
<span data-ttu-id="72dce-105">如果你当前尚未加入域，这一部分可以帮助你使用 DSC 快速建立起域控制器。</span><span class="sxs-lookup"><span data-stu-id="72dce-105">If you currently don't have a domain to join, this section can help you quickly stand up a domain controller using DSC.</span></span>

#### <a name="prerequisites"></a><span data-ttu-id="72dce-106">必备条件</span><span class="sxs-lookup"><span data-stu-id="72dce-106">Prerequisites</span></span>

1.  <span data-ttu-id="72dce-107">计算机位于内部网络上</span><span class="sxs-lookup"><span data-stu-id="72dce-107">The machine is on an internal network</span></span>
2.  <span data-ttu-id="72dce-108">计算机未加入到现有域</span><span class="sxs-lookup"><span data-stu-id="72dce-108">The machine is not joined to an existing domain</span></span>
3.  <span data-ttu-id="72dce-109">计算机正在运行 Windows Server 2016 或安装了 WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="72dce-109">The machine is running Windows Server 2016 or has WMF 5.0 installed</span></span>

#### <a name="install-xactivedirectory"></a><span data-ttu-id="72dce-110">安装 xActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="72dce-110">Install xActiveDirectory</span></span>
<span data-ttu-id="72dce-111">如果你的计算机具有有效的 Internet 连接，请在提升的 PowerShell 窗口中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="72dce-111">If your machine has an active internet connection, run the following command in an elevated PowerShell window:</span></span>
```PowerShell
Install-Module xActiveDirectory -Force
```
<span data-ttu-id="72dce-112">如果没有 Internet 连接，请将 xActiveDirectory 安装到另一台计算机，然后将 xActiveDirectory 文件夹复制到你的计算机上的“C:\Program Files\WindowsPowerShell\Modules”文件夹。</span><span class="sxs-lookup"><span data-stu-id="72dce-112">If you do not have an internet connection, install xActiveDirectory to another machine and then copy the xActiveDirectory folder to the "C:\Program Files\WindowsPowerShell\Modules" folder on your machine.</span></span>

<span data-ttu-id="72dce-113">若要确认安装成功，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="72dce-113">To confirm the installation succeeded, run the following command:</span></span>
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### <a name="set-up-a-domain-with-dsc"></a><span data-ttu-id="72dce-114">使用 DSC 设置域</span><span class="sxs-lookup"><span data-stu-id="72dce-114">Set up a domain with DSC</span></span>
<span data-ttu-id="72dce-115">将以下脚本复制到 PowerShell 中，使你的计算机成为新域中的域控制器。</span><span class="sxs-lookup"><span data-stu-id="72dce-115">Copy the following script in PowerShell to make your machine a Domain Controller in a new domain.</span></span>
<span data-ttu-id="72dce-116">**作者注释：不使用提供的凭据将导致已知问题。为了安全起见，请勿忘记本地管理员密码。**</span><span class="sxs-lookup"><span data-stu-id="72dce-116">**AUTHOR'S NOTE: THERE IS A KNOWN ISSUE WITH THE CREDENTIALS PROVIDED NOT BEING USED.  TO BE SAFE, DON'T FORGET YOUR LOCAL ADMIN PASSWORD.**</span></span>

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
<span data-ttu-id="72dce-117">你的计算机将重启数次。</span><span class="sxs-lookup"><span data-stu-id="72dce-117">Your machine will restart a few times.</span></span>
<span data-ttu-id="72dce-118">看到包含“Domain has been created.”的名为“C:\temp.txt”的文件，表示过程已完成。</span><span class="sxs-lookup"><span data-stu-id="72dce-118">You will know the process is complete once you see a file called "C:\temp.txt" containing "Domain has been created."</span></span>

#### <a name="set-up-users-and-groups"></a><span data-ttu-id="72dce-119">设置用户和组</span><span class="sxs-lookup"><span data-stu-id="72dce-119">Set up Users and Groups</span></span>
<span data-ttu-id="72dce-120">以下命令将在你的域中设置“操作员和技术支持人员”组以及身为该组成员的相应非管理员用户。</span><span class="sxs-lookup"><span data-stu-id="72dce-120">The following commands will set up an Operator and Helpdesk group in your domain and a corresponding non-administrator user who is a member of that group.</span></span>
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

