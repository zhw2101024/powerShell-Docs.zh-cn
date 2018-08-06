---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Log 资源
ms.openlocfilehash: 50fd6cd31ba426108830fcf124a767318060a95d
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268426"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="fdd31-103">DSC Log 资源</span><span class="sxs-lookup"><span data-stu-id="fdd31-103">DSC Log Resource</span></span>

<span data-ttu-id="fdd31-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fdd31-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="fdd31-105">Windows PowerShell Desired State Configuration (DSC) 内的 __Log__ 资源提供了将消息写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的机制。</span><span class="sxs-lookup"><span data-stu-id="fdd31-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="fdd31-106">默认情况下，仅启用 DSC 的运行日志。</span><span class="sxs-lookup"><span data-stu-id="fdd31-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="fdd31-107">必须先启用“分析”日志才能看到或使用它。</span><span class="sxs-lookup"><span data-stu-id="fdd31-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="fdd31-108">有关详细信息，请参阅 [DSC 事件日志在哪里？](troubleshooting.md#where-are-dsc-event-logs)。</span><span class="sxs-lookup"><span data-stu-id="fdd31-108">For more information, see [Where are DSC Event Logs?](troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="fdd31-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="fdd31-109">Properties</span></span>

| <span data-ttu-id="fdd31-110">属性</span><span class="sxs-lookup"><span data-stu-id="fdd31-110">Property</span></span> | <span data-ttu-id="fdd31-111">说明</span><span class="sxs-lookup"><span data-stu-id="fdd31-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fdd31-112">消息</span><span class="sxs-lookup"><span data-stu-id="fdd31-112">Message</span></span>| <span data-ttu-id="fdd31-113">指示要写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的消息。</span><span class="sxs-lookup"><span data-stu-id="fdd31-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="fdd31-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fdd31-114">DependsOn</span></span> | <span data-ttu-id="fdd31-115">指示必须先运行其他资源的配置，再写入此日志消息。</span><span class="sxs-lookup"><span data-stu-id="fdd31-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="fdd31-116">例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = '[ResourceType]ResourceName'`。</span><span class="sxs-lookup"><span data-stu-id="fdd31-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="fdd31-117">示例</span><span class="sxs-lookup"><span data-stu-id="fdd31-117">Example</span></span>

<span data-ttu-id="fdd31-118">下面的示例演示如何在 Microsoft-Windows-Desired State Configuration/Analytic 事件日志中纳入消息。</span><span class="sxs-lookup"><span data-stu-id="fdd31-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="fdd31-119">如果在配置此资源后运行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，它始终会返回 $false。</span><span class="sxs-lookup"><span data-stu-id="fdd31-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```