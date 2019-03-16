---
title: 如何设置 HelpInfo XML 版本号 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054129"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="632bc-102">如何设置 HelpInfo XML 版本号</span><span class="sxs-lookup"><span data-stu-id="632bc-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="632bc-103">本主题说明如何设置和增加版本号中的可更新帮助信息文件，通常称为"HelpInfo XML 文件"。</span><span class="sxs-lookup"><span data-stu-id="632bc-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="632bc-104">如何设置 HelpInfo XML 版本号</span><span class="sxs-lookup"><span data-stu-id="632bc-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="632bc-105">HelpInfo XML 文件中的版本号是至关重要的可更新帮助的操作。</span><span class="sxs-lookup"><span data-stu-id="632bc-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="632bc-106">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 下载新的帮助文件，仅当 UI 区域性中的远程 HelpInfo XML 文件的版本号大于该 UI 区域性中的版本号本地 HelpInfo XML，或不存在本地 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="632bc-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="632bc-107">HelpInfo XML 文件使用中定义的四部分版本号**System.Version**的 Microsoft.NET Framework 类。</span><span class="sxs-lookup"><span data-stu-id="632bc-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="632bc-108">格式是`N1.N2.N3.N4`。</span><span class="sxs-lookup"><span data-stu-id="632bc-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="632bc-109">模块作者可以使用任何版本编号的允许的方案**System.Version**类。</span><span class="sxs-lookup"><span data-stu-id="632bc-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="632bc-110">可更新的帮助时，需要仅版本号的 UI 区域性增加该 UI 区域性的 CAB 文件的新版本上载到由指定的位置**HelpContentURI** HelpInfo XML 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="632bc-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="632bc-111">下面的示例显示德语 (DE-DE) UI 区域性时的版本是 2.15.0.10 HelpInfo XML 文件的元素。</span><span class="sxs-lookup"><span data-stu-id="632bc-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="632bc-112">UI 区域性的版本号将反映该 UI 区域性的 CAB 文件的版本。</span><span class="sxs-lookup"><span data-stu-id="632bc-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="632bc-113">版本号应用于整个 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="632bc-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="632bc-114">CAB 文件中，不能设置为不同的文件的版本号不同。</span><span class="sxs-lookup"><span data-stu-id="632bc-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="632bc-115">每个 UI 区域性的版本号单独计算，并不需要与其他模块支持的 UI 区域性的版本号。</span><span class="sxs-lookup"><span data-stu-id="632bc-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>