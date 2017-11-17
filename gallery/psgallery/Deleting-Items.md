---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: "删除项"
ms.openlocfilehash: 00452f9b6625a51e95f3f46dbd66291fa20e17ad
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="deleting-items"></a><span data-ttu-id="dc9dc-103">删除项</span><span class="sxs-lookup"><span data-stu-id="dc9dc-103">Deleting items</span></span>

<span data-ttu-id="dc9dc-104">PowerShell 库不支持永久删除项，因为这会对依赖其仍可用的人造成中断。</span><span class="sxs-lookup"><span data-stu-id="dc9dc-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="dc9dc-105">但是，PowerShell 库支持“取消列出”项的方式，可以在网站项管理页面完成完成此操作。</span><span class="sxs-lookup"><span data-stu-id="dc9dc-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span> <span data-ttu-id="dc9dc-106">如果取消列出某个项，它将不会在搜索和任何项列表中出现（无论是在 PowerShell 库上，还是使用 PowerShellGet 命令）。</span><span class="sxs-lookup"><span data-stu-id="dc9dc-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span> <span data-ttu-id="dc9dc-107">但是，仍可通过指定精确版本下载它（精确版本可允许自动脚本继续运行）。</span><span class="sxs-lookup"><span data-stu-id="dc9dc-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="dc9dc-108">如果你遇到你认为必须删除一个项的特殊情况，PowerShell 库团队可手动解决此问题。</span><span class="sxs-lookup"><span data-stu-id="dc9dc-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span> <span data-ttu-id="dc9dc-109">例如，如果存在侵犯版权问题或潜在有害内容，这是删除项的正当理由。</span><span class="sxs-lookup"><span data-stu-id="dc9dc-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span> <span data-ttu-id="dc9dc-110">在此情况下，你应通过 [PowerShell 库] (http://www.PowerShellGallery.com) 提交支持请求。</span><span class="sxs-lookup"><span data-stu-id="dc9dc-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>

