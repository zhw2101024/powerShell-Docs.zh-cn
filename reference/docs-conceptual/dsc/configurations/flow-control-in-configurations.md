---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 配置中的条件语句和循环
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736890"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="e3114-103">配置中的条件语句和循环</span><span class="sxs-lookup"><span data-stu-id="e3114-103">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="e3114-104">可以使用 PowerShell 流控制关键字使[配置](configurations.md)更加动态。</span><span class="sxs-lookup"><span data-stu-id="e3114-104">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="e3114-105">本文介绍了如何使用条件语句和循环来使 `Configuration` 更加动态。</span><span class="sxs-lookup"><span data-stu-id="e3114-105">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="e3114-106">将条件语句和循环与[参数](add-parameters-to-a-configuration.md)和[配置数据](configData.md)结合使用，用户可以在编译 `Configuration` 时更灵活地进行控制。</span><span class="sxs-lookup"><span data-stu-id="e3114-106">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="e3114-107">就像函数或脚本块一样，可以在 `Configuration` 中使用任何 PowerShell 语言。</span><span class="sxs-lookup"><span data-stu-id="e3114-107">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span>
<span data-ttu-id="e3114-108">只有在调用 `Configuration` 来编译“`.mof`”文件时才会计算使用的语句。</span><span class="sxs-lookup"><span data-stu-id="e3114-108">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="e3114-109">下面的示例展示了一些场景来演示概念。</span><span class="sxs-lookup"><span data-stu-id="e3114-109">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="e3114-110">条件语句和循环通常与参数和配置数据一起使用。</span><span class="sxs-lookup"><span data-stu-id="e3114-110">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="e3114-111">在这个简单示例中，Service  资源块在编译时检索服务的当前状态，以生成维护其当前状态的“`.mof`”文件。</span><span class="sxs-lookup"><span data-stu-id="e3114-111">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="e3114-112">使用动态资源块将抢占 Intellisense 的效率。</span><span class="sxs-lookup"><span data-stu-id="e3114-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="e3114-113">在编译 `Configuration` 之前，PowerShell 解析器无法确定指定的值是否可接受。</span><span class="sxs-lookup"><span data-stu-id="e3114-113">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

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

<span data-ttu-id="e3114-114">此外，可以使用 `foreach` 循环为当前计算机上的每个服务创建一个 Service  资源块。</span><span class="sxs-lookup"><span data-stu-id="e3114-114">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
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

<span data-ttu-id="e3114-115">你还可以通过使用 `if` 语句，仅为联机的计算机创建 `Configuration`。</span><span class="sxs-lookup"><span data-stu-id="e3114-115">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="e3114-116">上述示例中的动态资源块引用当前计算机。</span><span class="sxs-lookup"><span data-stu-id="e3114-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="e3114-117">在本例中，这将是你编写 `Configuration` 的计算机，而不是目标节点。</span><span class="sxs-lookup"><span data-stu-id="e3114-117">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="e3114-118">总结</span><span class="sxs-lookup"><span data-stu-id="e3114-118">Summary</span></span>

<span data-ttu-id="e3114-119">总之，可以在 `Configuration` 中使用任何 PowerShell 语言功能。</span><span class="sxs-lookup"><span data-stu-id="e3114-119">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="e3114-120">这包括：</span><span class="sxs-lookup"><span data-stu-id="e3114-120">This includes things like:</span></span>

- <span data-ttu-id="e3114-121">自定义对象</span><span class="sxs-lookup"><span data-stu-id="e3114-121">Custom Objects</span></span>
- <span data-ttu-id="e3114-122">哈希表</span><span class="sxs-lookup"><span data-stu-id="e3114-122">Hashtables</span></span>
- <span data-ttu-id="e3114-123">字符串操作</span><span class="sxs-lookup"><span data-stu-id="e3114-123">String manipulation</span></span>
- <span data-ttu-id="e3114-124">远程处理</span><span class="sxs-lookup"><span data-stu-id="e3114-124">Remoting</span></span>
- <span data-ttu-id="e3114-125">WMI 和 CIM</span><span class="sxs-lookup"><span data-stu-id="e3114-125">WMI and CIM</span></span>
- <span data-ttu-id="e3114-126">ActiveDirectory 对象</span><span class="sxs-lookup"><span data-stu-id="e3114-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="e3114-127">更多...</span><span class="sxs-lookup"><span data-stu-id="e3114-127">and more...</span></span>

<span data-ttu-id="e3114-128">在 `Configuration` 中定义的任何 PowerShell 代码都将在编译时计算，但也可以将代码置于包含 `Configuration` 的脚本中。</span><span class="sxs-lookup"><span data-stu-id="e3114-128">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="e3114-129">导入 `Configuration` 时，将执行 `Configuration` 块之外的任何代码。</span><span class="sxs-lookup"><span data-stu-id="e3114-129">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3114-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3114-130">See also</span></span>

- [<span data-ttu-id="e3114-131">向配置添加参数</span><span class="sxs-lookup"><span data-stu-id="e3114-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="e3114-132">从配置中分离出配置数据</span><span class="sxs-lookup"><span data-stu-id="e3114-132">Separate Configuration data from Configurations</span></span>](configData.md)
