---
title: 加载和导出格式设置数据 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365116"
---
# <a name="loading-and-exporting-formatting-data"></a><span data-ttu-id="28ad3-102">加载和导出格式设置数据</span><span class="sxs-lookup"><span data-stu-id="28ad3-102">Loading and Exporting Formatting Data</span></span>

<span data-ttu-id="28ad3-103">创建格式化文件后，需要通过将文件加载到当前会话中来更新会话的格式数据。</span><span class="sxs-lookup"><span data-stu-id="28ad3-103">Once you have created your formatting file, you need to update the format data of the session by loading your files into the current session.</span></span> <span data-ttu-id="28ad3-104">（Windows PowerShell 提供的格式化文件由在打开当前会话时注册的管理单元加载。）当前会话的格式数据更新后，Windows PowerShell 将使用该数据显示与已加载的格式设置文件中定义的视图关联的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="28ad3-104">(The formatting files provided by Windows PowerShell are loaded by snap-ins that are registered when the current session is opened.) Once the format data of the current session is updated, Windows PowerShell uses that data to display the .NET objects associated with the views defined in the loaded formatting files.</span></span> <span data-ttu-id="28ad3-105">可以加载到当前会话中的格式化文件数没有限制。</span><span class="sxs-lookup"><span data-stu-id="28ad3-105">There is no limit to the number of formatting files that you can load into the current session.</span></span> <span data-ttu-id="28ad3-106">除了更新格式设置数据以外，还可以将当前会话中的格式数据导出回格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="28ad3-106">In addition to updating the formatting data, you can export the format data in the current session back to a formatting file.</span></span>

## <a name="loading-format-data"></a><span data-ttu-id="28ad3-107">正在加载格式数据</span><span class="sxs-lookup"><span data-stu-id="28ad3-107">Loading format data</span></span>

<span data-ttu-id="28ad3-108">可以使用以下方法将格式化文件加载到当前会话中：</span><span class="sxs-lookup"><span data-stu-id="28ad3-108">Formatting files can be loaded into the current session using the following methods:</span></span>

