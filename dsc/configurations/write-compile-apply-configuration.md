---
ms.date: 12/12/2018
keywords: dsc，powershell、 配置、 服务、 安装程序
title: 编写、编译和应用配置
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400407"
---
> <span data-ttu-id="cd8e7-103">适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cd8e7-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="cd8e7-104">编写、编译和应用配置</span><span class="sxs-lookup"><span data-stu-id="cd8e7-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="cd8e7-105">本练习演示创建和应用 Desired State Configuration (DSC) 配置的完整过程。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="cd8e7-106">在以下示例中，您将学习如何编写和应用非常简单的配置。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="cd8e7-107">配置将确保在本地计算机上存在的"HelloWorld.txt"文件。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="cd8e7-108">如果您删除该文件，DSC 将重新创建它的下一步的时间，它会更新。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="cd8e7-109">什么是 DSC 及其工作原理的概述，请参阅[面向开发人员 Desired State Configuration 概述](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="cd8e7-110">要求</span><span class="sxs-lookup"><span data-stu-id="cd8e7-110">Requirements</span></span>

<span data-ttu-id="cd8e7-111">若要运行此示例中，将需要运行 PowerShell 4.0 或更高版本的计算机。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="cd8e7-112">写入配置</span><span class="sxs-lookup"><span data-stu-id="cd8e7-112">Write the configuration</span></span>

<span data-ttu-id="cd8e7-113">DSC [配置](configurations.md)是一个特殊的 PowerShell 功能，可定义用于配置一个或多个目标计算机（节点）的方式。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="cd8e7-114">在 PowerShell ISE 中或其他 PowerShell 编辑器中，键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="cd8e7-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="cd8e7-115">将文件另存"HelloWorld.ps1"。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="cd8e7-116">定义配置就像定义函数。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="cd8e7-117">**节点**块指定要配置的目标节点，在本示例中为 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="cd8e7-118">配置调用其中一个[资源](../resources/resources.md)，则`File`资源。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="cd8e7-119">资源负责确保目标节点处于由配置定义的状态。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="cd8e7-120">编译配置</span><span class="sxs-lookup"><span data-stu-id="cd8e7-120">Compile the configuration</span></span>

<span data-ttu-id="cd8e7-121">对于要应用于节点的 DSC 配置，必须首先将其编译为 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="cd8e7-122">运行配置，如某个函数，将编译一个".mof"文件对于定义的每个节点`Node`块。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="cd8e7-123">若要运行此配置，需要对*点获取来源*到当前作用域"HelloWorld.ps1"脚本。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="cd8e7-124">有关详细信息，请参阅[about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="cd8e7-125">*使用点获取来源*通过在你在其中存储它之后, 的路径中键入"HelloWorld.ps1"脚本`. `（点、 空间）。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="cd8e7-126">然后，可以通过调用类似于函数运行您的配置。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-126">You may then, run your configuration by calling it like a Function.</span></span>

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="cd8e7-127">此操作生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="cd8e7-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="cd8e7-128">应用配置</span><span class="sxs-lookup"><span data-stu-id="cd8e7-128">Apply the configuration</span></span>

<span data-ttu-id="cd8e7-129">现在你已编译好 MOF，可以通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将配置应用于目标节点（在本例中为本地计算机）。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="cd8e7-130">`Start-DscConfiguration` Cmdlet 会告诉[本地配置管理器 (LCM)](../managing-nodes/metaConfig.md)，DSC，以应用配置的引擎。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="cd8e7-131">LCM 的工作是调用 DSC 资源以应用配置。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="cd8e7-132">使用下面的代码来执行`Start-DSCConfiguration`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="cd8e7-133">指定的目录路径为存储在"localhost.mof"`-Path`参数。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="cd8e7-134">`Start-DSCConfiguration` Cmdlet 的任何指定的目录中查找"\<computername\>.mof"文件。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="cd8e7-135">`Start-DSCConfiguration` Cmdlet 尝试将会在每个".mof"文件应用于指定的文件名 （"localhost"、"server01"、"dc-02"等） 的计算机名。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="cd8e7-136">如果`-Wait`未指定参数，`Start-DSCConfiguration`创建后台作业来执行该操作。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="cd8e7-137">指定`-Verbose`参数，可观看**Verbose**操作的输出。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="cd8e7-138">`-Wait`和`-Verbose`是这两个可选参数。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="cd8e7-139">测试配置</span><span class="sxs-lookup"><span data-stu-id="cd8e7-139">Test the configuration</span></span>

<span data-ttu-id="cd8e7-140">一次`Start-DSCConfiguration`cmdlet 完成后，你应看到一个"HelloWorld.txt"文件中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="cd8e7-141">你可以验证包含内容[Get-content](/powershell/module/microsoft.powershell.management/get-content) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="cd8e7-142">此外可以*测试*使用当前状态[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="cd8e7-143">如果节点是当前符合应用的配置，输出应为"True"。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="cd8e7-144">重新应用配置</span><span class="sxs-lookup"><span data-stu-id="cd8e7-144">Re-applying the configuration</span></span>

<span data-ttu-id="cd8e7-145">若要查看您再次获取应用的配置，可以删除您的配置创建的文本文件。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="cd8e7-146">使用`Start-DSCConfiguration`cmdlet 与`-UseExisting`参数。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="cd8e7-147">`-UseExisting`参数指示`Start-DSCConfiguration`重新应用"current.mof"文件，它表示最新成功应用配置。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="cd8e7-148">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cd8e7-148">Next steps</span></span>

- <span data-ttu-id="cd8e7-149">在 [DSC 配置](configurations.md)中了解有关 DSC 配置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="cd8e7-150">查看哪些 DSC 资源可用，以及如何在 [DSC 资源](../resources/resources.md)中创建自定义 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="cd8e7-151">在 [PowerShell 库](https://www.powershellgallery.com/)中查找 DSC 配置和资源。</span><span class="sxs-lookup"><span data-stu-id="cd8e7-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
