---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 信息流
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147607"
---
# <a name="information-stream"></a><span data-ttu-id="71818-103">信息流</span><span class="sxs-lookup"><span data-stu-id="71818-103">Information Stream</span></span>

<span data-ttu-id="71818-104">PowerShell 5.0 添加了新的结构化信息  流以在脚本及其主机之间传输结构化数据。</span><span class="sxs-lookup"><span data-stu-id="71818-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="71818-105">已将 `Write-Host` 更新为将其输出发出到信息  流，你现在可以在信息流中捕获或抑制它。</span><span class="sxs-lookup"><span data-stu-id="71818-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="71818-106">新的 `Write-Information` cmdlet 与 InformationVariable  和 InformationAction  通用参数一起使用可以增加灵活性并启用更多功能。</span><span class="sxs-lookup"><span data-stu-id="71818-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="71818-107">以下函数使用充分利用新信息  流的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="71818-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

<span data-ttu-id="71818-108">以下示例显示运行此函数的结果。</span><span class="sxs-lookup"><span data-stu-id="71818-108">The following examples show the results of running this function.</span></span>

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="71818-109">`$r` 变量已捕获脚本变量 `$p` 中的进程信息。</span><span class="sxs-lookup"><span data-stu-id="71818-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="71818-110">与 `Write-Host` cmdlet 不同，使用 `Write-Information` 的 InformationVariable  参数可以捕获变量中的输出。</span><span class="sxs-lookup"><span data-stu-id="71818-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="71818-111">使用标记  可以为发送到信息  流的消息创建单独通道。</span><span class="sxs-lookup"><span data-stu-id="71818-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

<span data-ttu-id="71818-112">使用标记将消息发送到信息  流时，该消息不会显示在主机应用程序中，但可以使用标记名称进行检索。</span><span class="sxs-lookup"><span data-stu-id="71818-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="71818-113">例如：</span><span class="sxs-lookup"><span data-stu-id="71818-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```