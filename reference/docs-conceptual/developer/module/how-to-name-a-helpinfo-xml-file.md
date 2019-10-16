---
title: 如何命名 HelpInfo XML 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367196"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="f121c-102">如何命名 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="f121c-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="f121c-103">本主题介绍可更新帮助信息文件（通常称为 HelpInfo XML 文件）所需的名称格式。</span><span class="sxs-lookup"><span data-stu-id="f121c-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="f121c-104">如何命名 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="f121c-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="f121c-105">HelpInfo XML 文件必须具有以下格式的名称。</span><span class="sxs-lookup"><span data-stu-id="f121c-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="f121c-106">名称的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="f121c-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="f121c-107">ModuleName[获取 Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 返回的**ModuleInfo**对象的**Name**属性的值。</span><span class="sxs-lookup"><span data-stu-id="f121c-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="f121c-108">ModuleGUID 模块清单中**GUID**密钥的值。</span><span class="sxs-lookup"><span data-stu-id="f121c-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="f121c-109">例如，如果模块名称为 "TestModule"，并且模块 GUID 为 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，则该模块的 HelpInfo XML 文件的名称将为：</span><span class="sxs-lookup"><span data-stu-id="f121c-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`