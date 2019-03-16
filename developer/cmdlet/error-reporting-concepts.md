---
title: 错误报告概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054401"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="96815-102">错误报告概念</span><span class="sxs-lookup"><span data-stu-id="96815-102">Error Reporting Concepts</span></span>

<span data-ttu-id="96815-103">Windows PowerShell 提供了两种机制用于报告错误： 一种机制*终止错误*和另一种可*非终止性错误*。</span><span class="sxs-lookup"><span data-stu-id="96815-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="96815-104">务必为你的 cmdlet 报告错误正确，以便运行 cmdlet 的主机应用程序可以以适当的方式作出反应。</span><span class="sxs-lookup"><span data-stu-id="96815-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="96815-105">你的 cmdlet 应调用[System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法在出错时却没有或不应允许该 cmdlet 可以继续处理其输入的对象。</span><span class="sxs-lookup"><span data-stu-id="96815-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="96815-106">你的 cmdlet 应调用[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法来报告非终止性错误，该 cmdlet 可以继续处理输入的对象时。</span><span class="sxs-lookup"><span data-stu-id="96815-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="96815-107">这两种方法提供主机应用程序可用于调查该错误的原因的错误记录。</span><span class="sxs-lookup"><span data-stu-id="96815-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="96815-108">使用以下准则来确定错误是否终止或非终止错误。</span><span class="sxs-lookup"><span data-stu-id="96815-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="96815-109">如果从继续处理当前对象或已成功处理任何进一步输入的对象，而不考虑其内容，它使你的 cmdlet，错误将是一个终止错误。</span><span class="sxs-lookup"><span data-stu-id="96815-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="96815-110">如果您不希望你的 cmdlet 以继续处理当前对象或任何进一步输入的对象，而不考虑其内容，错误将是一个终止错误。</span><span class="sxs-lookup"><span data-stu-id="96815-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="96815-111">错误是一个终止错误时不会接受或返回的对象的 cmdlet 或 cmdlet 接受或返回一个对象中发生。</span><span class="sxs-lookup"><span data-stu-id="96815-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="96815-112">如果你的 cmdlet 要继续处理当前对象和任何进一步输入的对象，错误将是一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="96815-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="96815-113">如果它与特定输入的对象或输入对象的子集，错误将是一个非终止错误。</span><span class="sxs-lookup"><span data-stu-id="96815-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="96815-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96815-114">See Also</span></span>

[<span data-ttu-id="96815-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="96815-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="96815-116">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="96815-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="96815-117">Windows PowerShell 错误记录</span><span class="sxs-lookup"><span data-stu-id="96815-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="96815-118">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="96815-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
