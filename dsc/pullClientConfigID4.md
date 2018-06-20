---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 在 PowerShell 4.0 中使用配置 ID 设置请求客户端
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187760"
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="79556-103">在 PowerShell 4.0 中使用配置 ID 设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="79556-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="79556-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="79556-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="79556-105">必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置的 URL。</span><span class="sxs-lookup"><span data-stu-id="79556-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="79556-106">若要执行此操作，必须为本地配置管理器 (LCM) 配置所需信息。</span><span class="sxs-lookup"><span data-stu-id="79556-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="79556-107">若要配置 LCM，请创建一个称为“元配置”的特殊配置。</span><span class="sxs-lookup"><span data-stu-id="79556-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="79556-108">有关配置 LCM 的详细信息，请参阅 [Windows PowerShell 4.0 Desired State Configuration 本地配置管理器](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="79556-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="79556-109">下面的脚本将 LCM 配置为从名为“PullServer”的服务器请求配置：</span><span class="sxs-lookup"><span data-stu-id="79556-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="79556-110">在该脚本中，**DownloadManagerCustomData** 传递请求服务器的 URL 并（在本示例中）允许不安全的连接。</span><span class="sxs-lookup"><span data-stu-id="79556-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span>

<span data-ttu-id="79556-111">此脚本运行后，将创建名为 **SimpleMetaConfigurationForPull** 的新输出文件夹，并在其中放入元配置 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="79556-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="79556-112">若要应用配置，请将 **Set-DscLocalConfigurationManager** 用于 **ComputerName**（使用“localhost”）和 **Path**（目标节点的 localhost.meta.mof 文件的位置路径）的参数。</span><span class="sxs-lookup"><span data-stu-id="79556-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="79556-113">例如：</span><span class="sxs-lookup"><span data-stu-id="79556-113">For example:</span></span>
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="79556-114">配置 ID</span><span class="sxs-lookup"><span data-stu-id="79556-114">Configuration ID</span></span>
<span data-ttu-id="79556-115">此脚本将 LCM 的 **ConfigurationID** 属性设置为之前为此目的创建的 GUID（你可以通过使用 **New-Guid** cmdlet 创建 GUID）。</span><span class="sxs-lookup"><span data-stu-id="79556-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="79556-116">LCM 使用 **ConfigurationID** 在请求服务器上查找相应配置。</span><span class="sxs-lookup"><span data-stu-id="79556-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="79556-117">请求服务器上的配置 MOF 文件必须命名为 `ConfigurationID.mof`，其中 *ConfigurationID* 是目标节点上 LCM 的 **ConfigurationID** 属性值。</span><span class="sxs-lookup"><span data-stu-id="79556-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="79556-118">从 SMB 服务器请求</span><span class="sxs-lookup"><span data-stu-id="79556-118">Pulling from an SMB server</span></span>

<span data-ttu-id="79556-119">如果请求服务器被设置为 SMB 文件共享，而不是 Web 服务，请指定 **DscFileDownloadManager**，而不是 **WebDownLoadManager**。</span><span class="sxs-lookup"><span data-stu-id="79556-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="79556-120">**DscFileDownloadManager** 采用 **SourcePath** 属性，而不是 **ServerUrl**。</span><span class="sxs-lookup"><span data-stu-id="79556-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="79556-121">下面的脚本将 LCM 配置为从“CONTOSO-SERVER”服务器上的“SmbDscShare”SMB 共享请求配置：</span><span class="sxs-lookup"><span data-stu-id="79556-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="79556-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79556-122">See Also</span></span>

- [<span data-ttu-id="79556-123">设置 DSC Web 请求服务器</span><span class="sxs-lookup"><span data-stu-id="79556-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="79556-124">设置 DSC SMB 请求服务器</span><span class="sxs-lookup"><span data-stu-id="79556-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)