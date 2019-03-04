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
ms.openlocfilehash: 4929a5b1c9f73bb12b6df975e03fc529db3565ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863313"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>如何设置 HelpInfo XML 版本号

本主题说明如何设置和增加版本号中的可更新帮助信息文件，通常称为"HelpInfo XML 文件"。

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>如何设置 HelpInfo XML 版本号

HelpInfo XML 文件中的版本号是至关重要的可更新帮助的操作。 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 下载新的帮助文件，仅当 UI 区域性中的远程 HelpInfo XML 文件的版本号大于该 UI 区域性中的版本号本地 HelpInfo XML，或不存在本地 HelpInfo XML 文件。
HelpInfo XML 文件中的版本号是至关重要的可更新帮助的操作。 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 下载新的帮助文件，仅当 UI 区域性中的远程 HelpInfo XML 文件的版本号大于该 UI 区域性中的版本号本地 HelpInfo XML，或不存在本地 HelpInfo XML 文件。

HelpInfo XML 文件使用中定义的四部分版本号**System.Version**的 Microsoft.NET Framework 类。 格式是`N1.N2.N3.N4`。 模块作者可以使用任何版本编号的允许的方案**System.Version**类。 可更新的帮助时，需要仅版本号的 UI 区域性增加该 UI 区域性的 CAB 文件的新版本上载到由指定的位置**HelpContentURI** HelpInfo XML 文件中的元素。

下面的示例显示德语 (DE-DE) UI 区域性时的版本是 2.15.0.10 HelpInfo XML 文件的元素。

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

UI 区域性的版本号将反映该 UI 区域性的 CAB 文件的版本。 版本号应用于整个 CAB 文件。 CAB 文件中，不能设置为不同的文件的版本号不同。 每个 UI 区域性的版本号单独计算，并不需要与其他模块支持的 UI 区域性的版本号。