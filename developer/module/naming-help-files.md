---
title: 命名的帮助文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856663"
---
# <a name="naming-help-files"></a><span data-ttu-id="19456-102">命名帮助文件</span><span class="sxs-lookup"><span data-stu-id="19456-102">Naming Help Files</span></span>

<span data-ttu-id="19456-103">本主题说明如何基于 XML 的帮助文件命名，以便[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 可以找到它。</span><span class="sxs-lookup"><span data-stu-id="19456-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="19456-104">为每个命令类型不同的名称要求。</span><span class="sxs-lookup"><span data-stu-id="19456-104">The name requirements differ for each command type.</span></span>
<span data-ttu-id="19456-105">本主题说明如何基于 XML 的帮助文件命名，以便[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 可以找到它。</span><span class="sxs-lookup"><span data-stu-id="19456-105">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="19456-106">为每个命令类型不同的名称要求。</span><span class="sxs-lookup"><span data-stu-id="19456-106">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="19456-107">Cmdlet 帮助文件</span><span class="sxs-lookup"><span data-stu-id="19456-107">Cmdlet Help Files</span></span>

<span data-ttu-id="19456-108">帮助文件的C#cmdlet 必须命名为程序集在其中定义该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="19456-108">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="19456-109">使用以下文件名称格式：</span><span class="sxs-lookup"><span data-stu-id="19456-109">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="19456-110">程序集名称格式是必需的即使该程序集是嵌套的模块。</span><span class="sxs-lookup"><span data-stu-id="19456-110">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="19456-111">例如， [Get-winevent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Microsoft.PowerShell.Diagnostics.dll 程序集中定义 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="19456-111">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="19456-112">`Get-Help` Cmdlet 查找帮助主题的`Get-WinEvent`cmdlet 仅在模块目录中的 Microsoft.PowerShell.Diagnostics.dll help.xml 文件中。</span><span class="sxs-lookup"><span data-stu-id="19456-112">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>
<span data-ttu-id="19456-113">例如， [Get-winevent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Microsoft.PowerShell.Diagnostics.dll 程序集中定义 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="19456-113">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="19456-114">`Get-Help` Cmdlet 查找帮助主题的`Get-WinEvent`cmdlet 仅在模块目录中的 Microsoft.PowerShell.Diagnostics.dll help.xml 文件中。</span><span class="sxs-lookup"><span data-stu-id="19456-114">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="19456-115">提供程序的帮助文件</span><span class="sxs-lookup"><span data-stu-id="19456-115">Provider Help files</span></span>

<span data-ttu-id="19456-116">必须在其中定义该提供程序程序集命名为 Windows PowerShell 提供程序的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="19456-116">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="19456-117">使用以下文件名称格式：</span><span class="sxs-lookup"><span data-stu-id="19456-117">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="19456-118">程序集名称格式是必需的即使该程序集是嵌套的模块。</span><span class="sxs-lookup"><span data-stu-id="19456-118">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="19456-119">例如，Certificate 提供程序是 Microsoft.PowerShell.Security.dll 集中定义。</span><span class="sxs-lookup"><span data-stu-id="19456-119">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="19456-120">`Get-Help` Cmdlet 为证书提供程序仅在模块目录中的 Microsoft.PowerShell.Security.dll help.xml 文件中查找的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="19456-120">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="19456-121">函数的帮助文件</span><span class="sxs-lookup"><span data-stu-id="19456-121">Function Help Files</span></span>

<span data-ttu-id="19456-122">函数可以通过使用所述[基于注释的帮助](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)或 XML 帮助文件中所述。</span><span class="sxs-lookup"><span data-stu-id="19456-122">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="19456-123">该函数时的 XML 文件中记录该函数必须具有`.ExternalHelp`注释将函数与 XML 文件相关联的关键字。</span><span class="sxs-lookup"><span data-stu-id="19456-123">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="19456-124">否则为`Get-Help`cmdlet 找不到帮助文件。</span><span class="sxs-lookup"><span data-stu-id="19456-124">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>
<span data-ttu-id="19456-125">函数可以通过使用所述[基于注释的帮助](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)或 XML 帮助文件中所述。</span><span class="sxs-lookup"><span data-stu-id="19456-125">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="19456-126">该函数时的 XML 文件中记录该函数必须具有`.ExternalHelp`注释将函数与 XML 文件相关联的关键字。</span><span class="sxs-lookup"><span data-stu-id="19456-126">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="19456-127">否则为`Get-Help`cmdlet 找不到帮助文件。</span><span class="sxs-lookup"><span data-stu-id="19456-127">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="19456-128">没有函数帮助文件的技术要求的名称。</span><span class="sxs-lookup"><span data-stu-id="19456-128">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="19456-129">但是，最佳做法是在其中定义该函数的脚本模块的帮助文件的名称。</span><span class="sxs-lookup"><span data-stu-id="19456-129">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="19456-130">例如，以下函数定义 MyModule.psm1 文件中。</span><span class="sxs-lookup"><span data-stu-id="19456-130">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="19456-131">CIM 命令的帮助文件</span><span class="sxs-lookup"><span data-stu-id="19456-131">CIM Command Help Files</span></span>

<span data-ttu-id="19456-132">必须在其中定义 CIM 命令的 CDXML 文件命名为 CIM 命令的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="19456-132">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="19456-133">使用以下文件名称格式：</span><span class="sxs-lookup"><span data-stu-id="19456-133">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="19456-134">可以作为嵌套模块的模块中包含的 CDXML 文件中定义了 CIM 命令。</span><span class="sxs-lookup"><span data-stu-id="19456-134">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="19456-135">Windows PowerShell CIM 命令导入到会话中作为函数时，将添加`.ExternalHelp`注释将函数与 XML 帮助相关联的函数定义的关键字文件名为在其中定义 CIM 命令的 CDXML 文件。</span><span class="sxs-lookup"><span data-stu-id="19456-135">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="19456-136">脚本工作流的帮助文件</span><span class="sxs-lookup"><span data-stu-id="19456-136">Script Workflow Help Files</span></span>

<span data-ttu-id="19456-137">在模块中包含的脚本工作流可以在基于 XML 的帮助文件中所述。</span><span class="sxs-lookup"><span data-stu-id="19456-137">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="19456-138">没有帮助文件的技术要求的名称。</span><span class="sxs-lookup"><span data-stu-id="19456-138">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="19456-139">但是，最佳做法是在其中定义脚本工作流脚本模块的帮助文件的名称。</span><span class="sxs-lookup"><span data-stu-id="19456-139">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="19456-140">例如：</span><span class="sxs-lookup"><span data-stu-id="19456-140">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="19456-141">脚本工作流不需要与其他脚本化命令不同`.ExternalHelp`注释关键字来使其与帮助文件关联。</span><span class="sxs-lookup"><span data-stu-id="19456-141">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="19456-142">相反，Windows PowerShell 的基于 XML 的帮助文件的模块目录的 UI 区域性特定的子目录中搜索并查找有关的所有文件中的脚本工作流的帮助。</span><span class="sxs-lookup"><span data-stu-id="19456-142">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="19456-143">`.ExternalHelp` 将忽略注释关键字。</span><span class="sxs-lookup"><span data-stu-id="19456-143">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="19456-144">因为`.ExternalHelp`注释关键字将被忽略， `Get-Help` cmdlet 可以找到帮助为脚本工作流仅当它们包含在模块中。</span><span class="sxs-lookup"><span data-stu-id="19456-144">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>