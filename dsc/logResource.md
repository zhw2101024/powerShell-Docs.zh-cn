---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Log 资源
ms.openlocfilehash: c7e1957540da2fd85a30f739e0f69bdb6975a4d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-log-resource"></a><span data-ttu-id="9b0bf-103">DSC Log 资源</span><span class="sxs-lookup"><span data-stu-id="9b0bf-103">DSC Log Resource</span></span>

> <span data-ttu-id="9b0bf-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9b0bf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9b0bf-105">Windows PowerShell Desired State Configuration (DSC) 内的 __Log__ 资源提供了将消息写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的机制。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="9b0bf-106">注意：默认情况下，仅启用 DSC 的“操作”日志。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="9b0bf-107">必须先启用“分析”日志才能看到或使用它。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="9b0bf-108">请参阅以下文章。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-108">See the following article.</span></span>

[<span data-ttu-id="9b0bf-109">DSC 事件日志在哪里？</span><span class="sxs-lookup"><span data-stu-id="9b0bf-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="9b0bf-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="9b0bf-110">Properties</span></span>
|  <span data-ttu-id="9b0bf-111">属性</span><span class="sxs-lookup"><span data-stu-id="9b0bf-111">Property</span></span>  |  <span data-ttu-id="9b0bf-112">说明</span><span class="sxs-lookup"><span data-stu-id="9b0bf-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="9b0bf-113">消息</span><span class="sxs-lookup"><span data-stu-id="9b0bf-113">Message</span></span>| <span data-ttu-id="9b0bf-114">指示要写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的消息。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="9b0bf-115">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9b0bf-115">DependsOn</span></span> | <span data-ttu-id="9b0bf-116">指示必须先运行其他资源的配置，再写入此日志消息。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="9b0bf-117">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="9b0bf-118">示例</span><span class="sxs-lookup"><span data-stu-id="9b0bf-118">Example</span></span>

<span data-ttu-id="9b0bf-119">下面的示例演示如何在 Microsoft-Windows-Desired State Configuration/Analytic 事件日志中纳入消息。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="9b0bf-120">**注意**：如果你在配置此资源后运行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，它将始终返回 **$false**。</span><span class="sxs-lookup"><span data-stu-id="9b0bf-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```