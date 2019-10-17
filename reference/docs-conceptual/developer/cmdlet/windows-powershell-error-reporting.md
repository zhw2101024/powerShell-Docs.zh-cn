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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364266"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="7fcf5-102">Windows PowerShell 错误报告</span><span class="sxs-lookup"><span data-stu-id="7fcf5-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="7fcf5-103">本部分中的主题讨论了 cmdlet 报告错误的方式。</span><span class="sxs-lookup"><span data-stu-id="7fcf5-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7fcf5-104">本部分内容</span><span class="sxs-lookup"><span data-stu-id="7fcf5-104">In This Section</span></span>

<span data-ttu-id="7fcf5-105">[错误报告概念](./error-reporting-concepts.md)介绍 cmdlet 可用于报告错误的两种机制。</span><span class="sxs-lookup"><span data-stu-id="7fcf5-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="7fcf5-106">[终止错误](./terminating-errors.md)描述用于报告终止错误的方法，在此方法中，可以从 cmdlet 内调用此方法，并在调用方法时由 Windows PowerShell 运行时返回异常。</span><span class="sxs-lookup"><span data-stu-id="7fcf5-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="7fcf5-107">[非终止错误](./non-terminating-errors.md)介绍用于报告非终止错误的方法，以及可以从 cmdlet 中调用该方法的位置。</span><span class="sxs-lookup"><span data-stu-id="7fcf5-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="7fcf5-108">[按类别显示错误信息](./displaying-error-information.md)讨论用户显示错误的方式。</span><span class="sxs-lookup"><span data-stu-id="7fcf5-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="7fcf5-109">[Windows PowerShell 错误记录](./windows-powershell-error-records.md)说明错误记录的组成部分。</span><span class="sxs-lookup"><span data-stu-id="7fcf5-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="7fcf5-110">[解释 ErrorRecord 对象](./interpreting-errorrecord-objects.md)讨论如何解释 ErrorRecord 对象。</span><span class="sxs-lookup"><span data-stu-id="7fcf5-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fcf5-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7fcf5-111">See Also</span></span>

[<span data-ttu-id="7fcf5-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7fcf5-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
