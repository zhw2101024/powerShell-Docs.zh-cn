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
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854633"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="dbf9d-102">GetProc03 (VB.NET) 示例代码</span><span class="sxs-lookup"><span data-stu-id="dbf9d-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="dbf9d-103">下面的代码演示如何实现`Get-Process`cmdlet，它可以接受管道输入。</span><span class="sxs-lookup"><span data-stu-id="dbf9d-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="dbf9d-104">此实现中定义`Name`接受管道输入的参数从基于提供的名称，在本地计算机检索进程信息，然后使用[System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)作为将对象发送到管道的输出机制的方法。</span><span class="sxs-lookup"><span data-stu-id="dbf9d-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="dbf9d-105">代码示例</span><span class="sxs-lookup"><span data-stu-id="dbf9d-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->