---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "使用用户凭据运行 DSC"
ms.openlocfilehash: 11c13d852b506be3e202b798d135eba73d84cfe0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="f9c7f-103">使用用户凭据运行 DSC</span><span class="sxs-lookup"><span data-stu-id="f9c7f-103">Running DSC with user credentials</span></span> 

> <span data-ttu-id="f9c7f-104">适用于：Windows PowerShell 5.0 和 Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f9c7f-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="f9c7f-105">可以通过在配置中使用 **PsDscRunAsCredential** 属性，在指定的一组凭据之下运行 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="f9c7f-106">默认情况下，DSC 以系统帐户身份运行每个资源。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="f9c7f-107">有时需要以用户身份运行，例如在特定用户上下文中安装 MSI 程序包、设置用户的注册表项、访问用户的特定本地目录或访问网络共享。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="f9c7f-108">每个 DSC 资源都具有 **PsDscRunAsCredential** 属性，它可以设置为任何用户凭据（[PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) 对象）。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="f9c7f-109">凭据可以硬编码为配置中属性的值，你也可以将值设置为 [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx)，这会在编译配置时提示用户输入凭据（有关编译配置的信息，请参阅[配置](configurations.md)）。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="f9c7f-110">**注意：**在 PowerShell 5.0 中，不支持在调用复合资源的配置中使用 **PsDscRunAsCredential** 属性。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> 
><span data-ttu-id="f9c7f-111">在 PowerShell 5.1 中，支持在调用复合资源的配置中使用 **PsDscRunAsCredential** 属性。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="f9c7f-112">**注意：****PsDscRunAsCredential** 属性在 PowerShell 4.0 中不可用。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="f9c7f-113">在下面的示例中，**Get-Credential** 用于提示用户输入凭据。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span> <span data-ttu-id="f9c7f-114">[Registry](registryResource.md) 资源用于更改可指定 Windows 命令提示符窗口背景色的注册表项。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
><span data-ttu-id="f9c7f-115">**注意：**此示例假定你在 `C:\publicKeys\targetNode.cer` 上具有有效证书，并且该证书的指纹是显示的值。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="f9c7f-116">若要了解如何在 DSC 配置 MOF 文件中加密凭据，请参阅[保护 MOF 文件](secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="f9c7f-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>

