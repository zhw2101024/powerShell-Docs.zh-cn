---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="b0580-102">基于类的 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="b0580-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="b0580-103">使用类定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="b0580-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="b0580-104">根据反馈，我们已简化了编写基于类的 DSC 资源的操作，并且内容更易于理解。</span><span class="sxs-lookup"><span data-stu-id="b0580-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="b0580-105">基于类的 DSC 资源和 cmdlet DSC 资源提供程序之间的主要区别如下：</span><span class="sxs-lookup"><span data-stu-id="b0580-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="b0580-106">架构的 MOF 文件不是必需的。</span><span class="sxs-lookup"><span data-stu-id="b0580-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="b0580-107">模块文件中的 **DSCResource** 子文件夹不是必需的。</span><span class="sxs-lookup"><span data-stu-id="b0580-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="b0580-108">PowerShell 模块文件可以包含多个 DSC 资源类。</span><span class="sxs-lookup"><span data-stu-id="b0580-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="b0580-109">有关详细信息，请参阅[使用 PowerShell 类编写自定义 DSC 资源](https://msdn.microsoft.com/powershell/dsc/authoringresource)。</span><span class="sxs-lookup"><span data-stu-id="b0580-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

