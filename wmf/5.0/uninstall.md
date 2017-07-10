---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 3392db954c22030bb64ae5093619d23952e1fcdb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="uninstallation-instructions" class="xliff"></a>
# 卸载说明

<a id="using-command-prompt" class="xliff"></a>
## 使用命令提示符
1.  打开“命令提示符”。
2.  运行 [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307)，如下所示：

在 Windows Server 2012 R2 和 Windows 8.1 上：
```powershell
wusa /uninstall /kb:3134758
```
在 Windows Server 2012 上：
```powershell
wusa /uninstall /kb:3134759
```
在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上：
```powershell
wusa /uninstall /kb:3134760
```

<a id="using-control-panel" class="xliff"></a>
## 使用控制面板。
1.  打开“控制面板”。
2.  打开“程序”，然后打开“卸载程序”。
3.  单击“查看已安装的更新”。
4.  从已安装的更新列表中选择“Windows Management Framework 5.0”。 这对应于 *KB3134758*、*KB3134759* 或 *KB3134760*。 单击“卸载”。

