---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 2af56be1915c148809f52cd9040c45da160ae0a2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="reporting-on-jea"></a>JEA 报告
要报告 JEA 配置的状态，可使用：
1.  **Get-PSSessionConfiguration** 返回给定计算机上所有已注册终结点的列表。
2.  **Get PSSessionCapability** 报告任意给定用户在特定终结点上具有的功能。

下面是 **Get-PSSessionCapability** 的一个示例：
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

若要报告用户在 JEA 会话期间执行的_操作_，你可以：
1. 为该 JEA 终结点启用“即时权限提升”脚本，并查询脚本目录以获取记录了每个用户的操作的完整日志。
2. 打开 PowerShell 模块日志记录并检查 PowerShell 事件日志。