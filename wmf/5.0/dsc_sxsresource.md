---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218427"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>对 DSC 资源的并行模块版本控制支持

可以并行安装包含 DSC 资源的模块，并且 DSC 配置可以使用系统上所安装资源的特定版本。

有关详细信息，请参阅[使用具有多个版本的资源](https://msdn.microsoft.com/powershell/dsc/sxsresource)。

## <a name="known-issues"></a>已知问题

在此版本中，下列是并行安装的已知问题：

-   不支持在同一配置内使用 DSC 资源的两个不同版本。
