---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 配置中的条件语句和循环
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080129"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="21762-103">配置中的条件语句和循环</span><span class="sxs-lookup"><span data-stu-id="21762-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="21762-104">可以使用 PowerShell 流控制关键字使[配置](configurations.md)更加动态。</span><span class="sxs-lookup"><span data-stu-id="21762-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="21762-105">本文将介绍如何使用条件语句和循环来使配置更加动态。</span><span class="sxs-lookup"><span data-stu-id="21762-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="21762-106">将条件语句和循环与[参数](add-parameters-to-a-configuration.md)和[配置数据](configData.md)结合使用，用户可以在编译配置时更灵活地进行控制。</span><span class="sxs-lookup"><span data-stu-id="21762-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="21762-107">就像函数或脚本块一样，可以在配置中使用任何 PowerShell 语言。</span><span class="sxs-lookup"><span data-stu-id="21762-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="21762-108">只有在调用配置来编译“.mof”文件时才会计算使用的语句。</span><span class="sxs-lookup"><span data-stu-id="21762-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="21762-109">下面的示例展示了一些简单的场景来演示概念。</span><span class="sxs-lookup"><span data-stu-id="21762-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="21762-110">条件语句和循环通常与参数和配置数据一起使用。</span><span class="sxs-lookup"><span data-stu-id="21762-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="21762-111">在这个简单示例中，Service 资源块在编译时检索服务的当前状态，以生成维护其当前状态的“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="21762-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="21762-112">使用动态资源块将抢占 Intellisense 的效率。</span><span class="sxs-lookup"><span data-stu-id="21762-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="21762-113">在编译配置之前，PowerShell 解析器无法确定指定的值是否可接受。</span><span class="sxs-lookup"><span data-stu-id="21762-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="21762-114">此外，可以使用 `foreach` 循环为当前计算机上的每个服务创建一个 Service 块资源。</span><span class="sxs-lookup"><span data-stu-id="21762-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="21762-115">还可以仅使用简单的 `if` 语句为联机计算机创建配置。</span><span class="sxs-lookup"><span data-stu-id="21762-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="21762-116">上述示例中的动态资源块引用当前计算机。</span><span class="sxs-lookup"><span data-stu-id="21762-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="21762-117">在本例中，这将是你编写配置的计算机，而不是目标节点。</span><span class="sxs-lookup"><span data-stu-id="21762-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="21762-118">摘要</span><span class="sxs-lookup"><span data-stu-id="21762-118">Summary</span></span>

<span data-ttu-id="21762-119">总之，可以在配置中使用任何 PowerShell 语言。</span><span class="sxs-lookup"><span data-stu-id="21762-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="21762-120">这包括：</span><span class="sxs-lookup"><span data-stu-id="21762-120">This includes things like:</span></span>

- <span data-ttu-id="21762-121">自定义对象</span><span class="sxs-lookup"><span data-stu-id="21762-121">Custom Objects</span></span>
- <span data-ttu-id="21762-122">哈希表</span><span class="sxs-lookup"><span data-stu-id="21762-122">Hashtables</span></span>
- <span data-ttu-id="21762-123">字符串操作</span><span class="sxs-lookup"><span data-stu-id="21762-123">String manipulation</span></span>
- <span data-ttu-id="21762-124">远程处理</span><span class="sxs-lookup"><span data-stu-id="21762-124">Remoting</span></span>
- <span data-ttu-id="21762-125">WMI 和 CIM</span><span class="sxs-lookup"><span data-stu-id="21762-125">WMI and CIM</span></span>
- <span data-ttu-id="21762-126">ActiveDirectory 对象</span><span class="sxs-lookup"><span data-stu-id="21762-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="21762-127">更多...</span><span class="sxs-lookup"><span data-stu-id="21762-127">and more...</span></span>

<span data-ttu-id="21762-128">在配置中定义的任何 PowerShell 代码都将在编译时计算，但也可以将代码置于包含配置的脚本中。</span><span class="sxs-lookup"><span data-stu-id="21762-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="21762-129">在导入配置时，将执行配置块之外的任何代码。</span><span class="sxs-lookup"><span data-stu-id="21762-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="21762-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21762-130">See also</span></span>

- [<span data-ttu-id="21762-131">向配置添加参数</span><span class="sxs-lookup"><span data-stu-id="21762-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="21762-132">从配置中分离出配置数据</span><span class="sxs-lookup"><span data-stu-id="21762-132">Separate Configuration data from Configurations</span></span>](configData.md)
