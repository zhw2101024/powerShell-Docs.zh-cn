---
title: 如何使用模块的 Cmdlet 导入 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859143"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="605ab-102">如何使用模块导入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="605ab-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="605ab-103">本主题介绍如何通过使用二进制模块导入的 Windows PowerShell 会话的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="605ab-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="605ab-104">模块的成员可以包括 cmdlet、 提供程序、 函数、 变量、 别名和其他更多。</span><span class="sxs-lookup"><span data-stu-id="605ab-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="605ab-105">管理单元只能包含 cmdlet 和提供程序。</span><span class="sxs-lookup"><span data-stu-id="605ab-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="605ab-106">如何加载使用模块的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="605ab-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="605ab-107">创建具有相同的名称与程序集文件中实现这些 cmdlet 的模块文件夹。</span><span class="sxs-lookup"><span data-stu-id="605ab-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="605ab-108">在此过程中，模块文件夹中创建`system32`文件夹。</span><span class="sxs-lookup"><span data-stu-id="605ab-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="605ab-109">请确保`PSModulePath`环境变量包含新的模块文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="605ab-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="605ab-110">默认情况下，系统文件夹已添加到`PSModulePath`环境变量。</span><span class="sxs-lookup"><span data-stu-id="605ab-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="605ab-111">将 cmdlet 程序集复制到模块文件夹中。</span><span class="sxs-lookup"><span data-stu-id="605ab-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="605ab-112">运行以下命令以将 cmdlet 添加到会话：</span><span class="sxs-lookup"><span data-stu-id="605ab-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="605ab-113">此过程可以用于测试 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="605ab-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="605ab-114">它将所有的 cmdlet 添加到该会话在程序集中。</span><span class="sxs-lookup"><span data-stu-id="605ab-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="605ab-115">不同类型的模块，若要加载的模块，以及如何限制将导出的模块元素的不同方式有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="605ab-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="605ab-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="605ab-116">See Also</span></span>

[<span data-ttu-id="605ab-117">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="605ab-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="605ab-118">安装模块</span><span class="sxs-lookup"><span data-stu-id="605ab-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)