---
title: GetProc03 （VB.NET）示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360306"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="448e6-102">GetProc03 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="448e6-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="448e6-103">下面的代码演示了可接受管道输入的 `Get-Process` cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="448e6-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="448e6-104">此实现定义了一个 `Name` 参数，该参数接受管道输入，基于提供的名称从本地计算机检索进程信息，然后使用[WriteObject （system.string，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法作为输出用于将对象发送到管道的机制。</span><span class="sxs-lookup"><span data-stu-id="448e6-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="448e6-105">代码示例</span><span class="sxs-lookup"><span data-stu-id="448e6-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
