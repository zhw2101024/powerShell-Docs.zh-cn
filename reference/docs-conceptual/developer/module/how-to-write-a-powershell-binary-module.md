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
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367116"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="7d52c-102">如何编写 PowerShell 二进制模块</span><span class="sxs-lookup"><span data-stu-id="7d52c-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="7d52c-103">二进制模块可以是包含 cmdlet 类的任何程序集（.dll）。</span><span class="sxs-lookup"><span data-stu-id="7d52c-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="7d52c-104">默认情况下，导入二进制模块时，会导入程序集中的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7d52c-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="7d52c-105">但是，可以通过创建模块清单（其根模块是程序集）来限制导入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7d52c-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="7d52c-106">（例如，清单的 CmdletsToExport 键只能用于导出所需的 cmdlet。）此外，二进制模块可以包含其他文件、目录结构以及单个 cmdlet 不能使用的其他有用的管理信息。</span><span class="sxs-lookup"><span data-stu-id="7d52c-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="7d52c-107">下面的过程介绍如何创建和安装 PowerShell 二进制模块。</span><span class="sxs-lookup"><span data-stu-id="7d52c-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="7d52c-108">如何创建和安装 PowerShell 二进制模块</span><span class="sxs-lookup"><span data-stu-id="7d52c-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="7d52c-109">使用所需的功能创建二进制 PowerShell 解决方案（例如， C#使用编写的 cmdlet），并确保其正常运行。</span><span class="sxs-lookup"><span data-stu-id="7d52c-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="7d52c-110">从代码的角度来看，二进制模块的核心只是一个 cmdlet 程序集。</span><span class="sxs-lookup"><span data-stu-id="7d52c-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="7d52c-111">事实上，在加载和卸载的过程中，PowerShell 会将单个 cmdlet 程序集视为模块，而不会对开发人员的其他工作进行额外的工作。</span><span class="sxs-lookup"><span data-stu-id="7d52c-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="7d52c-112">有关编写 cmdlet 的详细信息，请参阅[编写 Windows PowerShell cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="7d52c-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="7d52c-113">如有必要，请创建解决方案的其余部分：（附加 cmdlet、XML 文件等），并使用模块清单对它们进行说明。</span><span class="sxs-lookup"><span data-stu-id="7d52c-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="7d52c-114">除了描述解决方案中的 cmdlet 程序集外，模块清单还可以描述你希望如何导出和导入模块、将公开哪些 cmdlet 以及哪些其他文件将进入模块。</span><span class="sxs-lookup"><span data-stu-id="7d52c-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="7d52c-115">如前文所述，PowerShell 可以将二进制 cmdlet （如模块）视为不需要额外的工作。</span><span class="sxs-lookup"><span data-stu-id="7d52c-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="7d52c-116">因此，模块清单主要用于将多个文件合并到一个包中，或用于显式控制给定程序集的发布。</span><span class="sxs-lookup"><span data-stu-id="7d52c-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="7d52c-117">有关详细信息，请参阅[如何编写 PowerShell 模块清单](how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="7d52c-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="7d52c-118">下面的代码是一个非常简单C#的代码块，其中包含可用作模块的同一文件中的三个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7d52c-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="7d52c-119">打包解决方案，并将包保存到 PowerShell 模块路径中的某个位置。</span><span class="sxs-lookup"><span data-stu-id="7d52c-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="7d52c-120">@No__t-0 全局环境变量描述 PowerShell 将用于查找模块的默认路径。</span><span class="sxs-lookup"><span data-stu-id="7d52c-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="7d52c-121">例如，在系统上保存模块的通用路径将为 `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`。</span><span class="sxs-lookup"><span data-stu-id="7d52c-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="7d52c-122">如果未使用默认路径，则需要在安装过程中显式声明模块的位置。</span><span class="sxs-lookup"><span data-stu-id="7d52c-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="7d52c-123">请确保创建一个文件夹以将模块保存在中，因为您可能需要使用文件夹存储解决方案的多个程序集和文件。</span><span class="sxs-lookup"><span data-stu-id="7d52c-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="7d52c-124">请注意，从技术上讲，不需要在任何位置将模块安装到 `PSModulePath`-它们只是 PowerShell 将在其中查找模块的默认位置。</span><span class="sxs-lookup"><span data-stu-id="7d52c-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="7d52c-125">但是，除非您有充分的理由将模块存储在其他位置，否则这会被视为最佳做法。</span><span class="sxs-lookup"><span data-stu-id="7d52c-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="7d52c-126">有关详细信息，请参阅[安装 Powershell 模块](./installing-a-powershell-module.md)和[修改 Powershell 模块安装路径](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="7d52c-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="7d52c-127">通过调用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)将模块导入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="7d52c-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="7d52c-128">调用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)会将模块加载到活动内存。</span><span class="sxs-lookup"><span data-stu-id="7d52c-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="7d52c-129">如果你使用的是 PowerShell 3.0 和更高版本，只需在代码中调用模块的名称，就会将其导入。有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="7d52c-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="7d52c-130">导入管理单元程序集作为模块</span><span class="sxs-lookup"><span data-stu-id="7d52c-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="7d52c-131">管理单元程序集中存在的 cmdlet 和提供程序可以作为二进制模块加载。</span><span class="sxs-lookup"><span data-stu-id="7d52c-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="7d52c-132">当管理单元程序集作为二进制模块加载时，管理单元中的 cmdlet 和提供程序可供用户使用，但程序集中的管理单元类将被忽略，并且不会注册管理单元。</span><span class="sxs-lookup"><span data-stu-id="7d52c-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="7d52c-133">因此，即使 cmdlet 和提供程序可用于该会话，Windows PowerShell 提供的管理单元 cmdlet 仍无法检测该管理单元。</span><span class="sxs-lookup"><span data-stu-id="7d52c-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="7d52c-134">此外，管理单元引用的任何格式或类型文件都不能作为二进制模块的一部分导入。</span><span class="sxs-lookup"><span data-stu-id="7d52c-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="7d52c-135">若要导入格式和类型文件，必须创建模块清单。</span><span class="sxs-lookup"><span data-stu-id="7d52c-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="7d52c-136">请参阅[如何编写 PowerShell 模块清单](how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="7d52c-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d52c-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d52c-137">See Also</span></span>

[<span data-ttu-id="7d52c-138">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="7d52c-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
