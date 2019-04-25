---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057909"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="3ad18-102">对 DSC 资源的并行模块版本控制支持</span><span class="sxs-lookup"><span data-stu-id="3ad18-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="3ad18-103">可以并行安装包含 DSC 资源的模块，并且 DSC 配置可以使用系统上所安装资源的特定版本。</span><span class="sxs-lookup"><span data-stu-id="3ad18-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="3ad18-104">有关详细信息，请参阅[使用具有多个版本的资源](https://msdn.microsoft.com/powershell/dsc/sxsresource)。</span><span class="sxs-lookup"><span data-stu-id="3ad18-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="3ad18-105">已知问题</span><span class="sxs-lookup"><span data-stu-id="3ad18-105">Known issues</span></span>

<span data-ttu-id="3ad18-106">在此版本中，下列是并行安装的已知问题：</span><span class="sxs-lookup"><span data-stu-id="3ad18-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="3ad18-107">不支持在同一配置内使用 DSC 资源的两个不同版本。</span><span class="sxs-lookup"><span data-stu-id="3ad18-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
