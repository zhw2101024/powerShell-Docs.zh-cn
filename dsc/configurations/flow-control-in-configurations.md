---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 配置中的条件语句和循环
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400399"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="53bec-103">配置中的条件语句和循环</span><span class="sxs-lookup"><span data-stu-id="53bec-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="53bec-104">可以让你[配置](configurations.md)更加动态使用 PowerShell 流控制关键字。</span><span class="sxs-lookup"><span data-stu-id="53bec-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="53bec-105">本文将说明如何使用条件语句和循环来使你的配置更加动态化。</span><span class="sxs-lookup"><span data-stu-id="53bec-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="53bec-106">组合条件分支和循环[参数](add-parameters-to-a-configuration.md)并[配置数据](configData.md)允许您更大的灵活性和控制编译你的配置时。</span><span class="sxs-lookup"><span data-stu-id="53bec-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="53bec-107">就像函数或脚本块，可以使用配置内的任何 PowerShell 语言。</span><span class="sxs-lookup"><span data-stu-id="53bec-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="53bec-108">当您调用你的配置来编译".mof"文件时，才会计算您使用的语句。</span><span class="sxs-lookup"><span data-stu-id="53bec-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="53bec-109">下面的示例演示简单的方案来演示概念。</span><span class="sxs-lookup"><span data-stu-id="53bec-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="53bec-110">条件语句都使用了循环更频繁地使用参数和配置数据。</span><span class="sxs-lookup"><span data-stu-id="53bec-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="53bec-111">在此简单示例中，**服务**资源块检索在编译时生成保持其当前状态的".mof"文件服务的当前状态。</span><span class="sxs-lookup"><span data-stu-id="53bec-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="53bec-112">使用动态资源块将抢占 Intellisense 的有效性。</span><span class="sxs-lookup"><span data-stu-id="53bec-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="53bec-113">PowerShell 分析器无法确定指定的值是否可以接受，直到编译配置。</span><span class="sxs-lookup"><span data-stu-id="53bec-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="53bec-114">此外，您可以创建**服务**阻止在当前计算机上的每个服务的资源使用`foreach`循环。</span><span class="sxs-lookup"><span data-stu-id="53bec-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

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

<span data-ttu-id="53bec-115">你也只能创建处于在线状态，通过使用一个简单的机配置`if`语句。</span><span class="sxs-lookup"><span data-stu-id="53bec-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

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
> <span data-ttu-id="53bec-116">动态资源块以上述示例引用在当前计算机。</span><span class="sxs-lookup"><span data-stu-id="53bec-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="53bec-117">在此情况下，将在创作配置的计算机，而不是目标节点。</span><span class="sxs-lookup"><span data-stu-id="53bec-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="53bec-118">摘要</span><span class="sxs-lookup"><span data-stu-id="53bec-118">Summary</span></span>

<span data-ttu-id="53bec-119">总之，您可以使用配置内的任何 PowerShell 语言。</span><span class="sxs-lookup"><span data-stu-id="53bec-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="53bec-120">这包括诸如：</span><span class="sxs-lookup"><span data-stu-id="53bec-120">This includes things like:</span></span>

- <span data-ttu-id="53bec-121">自定义对象</span><span class="sxs-lookup"><span data-stu-id="53bec-121">Custom Objects</span></span>
- <span data-ttu-id="53bec-122">哈希表</span><span class="sxs-lookup"><span data-stu-id="53bec-122">Hashtables</span></span>
- <span data-ttu-id="53bec-123">字符串操作</span><span class="sxs-lookup"><span data-stu-id="53bec-123">String manipulation</span></span>
- <span data-ttu-id="53bec-124">远程处理</span><span class="sxs-lookup"><span data-stu-id="53bec-124">Remoting</span></span>
- <span data-ttu-id="53bec-125">WMI 和 CIM</span><span class="sxs-lookup"><span data-stu-id="53bec-125">WMI and CIM</span></span>
- <span data-ttu-id="53bec-126">与 active Directory 对象</span><span class="sxs-lookup"><span data-stu-id="53bec-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="53bec-127">更多...</span><span class="sxs-lookup"><span data-stu-id="53bec-127">and more...</span></span>

<span data-ttu-id="53bec-128">在配置中定义的任何 PowerShell 代码将计算编译时，但还可以将代码放在脚本中包含你的配置。</span><span class="sxs-lookup"><span data-stu-id="53bec-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="53bec-129">导入你的配置时，将执行在配置块之外的任何代码。</span><span class="sxs-lookup"><span data-stu-id="53bec-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="53bec-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53bec-130">See also</span></span>

- [<span data-ttu-id="53bec-131">向配置添加参数</span><span class="sxs-lookup"><span data-stu-id="53bec-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="53bec-132">从配置中分离出配置数据</span><span class="sxs-lookup"><span data-stu-id="53bec-132">Separate Configuration data from Configurations</span></span>](configData.md)
