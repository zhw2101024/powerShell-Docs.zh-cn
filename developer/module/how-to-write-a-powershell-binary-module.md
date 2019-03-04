---
title: 如何编写 PowerShell 二进制模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856483"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="79b3d-102">如何编写 PowerShell 二进制模块</span><span class="sxs-lookup"><span data-stu-id="79b3d-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="79b3d-103">二进制模块可以包含 cmdlet 类任何程序集 (.dll)。</span><span class="sxs-lookup"><span data-stu-id="79b3d-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="79b3d-104">默认情况下，导入二进制模块导入的程序集中的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79b3d-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="79b3d-105">但是，可以限制会通过创建一个其根模块是程序集的模块清单导入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79b3d-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="79b3d-106">（例如，在清单的 CmdletsToExport 密钥可以用于导出所需的 cmdlet。）此外，二进制模块可以包含其他文件、 目录结构和其他许多有用的管理信息单个 cmdlet 不能。</span><span class="sxs-lookup"><span data-stu-id="79b3d-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="79b3d-107">以下过程介绍如何创建和安装 PowerShell 二进制模块。</span><span class="sxs-lookup"><span data-stu-id="79b3d-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="79b3d-108">如何创建和安装 PowerShell 二进制模块</span><span class="sxs-lookup"><span data-stu-id="79b3d-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="79b3d-109">创建一个二进制 PowerShell 解决方案 (如编写的 cmdlet C#)，使用的功能所需，并且确保其正常运行。</span><span class="sxs-lookup"><span data-stu-id="79b3d-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="79b3d-110">从代码角度看，二进制模块的核心是只需一个 cmdlet 的程序集。</span><span class="sxs-lookup"><span data-stu-id="79b3d-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="79b3d-111">事实上，PowerShell 会将单个 cmdlet 程序集视为一个模块中，根据加载和卸载，开发人员来说没有额外操作。</span><span class="sxs-lookup"><span data-stu-id="79b3d-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="79b3d-112">有关编写 cmdlet 的详细信息，请参阅[编写 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="79b3d-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="79b3d-113">如有必要，创建解决方案的其余部分: （更多的 cmdlet、 XML 文件等） 并使用模块清单中描述它们。</span><span class="sxs-lookup"><span data-stu-id="79b3d-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="79b3d-114">除了介绍你的解决方案中的 cmdlet 程序集，模块清单可以描述要如何导出和导入模块、 将公开哪些 cmdlet，和内容的其他文件将进入该模块。</span><span class="sxs-lookup"><span data-stu-id="79b3d-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span> <span data-ttu-id="79b3d-115">如前面所述但是，PowerShell，可以将任何额外操作模块之类的二进制 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79b3d-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span> <span data-ttu-id="79b3d-116">在这种情况下，模块清单是主要用于将多个文件组合成单个包中，或显式控制给定程序集发布有用的。</span><span class="sxs-lookup"><span data-stu-id="79b3d-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span> <span data-ttu-id="79b3d-117">有关详细信息，请参阅[如何编写 PowerShell 模块清单](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)。</span><span class="sxs-lookup"><span data-stu-id="79b3d-117">For more information, see [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

   <span data-ttu-id="79b3d-118">下面的代码是非常简单C#包含三个 cmdlet 可以用作模块在同一文件中的代码块。</span><span class="sxs-lookup"><span data-stu-id="79b3d-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="79b3d-119">打包你的解决方案，并将包保存到某个位置中的 PowerShell 模块路径。</span><span class="sxs-lookup"><span data-stu-id="79b3d-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="79b3d-120">`PSModulePath`全局环境变量描述将使用 PowerShell 来查找你的模块的默认路径。</span><span class="sxs-lookup"><span data-stu-id="79b3d-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="79b3d-121">例如，若要将模块保存在系统上的公共路径将`%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`。</span><span class="sxs-lookup"><span data-stu-id="79b3d-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="79b3d-122">如果不使用默认路径，您需要在安装过程中显式声明模块的位置。</span><span class="sxs-lookup"><span data-stu-id="79b3d-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="79b3d-123">请务必创建一个文件夹以保存您的模块中，您可能需要存储多个程序集和解决方案文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="79b3d-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="79b3d-124">请注意，从技术上讲不需要在任意位置安装你的模块`PSModulePath`-这些都是只需将查找 PowerShell 模块的默认位置。</span><span class="sxs-lookup"><span data-stu-id="79b3d-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="79b3d-125">但是，它被视为最佳做法，若要执行此操作，除非您有一个充分的理由来存储您的模块中其他位置。</span><span class="sxs-lookup"><span data-stu-id="79b3d-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="79b3d-126">有关详细信息，请参阅[安装 PowerShell 模块](./installing-a-powershell-module.md)并[修改 PowerShell 模块安装路径](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="79b3d-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="79b3d-127">将模块导入 PowerShell，通过调用[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)。</span><span class="sxs-lookup"><span data-stu-id="79b3d-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="79b3d-128">调用到[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)将你的模块加载到活动内存中。</span><span class="sxs-lookup"><span data-stu-id="79b3d-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="79b3d-129">如果使用 PowerShell 3.0 和更高版本，只需在代码中调用你的模块名称还将导入它;有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="79b3d-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="79b3d-130">作为模块导入管理单元中的程序集</span><span class="sxs-lookup"><span data-stu-id="79b3d-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="79b3d-131">可以作为二进制模块加载 Cmdlet 和提供程序中管理单元中的程序集存在。</span><span class="sxs-lookup"><span data-stu-id="79b3d-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="79b3d-132">作为二进制模块加载管理单元中的程序集时，cmdlet 和管理单元中的提供程序可供用户，但在程序集中的管理单元类将被忽略，以及未注册管理单元中。</span><span class="sxs-lookup"><span data-stu-id="79b3d-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="79b3d-133">因此，提供 Windows PowerShell 的管理单元中 cmdlet 无法检测到管理单元中即使 cmdlet 和提供程序是可用于该会话。</span><span class="sxs-lookup"><span data-stu-id="79b3d-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="79b3d-134">此外，不能作为二进制模块的一部分导入引用的管理单元中的任何格式设置或类型文件。</span><span class="sxs-lookup"><span data-stu-id="79b3d-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span> <span data-ttu-id="79b3d-135">若要导入的文件格式和类型文件必须创建一个模块清单。</span><span class="sxs-lookup"><span data-stu-id="79b3d-135">To import the formatting and types files you must create a module manifest.</span></span> <span data-ttu-id="79b3d-136">查看，请[如何编写 PowerShell 模块清单](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)。</span><span class="sxs-lookup"><span data-stu-id="79b3d-136">See, [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

## <a name="see-also"></a><span data-ttu-id="79b3d-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79b3d-137">See Also</span></span>

[<span data-ttu-id="79b3d-138">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="79b3d-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
