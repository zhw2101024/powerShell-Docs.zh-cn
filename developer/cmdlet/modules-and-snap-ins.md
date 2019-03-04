---
title: 模块和管理单元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860493"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="9b5b0-102">模块和管理单元</span><span class="sxs-lookup"><span data-stu-id="9b5b0-102">Modules and Snap-ins</span></span>

<span data-ttu-id="9b5b0-103">Cmdlet 可以添加到使用 （通过 Windows PowerShell 2.0 中引入） 的模块或管理单元的会话。一旦该 cmdlet 添加到会话中它可以在主机应用程序或以交互方式在命令行以编程方式运行。</span><span class="sxs-lookup"><span data-stu-id="9b5b0-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="9b5b0-104">我们建议你使用模块作为传递方法将 cmdlet 添加到的会话由于以下原因：</span><span class="sxs-lookup"><span data-stu-id="9b5b0-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="9b5b0-105">模块，可将 cmdlet 添加的程序集加载其中定义该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b5b0-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="9b5b0-106">没有无需实现一个管理单元中的类。</span><span class="sxs-lookup"><span data-stu-id="9b5b0-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="9b5b0-107">模块可以添加其他资源，如变量、 函数、 脚本、 类型和格式设置文件，和的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9b5b0-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="9b5b0-108">可以使用管理单元只可添加到会话的 cmdlet 和提供程序。</span><span class="sxs-lookup"><span data-stu-id="9b5b0-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b5b0-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b5b0-109">See Also</span></span>

[<span data-ttu-id="9b5b0-110">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="9b5b0-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="9b5b0-111">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9b5b0-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
