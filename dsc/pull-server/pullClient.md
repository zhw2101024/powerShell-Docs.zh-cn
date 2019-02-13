---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 设置 DSC请求客户端
ms.openlocfilehash: b7cd6dc0087eb8368c5467df4c3c7266ed704451
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677282"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="4d525-103">设置 DSC请求客户端</span><span class="sxs-lookup"><span data-stu-id="4d525-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="4d525-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4d525-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d525-105">请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。</span><span class="sxs-lookup"><span data-stu-id="4d525-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="4d525-106">建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="4d525-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="4d525-107">必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置和资源以及应在其中发送报表数据的 URL 或文件位置。</span><span class="sxs-lookup"><span data-stu-id="4d525-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="4d525-108">以下主题说明了如何设置请求客户端：</span><span class="sxs-lookup"><span data-stu-id="4d525-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="4d525-109">使用配置名称设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="4d525-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="4d525-110">使用配置 ID 设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="4d525-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="4d525-111">**注意**：这些主题适用于 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="4d525-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="4d525-112">有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="4d525-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>