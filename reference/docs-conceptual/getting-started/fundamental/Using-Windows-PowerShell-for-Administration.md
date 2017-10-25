---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用 Windows PowerShell 进行管理"
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: fa87745b9be04d14de37a308d870b73c5a98cf83
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="using-windows-powershell-for-administration"></a><span data-ttu-id="a4c03-103">使用 Windows PowerShell 进行管理</span><span class="sxs-lookup"><span data-stu-id="a4c03-103">Using Windows PowerShell for Administration</span></span>
<span data-ttu-id="a4c03-104">Windows PowerShell 的根本目标是通过交互方式或从脚本提供针对系统的更好的、更便捷的管理控制。</span><span class="sxs-lookup"><span data-stu-id="a4c03-104">The fundamental goal of Windows PowerShell is providing better, easier administrative control over systems, either interactively or from script.</span></span> <span data-ttu-id="a4c03-105">本章展示了针对使用 Windows PowerShell 管理 Windows 系统过程中许多特殊问题的解决方案。</span><span class="sxs-lookup"><span data-stu-id="a4c03-105">This chapter walks through solutions to many specific problems in administering Windows systems with Windows PowerShell.</span></span> <span data-ttu-id="a4c03-106">虽然我们在 Windows PowerShell 用户指南中未讨论脚本或函数，但以后可以从脚本使用这些解决方案或将其用作函数。</span><span class="sxs-lookup"><span data-stu-id="a4c03-106">Although we have not talked about scripts or functions in the Windows PowerShell User's Guide, the solutions can be used from scripts or as functions later.</span></span> <span data-ttu-id="a4c03-107">我们将展示包括函数在内的示例，作为解决问题的解决方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="a4c03-107">We will show examples that include functions as part of the solution to solve problems.</span></span>

<span data-ttu-id="a4c03-108">在整个解决方案介绍中，你会看到解决方案的组合，它们使用特定的 cmdlet、常规的 Get-WmiObject cmdlet，甚至还有作为 Windows 和 .NET Framework 基础结构一部分的外部工具。</span><span class="sxs-lookup"><span data-stu-id="a4c03-108">Throughout the solution descriptions, you will see a mix of solutions using specific cmdlets, the general Get-WmiObject cmdlet, and even external tools that are part of the Windows and .NET Framework infrastructures.</span></span> <span data-ttu-id="a4c03-109">外部工具的使用是 Windows PowerShell 长久以来设计目的的一部分。</span><span class="sxs-lookup"><span data-stu-id="a4c03-109">Use of external tools is part of the long-term design intent of Windows PowerShell.</span></span> <span data-ttu-id="a4c03-110">虽然此系统在不断改进，用户仍会遇到可用工具集无法实现其全部需求的情况。</span><span class="sxs-lookup"><span data-stu-id="a4c03-110">Even as the system grows, users will continually encounter situations in which the available toolsets do not do everything they need.</span></span> <span data-ttu-id="a4c03-111">Windows PowerShell 尝试将针对各种可能情况的解决方案进行整合，而不仅仅依赖于 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="a4c03-111">Rather than foster dependency on cmdlet implementations alone, Windows PowerShell tries to support integrating solutions from every possible alternative scenario.</span></span>

