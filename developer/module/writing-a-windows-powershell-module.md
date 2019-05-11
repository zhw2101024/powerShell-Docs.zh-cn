---
title: 编写 Windows PowerShell 模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229342"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="47515-102">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="47515-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="47515-103">本文档面向管理员、 脚本开发人员和 cmdlet 的开发人员需要打包并分发其 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="47515-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="47515-104">通过使用 Windows PowerShell 模块，可打包并分发你的 Windows PowerShell 解决方案，而无需使用经过编译的语言。</span><span class="sxs-lookup"><span data-stu-id="47515-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="47515-105">Windows PowerShell 模块可以对分区、 组织和抽象化成独立的、 可重用单元的 Windows PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="47515-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="47515-106">使用这些可重用单元，可以轻松共享您直接与其他人的模块。</span><span class="sxs-lookup"><span data-stu-id="47515-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="47515-107">如果您是脚本开发人员，您还可以重新打包第三方模块来创建自定义基于脚本的应用程序。</span><span class="sxs-lookup"><span data-stu-id="47515-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="47515-108">模块，类似于如 Perl 和 Python，其他脚本语言中的模块，生产的脚本解决方案与优点，使你能够重新打包和抽象到多个组件一起使用可重用、 可再发行组件创建自定义解决方案。</span><span class="sxs-lookup"><span data-stu-id="47515-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="47515-109">在其最基本的 Windows PowerShell 会将保存为模块的.psm1 文件中任何有效的 Windows PowerShell 脚本代码。</span><span class="sxs-lookup"><span data-stu-id="47515-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="47515-110">PowerShell 还会自动将视为二进制 cmdlet 的任何程序集模块。</span><span class="sxs-lookup"><span data-stu-id="47515-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="47515-111">但是，您还可以使用模块 （或更具体地说，模块清单） 捆绑在一起的整个解决方案。</span><span class="sxs-lookup"><span data-stu-id="47515-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="47515-112">以下方案说明 Windows PowerShell 模块的典型用途。</span><span class="sxs-lookup"><span data-stu-id="47515-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="47515-113">库</span><span class="sxs-lookup"><span data-stu-id="47515-113">Libraries</span></span>

<span data-ttu-id="47515-114">模块可用于打包并分发内聚库执行常见任务的函数。</span><span class="sxs-lookup"><span data-stu-id="47515-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="47515-115">通常情况下，这些函数的名称共享反映它们的用途的常见任务的一个或多个名词。</span><span class="sxs-lookup"><span data-stu-id="47515-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="47515-116">这些函数也可以是类似于.NET Framework 类，都可以具有公共和私有成员。</span><span class="sxs-lookup"><span data-stu-id="47515-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="47515-117">例如，一个库可以包含一组函数的文件传输。</span><span class="sxs-lookup"><span data-stu-id="47515-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="47515-118">在这种情况下，（） 名词，专用于反映将常见的任务可能是"文件。</span><span class="sxs-lookup"><span data-stu-id="47515-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="47515-119">配置</span><span class="sxs-lookup"><span data-stu-id="47515-119">Configuration</span></span>

<span data-ttu-id="47515-120">模块可用于通过添加特定的 cmdlet、 提供程序、 函数和变量来自定义您的环境。</span><span class="sxs-lookup"><span data-stu-id="47515-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="47515-121">已编译的代码开发和分发</span><span class="sxs-lookup"><span data-stu-id="47515-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="47515-122">Cmdlet 和提供程序开发人员可以使用模块来测试和分发其编译的代码而无需创建管理单元。他们可以将包含已编译的代码作为模块 （二进制模块） 的程序集，而无需创建并注册管理单元。</span><span class="sxs-lookup"><span data-stu-id="47515-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="47515-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47515-123">See Also</span></span>

[<span data-ttu-id="47515-124">了解 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="47515-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="47515-125">如何编写 PowerShell 脚本模块</span><span class="sxs-lookup"><span data-stu-id="47515-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="47515-126">如何编写 PowerShell 二进制模块</span><span class="sxs-lookup"><span data-stu-id="47515-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="47515-127">如何编写 PowerShell 模块清单</span><span class="sxs-lookup"><span data-stu-id="47515-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="47515-128">修改 PSModulePath 安装路径</span><span class="sxs-lookup"><span data-stu-id="47515-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="47515-129">正在导入 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="47515-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="47515-130">安装 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="47515-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
