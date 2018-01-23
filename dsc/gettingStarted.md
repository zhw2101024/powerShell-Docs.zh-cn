---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "PowerShell Desired State Configuration 入门"
ms.openlocfilehash: 856528f1e52eafa8b2c93b825a60376a0d64cab2
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="dc7f9-103">PowerShell Desired State Configuration 入门</span><span class="sxs-lookup"><span data-stu-id="dc7f9-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="dc7f9-104">本指南介绍了如何开始创建 PowerShell Desired State Configuration文档并将其应用到计算机中。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="dc7f9-105">假定你基本熟悉 PowerShell cmdlet、模块和函数。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span> 


## <a name="create-a-configuration"></a><span data-ttu-id="dc7f9-106">创建配置</span><span class="sxs-lookup"><span data-stu-id="dc7f9-106">Create a Configuration</span></span> ##

<span data-ttu-id="dc7f9-107">[**配置**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)是描述环境的文档。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-107">[**Configurations**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="dc7f9-108">环境中包含“**节点**”（通常是虚拟机或物理计算机）。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span> 

<span data-ttu-id="dc7f9-109">配置会以各种形式出现。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="dc7f9-110">创建新配置最简单方法就是创建 .ps1（PowerShell 脚本）文件。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="dc7f9-111">若要执行此操作，请打开首选编辑器。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="dc7f9-112">PowerShell ISE 是一个不错的选择，因为它本身了解 DSC。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="dc7f9-113">将以下内容另存为 PS1：</span><span class="sxs-lookup"><span data-stu-id="dc7f9-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="dc7f9-114">Configuration 部分</span><span class="sxs-lookup"><span data-stu-id="dc7f9-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="dc7f9-115">**Configuration** 是已添加到 PowerShell 4.0 的关键字。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="dc7f9-116">它表示一种由 Desired State Configuration.使用的特殊 PowerShell 函数。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="dc7f9-117">在此示例中，该函数被命名为 myFirstConfiguration。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-117">In this example, the function is named myFirstConfiguration.</span></span> 

<span data-ttu-id="dc7f9-118">下一行是类似于导入模块的导入语句。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="dc7f9-119">稍后将对其展开讨论。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-119">It will be discussed later on.</span></span>

<span data-ttu-id="dc7f9-120">“节点”定义此配置将对其进行操作的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="dc7f9-121">尽管此配置是本地编辑的，但是这些配置可访问并配置远程节点。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span> 

<span data-ttu-id="dc7f9-122">节点可以是计算机名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="dc7f9-123">单个配置文档中可有多个节点。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="dc7f9-124">使用[配置数据](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)，你也可将相同的配置应用到多个节点。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-124">Using [configuration data](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="dc7f9-125">在这种情况下，该节点是“localhost” - 表示本地计算机。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-125">In this case, the node is "localhost" - which means the local computer.</span></span> 

<span data-ttu-id="dc7f9-126">下一项是[**资源**](https://msdn.microsoft.com/en-us/powershell/dsc/resources)。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-126">The next item is a [**resource**](https://msdn.microsoft.com/en-us/powershell/dsc/resources).</span></span> <span data-ttu-id="dc7f9-127">资源是配置的构建基块。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="dc7f9-128">每个资源都是定义计算机单方面实现逻辑的模块。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="dc7f9-129">可通过在 PowerShell 中运行 **Get-DscResource** 查看计算机上的每个资源。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="dc7f9-130">资源必须存在于本地计算机中并通过 **Import-DscResource**（位于此配置的第二行）导入后，才可在配置中使用它们。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span> 

<span data-ttu-id="dc7f9-131">**执行配置**</span><span class="sxs-lookup"><span data-stu-id="dc7f9-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="dc7f9-132">如果以上脚本已保存并运行，则不会产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="dc7f9-133">这是因为配置只是一个函数，并且上述脚本已定义但尚未运行该函数。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="dc7f9-134">将函数定义后，必须调用它：</span><span class="sxs-lookup"><span data-stu-id="dc7f9-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="dc7f9-135">执行时，配置函数验证配置是否有效。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="dc7f9-136">不应有语法错误，资源需定义所有强制参数，同时在执行前应导入所有资源。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="dc7f9-137">一旦执行配置，它将使用含 **.MOF 文件** 的配置的名称为配置中的每个节点创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="dc7f9-138">.MOF 文件是一种基于标准的管理格式，PowerShell DSC 用其在网络上进行通信。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="dc7f9-139">执行配置：</span><span class="sxs-lookup"><span data-stu-id="dc7f9-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="dc7f9-140">这将创建可访问配置中节点的 PowerShell 作业，并对其进行配置。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="dc7f9-141">若要查看作业输出，请使用 -Wait。</span><span class="sxs-lookup"><span data-stu-id="dc7f9-141">To see the output of the job, use -Wait.</span></span> 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```

