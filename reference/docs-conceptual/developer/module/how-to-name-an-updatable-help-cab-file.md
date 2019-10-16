---
title: 如何为可更新的帮助 CAB 文件命名 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367156"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="cdc52-102">如何命名可更新帮助 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="cdc52-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="cdc52-103">本主题介绍可更新帮助 cabinet 的必需名称格式（。CAB）文件。</span><span class="sxs-lookup"><span data-stu-id="cdc52-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="cdc52-104">如何命名可更新帮助 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="cdc52-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="cdc52-105">可更新的 cabinet （。CAB）文件必须具有以下格式的名称。</span><span class="sxs-lookup"><span data-stu-id="cdc52-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="cdc52-106">名称的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="cdc52-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="cdc52-107">ModuleName[获取 Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 返回的**ModuleInfo**对象的**Name**属性的值。</span><span class="sxs-lookup"><span data-stu-id="cdc52-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="cdc52-108">ModuleGUID 模块清单中**GUID**密钥的值。</span><span class="sxs-lookup"><span data-stu-id="cdc52-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="cdc52-109">UICulture CAB 文件中的帮助文件的 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="cdc52-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="cdc52-110">此值必须与模块的 HelpInfo XML 文件中的一个**UICulture**元素的值匹配。</span><span class="sxs-lookup"><span data-stu-id="cdc52-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="cdc52-111">例如，如果模块名称为 "TestModule"，则模块 GUID 为 9cabb9ad-f2ac 4914-a46b-bfc1bebf07f9，而 UI 区域性为 "en-us"，则 CAB 文件的名称将为：</span><span class="sxs-lookup"><span data-stu-id="cdc52-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`