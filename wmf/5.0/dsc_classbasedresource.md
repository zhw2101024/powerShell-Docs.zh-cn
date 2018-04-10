---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="cd95d-102">基于类的 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="cd95d-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="cd95d-103">使用类定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="cd95d-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="cd95d-104">根据反馈，我们已简化了编写基于类的 DSC 资源的操作，并且内容更易于理解。</span><span class="sxs-lookup"><span data-stu-id="cd95d-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="cd95d-105">基于类的 DSC 资源和 cmdlet DSC 资源提供程序之间的主要区别如下：</span><span class="sxs-lookup"><span data-stu-id="cd95d-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="cd95d-106">架构的 MOF 文件不是必需的。</span><span class="sxs-lookup"><span data-stu-id="cd95d-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="cd95d-107">模块文件中的 **DSCResource** 子文件夹不是必需的。</span><span class="sxs-lookup"><span data-stu-id="cd95d-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="cd95d-108">PowerShell 模块文件可以包含多个 DSC 资源类。</span><span class="sxs-lookup"><span data-stu-id="cd95d-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="cd95d-109">有关详细信息，请参阅[使用 PowerShell 类编写自定义 DSC 资源](https://msdn.microsoft.com/powershell/dsc/authoringresource)。</span><span class="sxs-lookup"><span data-stu-id="cd95d-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>