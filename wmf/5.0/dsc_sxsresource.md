---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="7a3c5-102">对 DSC 资源的并行模块版本控制支持</span><span class="sxs-lookup"><span data-stu-id="7a3c5-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="7a3c5-103">可以并行安装包含 DSC 资源的模块，并且 DSC 配置可以使用系统上所安装资源的特定版本。</span><span class="sxs-lookup"><span data-stu-id="7a3c5-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="7a3c5-104">有关详细信息，请参阅[使用具有多个版本的资源](https://msdn.microsoft.com/powershell/dsc/sxsresource)。</span><span class="sxs-lookup"><span data-stu-id="7a3c5-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="7a3c5-105">已知问题</span><span class="sxs-lookup"><span data-stu-id="7a3c5-105">Known issues</span></span>

<span data-ttu-id="7a3c5-106">在此版本中，下列是并行安装的已知问题：</span><span class="sxs-lookup"><span data-stu-id="7a3c5-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="7a3c5-107">不支持在同一配置内使用 DSC 资源的两个不同版本。</span><span class="sxs-lookup"><span data-stu-id="7a3c5-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>

