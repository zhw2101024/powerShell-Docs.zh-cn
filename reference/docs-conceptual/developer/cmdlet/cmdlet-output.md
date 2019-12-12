---
title: Cmdlet 输出 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1362f4cd-4e05-4ace-ade6-7128da8ad86c
caps.latest.revision: 10
ms.openlocfilehash: 4c6aacd49b0a87bca6806ba5f08a1b4d48a90959
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365936"
---
# <a name="cmdlet-output"></a><span data-ttu-id="252d9-102">Cmdlet 输出</span><span class="sxs-lookup"><span data-stu-id="252d9-102">Cmdlet Output</span></span>

<span data-ttu-id="252d9-103">本部分讨论 cmdlet 输出的类型，以及 cmdlet 可调用以生成输出（如错误消息和对象）的方法。</span><span class="sxs-lookup"><span data-stu-id="252d9-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="252d9-104">本节还介绍如何定义 cmdlet 返回的 .NET Framework 类型以及这些对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="252d9-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="252d9-105">本部分内容</span><span class="sxs-lookup"><span data-stu-id="252d9-105">In This Section</span></span>

<span data-ttu-id="252d9-106">[Cmdlet 输出的类型](./types-of-cmdlet-output.md)介绍 cmdlet 可以生成的类型和输出，以及 cmdlet 调用以生成输出的方法。</span><span class="sxs-lookup"><span data-stu-id="252d9-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="252d9-107">[Cmdlet 错误报告](./cmdlet-error-reporting.md)讨论 cmdlet 错误报告，这是 cmdlet 输出的子集。</span><span class="sxs-lookup"><span data-stu-id="252d9-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="252d9-108">[扩展输出对象](./extending-output-objects.md)讨论如何使用类型文件（. types.ps1xml）来扩展由 cmdlet、函数和脚本返回的 .NET Framework 对象。</span><span class="sxs-lookup"><span data-stu-id="252d9-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="252d9-109">[PowerShell 格式化文件](../format/powershell-formatting-files.md)描述用于定义 Windows PowerShell 中特定 .NET Framework 对象集的默认显示的格式化文件（. types.ps1xml）文件。</span><span class="sxs-lookup"><span data-stu-id="252d9-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="252d9-110">[自定义格式设置文件](./custom-formatting-files.md)描述如何创建您自己的自定义格式设置文件以覆盖默认显示格式或定义您自己的命令返回的对象的显示。</span><span class="sxs-lookup"><span data-stu-id="252d9-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="252d9-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="252d9-111">See Also</span></span>

[<span data-ttu-id="252d9-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="252d9-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
