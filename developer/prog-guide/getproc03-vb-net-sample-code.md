---
title: GetProc03 (VB.NET) 的示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301567"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="9f02f-102">GetProc03 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="9f02f-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="9f02f-103">下面的代码演示如何实现`Get-Process`cmdlet，它可以接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="9f02f-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="9f02f-104">此实现中定义`Name`接受管道输入的参数从基于提供的名称，在本地计算机检索进程信息，然后使用[WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)作为将对象发送到管道的输出机制的方法。</span><span class="sxs-lookup"><span data-stu-id="9f02f-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9f02f-105">代码示例</span><span class="sxs-lookup"><span data-stu-id="9f02f-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
