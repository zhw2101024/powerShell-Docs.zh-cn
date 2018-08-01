---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268572"
---
# <a name="reporting-on-jea"></a><span data-ttu-id="b62cf-102">JEA 报告</span><span class="sxs-lookup"><span data-stu-id="b62cf-102">Reporting on JEA</span></span>

<span data-ttu-id="b62cf-103">要报告 JEA 配置的状态，可使用：</span><span class="sxs-lookup"><span data-stu-id="b62cf-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="b62cf-104">**Get-PSSessionConfiguration** 返回给定计算机上所有已注册终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="b62cf-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2. <span data-ttu-id="b62cf-105">**Get PSSessionCapability** 报告任意给定用户在特定终结点上具有的功能。</span><span class="sxs-lookup"><span data-stu-id="b62cf-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="b62cf-106">下面是 Get-PSSessionCapability 示例：</span><span class="sxs-lookup"><span data-stu-id="b62cf-106">Here's an example of **Get-PSSessionCapability**:</span></span>

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

<span data-ttu-id="b62cf-107">若要报告用户在 JEA 会话期间执行的_操作_，你可以：</span><span class="sxs-lookup"><span data-stu-id="b62cf-107">To report on the _actions_ users took during a JEA session, you can:</span></span>

1. <span data-ttu-id="b62cf-108">为该 JEA 终结点启用“即时权限提升”脚本，并查询脚本目录以获取记录了每个用户的操作的完整日志。</span><span class="sxs-lookup"><span data-stu-id="b62cf-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="b62cf-109">打开 PowerShell 模块日志记录并检查 PowerShell 事件日志。</span><span class="sxs-lookup"><span data-stu-id="b62cf-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>