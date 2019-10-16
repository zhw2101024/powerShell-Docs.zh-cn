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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360676"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="8c6d6-102">如何设置 HelpInfo XML 版本号</span><span class="sxs-lookup"><span data-stu-id="8c6d6-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="8c6d6-103">本主题说明如何设置和增加可更新帮助信息文件（通常称为 "HelpInfo XML 文件"）中的版本号。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="8c6d6-104">如何设置 HelpInfo XML 版本号</span><span class="sxs-lookup"><span data-stu-id="8c6d6-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="8c6d6-105">HelpInfo XML 文件中的版本号对于可更新帮助的操作至关重要。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="8c6d6-106">只有当远程 HelpInfo XML 文件中的 UI 区域性的版本号大于本地 HelpInfo XML 中该 UI 区域性的版本号，或者没有本地 HelpInfo 时， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 才会下载新的帮助文件。XML 文件。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="8c6d6-107">HelpInfo XML 文件使用由四个部分构成的版本号，该版本号在 Microsoft .NET Framework 的**system.web**类中定义。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="8c6d6-108">格式为 `N1.N2.N3.N4`。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="8c6d6-109">模块作者可以使用**System**类允许的任何版本编号方案。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="8c6d6-110">仅当将该 UI 区域性的新版本的 CAB 文件上传到 HelpInfo XML 文件中的**HelpContentURI**元素所指定的位置时，可更新帮助才需要增加 ui 区域性的版本号。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="8c6d6-111">下面的示例演示了德语（de） UI 区域性的 HelpInfo XML 文件的元素（在版本为2.15.0.10 时）。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="8c6d6-112">UI 区域性的版本号反映了该 UI 区域性的 CAB 文件的版本。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="8c6d6-113">版本号适用于整个 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="8c6d6-114">不能为 CAB 文件中的不同文件设置不同的版本号。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="8c6d6-115">每个 UI 区域性的版本号是独立计算的，无需与模块支持的其他 UI 区域性的版本号相关。</span><span class="sxs-lookup"><span data-stu-id="8c6d6-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>