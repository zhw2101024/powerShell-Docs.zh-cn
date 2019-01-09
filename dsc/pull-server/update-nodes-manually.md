---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 从拉取服务器更新节点
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400358"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="c0c63-103">从拉取服务器更新节点</span><span class="sxs-lookup"><span data-stu-id="c0c63-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="c0c63-104">以下各节假定您已设置请求服务器。</span><span class="sxs-lookup"><span data-stu-id="c0c63-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="c0c63-105">如果不设置拉取服务器，则可以使用以下指南：</span><span class="sxs-lookup"><span data-stu-id="c0c63-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="c0c63-106">设置 DSC SMB 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="c0c63-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="c0c63-107">设置 DSC HTTP 拉取服务器</span><span class="sxs-lookup"><span data-stu-id="c0c63-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="c0c63-108">每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。</span><span class="sxs-lookup"><span data-stu-id="c0c63-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="c0c63-109">本文将演示如何上传的资源，以便它们可供下载，并配置客户端会自动下载资源。</span><span class="sxs-lookup"><span data-stu-id="c0c63-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="c0c63-110">当该节点的收到的已分配的配置，通过**拉取**或**推送**(v5)，则会自动下载所需的 LCM 中指定的位置中的配置的任何资源。</span><span class="sxs-lookup"><span data-stu-id="c0c63-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="c0c63-111">使用 Update-dscconfiguration cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0c63-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="c0c63-112">从 PowerShell 5.0 中，开始[Update-dscconfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet，强制更新其状态从拉服务器配置 LCM 中的节点。</span><span class="sxs-lookup"><span data-stu-id="c0c63-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="c0c63-113">使用调用 CIMMethod</span><span class="sxs-lookup"><span data-stu-id="c0c63-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="c0c63-114">在 PowerShell 4.0 中，可以仍手动强制请求客户端，以更新其配置中使用[Invoke-cimmethod](/powershell/module/cimcmdlets/invoke-cimmethod)。</span><span class="sxs-lookup"><span data-stu-id="c0c63-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="c0c63-115">下面的示例使用指定的凭据创建 CIM 会话、 调用相应的 CIM 方法和删除该会话。</span><span class="sxs-lookup"><span data-stu-id="c0c63-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="c0c63-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0c63-116">See Also</span></span>

[<span data-ttu-id="c0c63-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="c0c63-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
