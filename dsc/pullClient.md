---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: 设置 DSC请求客户端
ms.openlocfilehash: e6d73187566db2756ae24dabe0a825fffb5ecce0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="f9a09-103">设置 DSC请求客户端</span><span class="sxs-lookup"><span data-stu-id="f9a09-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="f9a09-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f9a09-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f9a09-105">必须告知每个目标节点使用请求模式，并为其提供用于联系请求服务器以获取配置和资源以及应在其中发送报表数据的 URL 或文件位置。</span><span class="sxs-lookup"><span data-stu-id="f9a09-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="f9a09-106">以下主题说明了如何设置请求客户端：</span><span class="sxs-lookup"><span data-stu-id="f9a09-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="f9a09-107">使用配置名称设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="f9a09-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="f9a09-108">使用配置 ID 设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="f9a09-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="f9a09-109">**请注意**：这些主题适用于 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="f9a09-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="f9a09-110">有关在 PowerShell 4.0 中设置请求客户端的信息，请参阅[在 PowerShell 4.0 中使用配置 ID 设置请求客户端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="f9a09-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>