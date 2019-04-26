---
title: Windows PowerShell 错误报告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067065"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="1bdf6-102">Windows PowerShell 错误报告</span><span class="sxs-lookup"><span data-stu-id="1bdf6-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="1bdf6-103">在本部分中的主题讨论 cmdlet 报告错误的方式。</span><span class="sxs-lookup"><span data-stu-id="1bdf6-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1bdf6-104">本部分内容</span><span class="sxs-lookup"><span data-stu-id="1bdf6-104">In This Section</span></span>

<span data-ttu-id="1bdf6-105">[错误报告概念](./error-reporting-concepts.md)介绍 cmdlet 可用于报告错误的两个机制。</span><span class="sxs-lookup"><span data-stu-id="1bdf6-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="1bdf6-106">[终止错误](./terminating-errors.md)介绍用来报告的错误，其中该方法可以从内部调用该 cmdlet，并调用方法时，Windows PowerShell 运行时可以返回的异常终止的方法。</span><span class="sxs-lookup"><span data-stu-id="1bdf6-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="1bdf6-107">[非终止性错误](./non-terminating-errors.md)介绍用来报告非终止错误和其中的该方法可以在 cmdlet 内从调用的方法。</span><span class="sxs-lookup"><span data-stu-id="1bdf6-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="1bdf6-108">[按类别显示错误信息](./displaying-error-information.md)讨论用户可以显示错误的方法。</span><span class="sxs-lookup"><span data-stu-id="1bdf6-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="1bdf6-109">[Windows PowerShell 错误记录](./windows-powershell-error-records.md)错误记录组件进行了说明。</span><span class="sxs-lookup"><span data-stu-id="1bdf6-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="1bdf6-110">[解释 ErrorRecord 对象](./interpreting-errorrecord-objects.md)讨论了如何解释 ErrorRecord 对象。</span><span class="sxs-lookup"><span data-stu-id="1bdf6-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bdf6-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bdf6-111">See Also</span></span>

[<span data-ttu-id="1bdf6-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1bdf6-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
