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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365366"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="9facd-102">模块和管理单元</span><span class="sxs-lookup"><span data-stu-id="9facd-102">Modules and Snap-ins</span></span>

<span data-ttu-id="9facd-103">Cmdlet 可以使用模块（由 Windows PowerShell 2.0 引入）或管理单元添加到会话中。将 cmdlet 添加到会话后，它可以通过主机应用程序以编程方式运行，或在命令行中以编程方式运行。</span><span class="sxs-lookup"><span data-stu-id="9facd-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="9facd-104">出于以下原因，建议使用模块作为向会话添加 cmdlet 的传递方法：</span><span class="sxs-lookup"><span data-stu-id="9facd-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="9facd-105">模块允许通过加载定义 cmdlet 的程序集来添加 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9facd-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="9facd-106">无需实现管理单元类。</span><span class="sxs-lookup"><span data-stu-id="9facd-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="9facd-107">模块允许添加其他资源，例如变量、函数、脚本、类型和格式设置文件等。</span><span class="sxs-lookup"><span data-stu-id="9facd-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="9facd-108">管理单元只能用于向会话添加 cmdlet 和提供程序。</span><span class="sxs-lookup"><span data-stu-id="9facd-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="9facd-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9facd-109">See Also</span></span>

[<span data-ttu-id="9facd-110">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="9facd-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="9facd-111">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9facd-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
