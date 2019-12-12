---
title: Runspace02 （C#）代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: abf539bc29bd9ccac59bd5957397fbe68951f266
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366616"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="11162-102">Runspace02 (C#) 代码示例</span><span class="sxs-lookup"><span data-stu-id="11162-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="11162-103">下面是 Runspace02 C#示例的源代码。</span><span class="sxs-lookup"><span data-stu-id="11162-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="11162-104">此示例使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类来同步执行 `Get-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="11162-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="11162-105">然后，使用 Windows 窗体和数据绑定在 DataGridView 控件中显示结果</span><span class="sxs-lookup"><span data-stu-id="11162-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="11162-106">代码示例</span><span class="sxs-lookup"><span data-stu-id="11162-106">Code Sample</span></span>

[!code-csharp[Runspace02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a><span data-ttu-id="11162-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11162-107">See Also</span></span>

[<span data-ttu-id="11162-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="11162-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