- <span data-ttu-id="28ad3-109">你可以从命令行将格式设置文件导入到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="28ad3-109">You can import the formatting file into the current session from the command line.</span></span> <span data-ttu-id="28ad3-110">按照以下过程中所述，使用[update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="28ad3-110">Use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet as described in the following procedure.</span></span>

- <span data-ttu-id="28ad3-111">你可以创建一个引用你的格式化文件的模块清单。</span><span class="sxs-lookup"><span data-stu-id="28ad3-111">You can create a module manifest that references your formatting file.</span></span> <span data-ttu-id="28ad3-112">模块允许您打包格式化文件以进行分发。</span><span class="sxs-lookup"><span data-stu-id="28ad3-112">Modules allow you to package you formatting files for distribution.</span></span> <span data-ttu-id="28ad3-113">使用[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 创建清单，并使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 将模块加载到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="28ad3-113">Use the [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet to create the manifest, and the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet to load the module into the current session.</span></span> <span data-ttu-id="28ad3-114">有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="28ad3-114">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="28ad3-115">你可以创建一个引用你的格式化文件的管理单元。</span><span class="sxs-lookup"><span data-stu-id="28ad3-115">You can create a snap-in that references your formatting file.</span></span> <span data-ttu-id="28ad3-116">使用[add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn.Formats)可引用您的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="28ad3-116">Use the [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) to reference your formatting files.</span></span> <span data-ttu-id="28ad3-117">强烈建议使用模块打包 cmdlet 以及任何关联的格式和类型文件以进行分发。</span><span class="sxs-lookup"><span data-stu-id="28ad3-117">It is strongly encouraged to use modules to package cmdlets, and any associated formatting and types files for distribution.</span></span> <span data-ttu-id="28ad3-118">有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="28ad3-118">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="28ad3-119">如果以编程方式调用命令，则可以将格式设置文件条目添加到运行命令的运行空间的初始会话状态。</span><span class="sxs-lookup"><span data-stu-id="28ad3-119">If you are invoking commands programmatically, you can add a formatting file entry to the initial session state of the runspace where the commands are run.</span></span> <span data-ttu-id="28ad3-120">有关用于添加格式化文件的 .NET 类型的详细信息，请参阅[Sessionstateformatentry？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry)类。</span><span class="sxs-lookup"><span data-stu-id="28ad3-120">For more information about .NET type used to add the formatting file, see the [System.Management.Automation.Runspaces.Sessionstateformatentry?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) class.</span></span>

<span data-ttu-id="28ad3-121">加载格式设置文件时，会将其添加到 Windows PowerShell 用来确定在命令行显示对象时使用的视图的内部列表。</span><span class="sxs-lookup"><span data-stu-id="28ad3-121">When a formatting file is loaded, it is added to an internal list that Windows PowerShell uses to determine which view to use when displaying objects at the command line.</span></span> <span data-ttu-id="28ad3-122">您可以在列表开头添加格式文件，也可以将其追加到列表的末尾。</span><span class="sxs-lookup"><span data-stu-id="28ad3-122">You can prepend your formatting file to the beginning of the list, or you can append it to the end of the list.</span></span> <span data-ttu-id="28ad3-123">如果正在加载为定义了现有视图的对象定义视图（例如，当你想要更改 Windows PowerShell core cmdlet 返回的对象的方式）时，了解将格式设置文件添加到此列表中的位置非常重要。 会.</span><span class="sxs-lookup"><span data-stu-id="28ad3-123">Knowing where your formatting file is added to this list is important if you are loading formatting file that defines a view for an object that has an existing view defined, such as when you want to change how an object that is returned by a Windows PowerShell core cmdlet is displayed.</span></span> <span data-ttu-id="28ad3-124">如果正在加载的格式设置文件定义对象的唯一视图，则可以使用前面所述的任何方法。</span><span class="sxs-lookup"><span data-stu-id="28ad3-124">If you are loading a formatting file that defines the only view for an object, you can use any of the methods described previously.</span></span>  <span data-ttu-id="28ad3-125">如果要加载的格式设置文件定义了对象的其他视图，则必须使用[update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，并将文件预置到列表的开头。</span><span class="sxs-lookup"><span data-stu-id="28ad3-125">If you are loading a formatting file that defines another view for an object, you must use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet and prepend your file to the beginning of the list.</span></span>

## <a name="storing-your-formatting-file"></a><span data-ttu-id="28ad3-126">存储格式设置文件</span><span class="sxs-lookup"><span data-stu-id="28ad3-126">Storing Your Formatting File</span></span>

<span data-ttu-id="28ad3-127">不要求在磁盘上存储格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="28ad3-127">There is no requirement for where your formatting files are stored on disk.</span></span> <span data-ttu-id="28ad3-128">但是，强烈建议将它们存储在以下文件夹中： `user\documents\windowspowershell\`</span><span class="sxs-lookup"><span data-stu-id="28ad3-128">However, it is strongly suggested that you store them in the following folder: `user\documents\windowspowershell\`</span></span>

#### <a name="loading-a-format-file-using-import-formatdata"></a><span data-ttu-id="28ad3-129">使用 Update-formatdata 加载格式化文件</span><span class="sxs-lookup"><span data-stu-id="28ad3-129">Loading a format file using Import-FormatData</span></span>

1. <span data-ttu-id="28ad3-130">将格式化文件存储到磁盘。</span><span class="sxs-lookup"><span data-stu-id="28ad3-130">Store your formatting file to disk.</span></span>

2. <span data-ttu-id="28ad3-131">使用以下命令之一运行[update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="28ad3-131">Run the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet using one of the following commands.</span></span>

   <span data-ttu-id="28ad3-132">若要在列表的前面添加格式文件，请使用此命令。</span><span class="sxs-lookup"><span data-stu-id="28ad3-132">To add your formatting file to the front of the list use this command.</span></span> <span data-ttu-id="28ad3-133">如果要更改对象的显示方式，请使用此命令。</span><span class="sxs-lookup"><span data-stu-id="28ad3-133">Use this command if you are changing how an object is displayed.</span></span>

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   <span data-ttu-id="28ad3-134">若要在列表的末尾添加格式文件，请使用此命令。</span><span class="sxs-lookup"><span data-stu-id="28ad3-134">To add your formatting file to the end of the list use this command.</span></span>

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   <span data-ttu-id="28ad3-135">使用[update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 添加文件后，当会话处于打开状态时，不能从列表中删除该文件。</span><span class="sxs-lookup"><span data-stu-id="28ad3-135">Once you have added a file using the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, you cannot remove the file from the list while the session is open.</span></span> <span data-ttu-id="28ad3-136">要从列表中删除格式化文件，必须关闭会话。</span><span class="sxs-lookup"><span data-stu-id="28ad3-136">You must close the session to remove the formatting file from the list.</span></span>

## <a name="exporting-format-data"></a><span data-ttu-id="28ad3-137">导出格式数据</span><span class="sxs-lookup"><span data-stu-id="28ad3-137">Exporting format data</span></span>

<span data-ttu-id="28ad3-138">在此处插入分区正文。</span><span class="sxs-lookup"><span data-stu-id="28ad3-138">Insert section body here.</span></span>
