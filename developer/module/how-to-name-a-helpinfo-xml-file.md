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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082390"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="b426b-102">如何命名 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="b426b-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="b426b-103">本主题介绍了可更新帮助信息文件，通常称为 HelpInfo XML 文件的所需的名称格式。</span><span class="sxs-lookup"><span data-stu-id="b426b-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="b426b-104">如何命名 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="b426b-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="b426b-105">HelpInfo XML 文件必须具有以下格式的名称。</span><span class="sxs-lookup"><span data-stu-id="b426b-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="b426b-106">名称的元素如下所示。</span><span class="sxs-lookup"><span data-stu-id="b426b-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="b426b-107">ModuleName 值的**名称**的属性**ModuleInfo**对象[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 将返回。</span><span class="sxs-lookup"><span data-stu-id="b426b-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="b426b-108">ModuleGUID 值的**GUID**密钥模块清单中。</span><span class="sxs-lookup"><span data-stu-id="b426b-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="b426b-109">例如，如果模块名称为"TestModule"，模块 GUID 为 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9，则该模块的 HelpInfo XML 文件的名称将为：</span><span class="sxs-lookup"><span data-stu-id="b426b-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`