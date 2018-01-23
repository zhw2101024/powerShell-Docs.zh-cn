---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "设置 DSC请求客户端"
ms.openlocfilehash: 98a67b8d27eeb445bb70f75253ca31e12207d5bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="1fc77-103">设置 DSC请求客户端</span><span class="sxs-lookup"><span data-stu-id="1fc77-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="1fc77-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1fc77-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1fc77-105">必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置和资源以及应在其中发送报表数据的 URL 或文件位置。</span><span class="sxs-lookup"><span data-stu-id="1fc77-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="1fc77-106">以下主题说明了如何设置请求客户端：</span><span class="sxs-lookup"><span data-stu-id="1fc77-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="1fc77-107">使用配置名称设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="1fc77-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="1fc77-108">使用配置 ID 设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="1fc77-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="1fc77-109">**请注意**：这些主题适用于 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="1fc77-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="1fc77-110">有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="1fc77-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

