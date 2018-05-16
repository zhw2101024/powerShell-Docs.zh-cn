---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery
title: 删除项
ms.openlocfilehash: 5af66c5b7edf8f0d7049a98ed4dd10b13d4e9471
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="deleting-items"></a><span data-ttu-id="b568b-103">删除项</span><span class="sxs-lookup"><span data-stu-id="b568b-103">Deleting items</span></span>

<span data-ttu-id="b568b-104">PowerShell 库不支持永久删除项，因为这会对依赖其仍可用的人造成中断。</span><span class="sxs-lookup"><span data-stu-id="b568b-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="b568b-105">但是，PowerShell 库支持“取消列出”项的方式，可以在网站项管理页面完成完成此操作。</span><span class="sxs-lookup"><span data-stu-id="b568b-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="b568b-106">如果取消列出某个项，它将不会在搜索和任何项列表中出现（无论是在 PowerShell 库上，还是使用 PowerShellGet 命令）。</span><span class="sxs-lookup"><span data-stu-id="b568b-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="b568b-107">但是，仍可通过指定精确版本下载它（精确版本可允许自动脚本继续运行）。</span><span class="sxs-lookup"><span data-stu-id="b568b-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="b568b-108">如果你遇到你认为必须删除一个项的特殊情况，PowerShell 库团队可手动解决此问题。</span><span class="sxs-lookup"><span data-stu-id="b568b-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="b568b-109">例如，如果存在侵犯版权问题或潜在有害内容，这是删除项的正当理由。</span><span class="sxs-lookup"><span data-stu-id="b568b-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="b568b-110">在这种情况下，应通过 [PowerShell 库](http://www.PowerShellGallery.com)提交支持请求。</span><span class="sxs-lookup"><span data-stu-id="b568b-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>