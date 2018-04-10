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
# <a name="class-based-dsc-resources"></a>基于类的 DSC 资源

## <a name="defining-dsc-resources-with-classes"></a>使用类定义 DSC 资源

根据反馈，我们已简化了编写基于类的 DSC 资源的操作，并且内容更易于理解。
基于类的 DSC 资源和 cmdlet DSC 资源提供程序之间的主要区别如下：

* 架构的 MOF 文件不是必需的。
* 模块文件中的 **DSCResource** 子文件夹不是必需的。
* PowerShell 模块文件可以包含多个 DSC 资源类。

有关详细信息，请参阅[使用 PowerShell 类编写自定义 DSC 资源](https://msdn.microsoft.com/powershell/dsc/authoringresource)。