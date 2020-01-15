---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Log 资源
ms.openlocfilehash: 0a2f12793357fdf10bd4a2f6003f9dc2276b173c
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870755"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="a817b-103">DSC Log 资源</span><span class="sxs-lookup"><span data-stu-id="a817b-103">DSC Log Resource</span></span>

> <span data-ttu-id="a817b-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a817b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="a817b-105">Windows PowerShell Desired State Configuration (DSC) 内的 **Log** 资源提供了将消息写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的机制。</span><span class="sxs-lookup"><span data-stu-id="a817b-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

## <a name="syntax"></a><span data-ttu-id="a817b-106">语法</span><span class="sxs-lookup"><span data-stu-id="a817b-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="a817b-107">默认情况下，仅启用 DSC 的运行日志。</span><span class="sxs-lookup"><span data-stu-id="a817b-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="a817b-108">必须先启用“分析”日志才能看到或使用它。</span><span class="sxs-lookup"><span data-stu-id="a817b-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="a817b-109">有关详细信息，请参阅 [DSC 事件日志在哪里？](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs)。</span><span class="sxs-lookup"><span data-stu-id="a817b-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="a817b-110">属性</span><span class="sxs-lookup"><span data-stu-id="a817b-110">Properties</span></span>

| <span data-ttu-id="a817b-111">properties</span><span class="sxs-lookup"><span data-stu-id="a817b-111">Property</span></span> |                                                   <span data-ttu-id="a817b-112">说明</span><span class="sxs-lookup"><span data-stu-id="a817b-112">Description</span></span>                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="a817b-113">消息</span><span class="sxs-lookup"><span data-stu-id="a817b-113">Message</span></span>  | <span data-ttu-id="a817b-114">指示要写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的消息。</span><span class="sxs-lookup"><span data-stu-id="a817b-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a817b-115">公共属性</span><span class="sxs-lookup"><span data-stu-id="a817b-115">Common properties</span></span>

|       <span data-ttu-id="a817b-116">properties</span><span class="sxs-lookup"><span data-stu-id="a817b-116">Property</span></span>       |                                                                                                                                                          <span data-ttu-id="a817b-117">说明</span><span class="sxs-lookup"><span data-stu-id="a817b-117">Description</span></span>                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="a817b-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a817b-118">DependsOn</span></span>            | <span data-ttu-id="a817b-119">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="a817b-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a817b-120">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="a817b-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
| <span data-ttu-id="a817b-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a817b-121">PsDscRunAsCredential</span></span> | <span data-ttu-id="a817b-122">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="a817b-122">Sets the credential for running the entire resource as.</span></span>                                                                                                                                                                                                                                                                        |

> [!NOTE]
> <span data-ttu-id="a817b-123">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="a817b-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="a817b-124">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="a817b-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="a817b-125">示例</span><span class="sxs-lookup"><span data-stu-id="a817b-125">Example</span></span>

<span data-ttu-id="a817b-126">下面的示例演示如何在 Microsoft-Windows-Desired State Configuration/Analytic 事件日志中纳入消息。</span><span class="sxs-lookup"><span data-stu-id="a817b-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="a817b-127">如果在配置此资源后运行 [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration?view=powershell-5.1)，它始终会返回 $false  。</span><span class="sxs-lookup"><span data-stu-id="a817b-127">If you run [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration?view=powershell-5.1) with this resource configured, it will always return **$false**.</span></span>

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
