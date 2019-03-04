---
title: 如何命名可更新的帮助 CAB 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 23303489372cfe7e036fdea842ae75f7e47503c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861283"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="c1ce6-102">如何命名可更新帮助 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="c1ce6-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="c1ce6-103">本主题介绍了可更新帮助 cab 文件的所需的名称格式 (。CAB) 文件。</span><span class="sxs-lookup"><span data-stu-id="c1ce6-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="c1ce6-104">如何命名可更新帮助 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="c1ce6-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="c1ce6-105">可更新的 cab 文件 (。CAB) 文件必须具有以下格式的名称。</span><span class="sxs-lookup"><span data-stu-id="c1ce6-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="c1ce6-106">名称的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="c1ce6-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="c1ce6-107">ModuleName 值的**名称**的属性**ModuleInfo**对象[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 将返回。</span><span class="sxs-lookup"><span data-stu-id="c1ce6-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="c1ce6-108">值**名称**的属性**ModuleInfo**对象[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 将返回。</span><span class="sxs-lookup"><span data-stu-id="c1ce6-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="c1ce6-109">ModuleGUID 值的**GUID**密钥模块清单中。</span><span class="sxs-lookup"><span data-stu-id="c1ce6-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="c1ce6-110">UICulture 的 UI 区域性的 CAB 文件中的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="c1ce6-110">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="c1ce6-111">此值必须匹配的值之一**UICulture**模块的 HelpInfo XML 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="c1ce6-111">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="c1ce6-112">例如，如果模块名称为"TestModule"，模块 GUID 是 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，和 UI 区域性为"EN-US"，CAB 文件的名称将为：</span><span class="sxs-lookup"><span data-stu-id="c1ce6-112">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`