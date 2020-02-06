---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,服务,设置
title: 编写、编译和应用配置
ms.openlocfilehash: eb61e518762b9f13e617ecd4711bfef7a86814ec
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818152"
---
> <span data-ttu-id="726ec-103">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="726ec-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="726ec-104">编写、编译和应用配置</span><span class="sxs-lookup"><span data-stu-id="726ec-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="726ec-105">本练习演示创建和应用 Desired State Configuration (DSC) 配置的完整过程。</span><span class="sxs-lookup"><span data-stu-id="726ec-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="726ec-106">在以下示例中，你将学习如何编写和应用一个非常简单的配置。</span><span class="sxs-lookup"><span data-stu-id="726ec-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="726ec-107">该配置会确保本地计算机上存在“HelloWorld.txt”文件。</span><span class="sxs-lookup"><span data-stu-id="726ec-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="726ec-108">如果删除该文件，则 DSC 会在下次更新时重新创建它。</span><span class="sxs-lookup"><span data-stu-id="726ec-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="726ec-109">有关什么是 DSC 及其工作原理的概述，请参阅[面向开发人员的 Desired State Configuration 概述](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="726ec-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="726ec-110">要求</span><span class="sxs-lookup"><span data-stu-id="726ec-110">Requirements</span></span>

<span data-ttu-id="726ec-111">要运行此示例，需要运行 PowerShell 4.0 或更高版本的计算机。</span><span class="sxs-lookup"><span data-stu-id="726ec-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="726ec-112">写入配置</span><span class="sxs-lookup"><span data-stu-id="726ec-112">Write the configuration</span></span>

<span data-ttu-id="726ec-113">DSC [配置](configurations.md)是一个特殊的 PowerShell 功能，可定义用于配置一个或多个目标计算机（节点）的方式。</span><span class="sxs-lookup"><span data-stu-id="726ec-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="726ec-114">在 PowerShell ISE 或其他 PowerShell 编辑器中，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="726ec-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

> <span data-ttu-id="726ec-115">重要提示！在需要导入多个模块以便在同一配置中使用多个 DSC 资源的更高级方案中，请务必使用 `Import-DscResource` 让每个模块单独占一行。</span><span class="sxs-lookup"><span data-stu-id="726ec-115">!Important In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a separate line using `Import-DscResource`.</span></span>
> <span data-ttu-id="726ec-116">这样一来，在源代码管理中更易于维护，这也是在 Azure 状态配置中使用 DSC 时所必需的操作。</span><span class="sxs-lookup"><span data-stu-id="726ec-116">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="726ec-117">将文件保存为“HelloWorld.ps1”。</span><span class="sxs-lookup"><span data-stu-id="726ec-117">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="726ec-118">定义配置类似于定义函数。</span><span class="sxs-lookup"><span data-stu-id="726ec-118">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="726ec-119">**节点**块指定要配置的目标节点，在本示例中为 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="726ec-119">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="726ec-120">配置会调用一个[资源](../resources/resources.md)（`File` 资源）。</span><span class="sxs-lookup"><span data-stu-id="726ec-120">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="726ec-121">资源负责确保目标节点处于由配置定义的状态。</span><span class="sxs-lookup"><span data-stu-id="726ec-121">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="726ec-122">编译配置</span><span class="sxs-lookup"><span data-stu-id="726ec-122">Compile the configuration</span></span>

<span data-ttu-id="726ec-123">对于要应用于节点的 DSC 配置，必须首先将其编译为 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="726ec-123">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="726ec-124">与函数类似，运行配置会为 `Node` 块定义的每个节点编译一个“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="726ec-124">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="726ec-125">若要运行配置，需要使用点  将“HelloWorld.ps1”脚本的来源获取到当前范围中。</span><span class="sxs-lookup"><span data-stu-id="726ec-125">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="726ec-126">有关详细信息，请参阅 [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)。</span><span class="sxs-lookup"><span data-stu-id="726ec-126">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="726ec-127"> 通过在 `. `（点，空格）后键入用于存储“HelloWorld.ps1”脚本的路径，来使用点获取其来源。</span><span class="sxs-lookup"><span data-stu-id="726ec-127">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="726ec-128">随后可以通过调用配置（类似于函数）来运行它。</span><span class="sxs-lookup"><span data-stu-id="726ec-128">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="726ec-129">此操作生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="726ec-129">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="726ec-130">应用配置</span><span class="sxs-lookup"><span data-stu-id="726ec-130">Apply the configuration</span></span>

<span data-ttu-id="726ec-131">现在你已编译好 MOF，可以通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将配置应用于目标节点（在本例中为本地计算机）。</span><span class="sxs-lookup"><span data-stu-id="726ec-131">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="726ec-132">`Start-DscConfiguration` cmdlet 通知作为 DSC 引擎的[本地配置管理器 (LCM)](../managing-nodes/metaConfig.md) 应用配置。</span><span class="sxs-lookup"><span data-stu-id="726ec-132">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="726ec-133">LCM 的工作是调用 DSC 资源以应用配置。</span><span class="sxs-lookup"><span data-stu-id="726ec-133">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="726ec-134">使用下面的代码执行 `Start-DSCConfiguration` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="726ec-134">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="726ec-135">向 `-Path` 参数指定用于存储“localhost.mof”的目录路径。</span><span class="sxs-lookup"><span data-stu-id="726ec-135">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="726ec-136">`Start-DSCConfiguration` Cmdlet 在指定的目录中查找任何“\<computername\>.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="726ec-136">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="726ec-137">`Start-DSCConfiguration` Cmdlet 尝试将找到的每个“.mof”文件应用于通过文件名指定的计算机名（“localhost”、“server01”、“dc-02”等）。</span><span class="sxs-lookup"><span data-stu-id="726ec-137">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="726ec-138">如果未指定 `-Wait` 参数，则 `Start-DSCConfiguration` 会创建后台作业来执行操作。</span><span class="sxs-lookup"><span data-stu-id="726ec-138">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="726ec-139">通过指定 `-Verbose` 参数可以观察操作的详细  输出。</span><span class="sxs-lookup"><span data-stu-id="726ec-139">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="726ec-140">`-Wait` 和 `-Verbose` 是可选参数。</span><span class="sxs-lookup"><span data-stu-id="726ec-140">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="726ec-141">测试配置</span><span class="sxs-lookup"><span data-stu-id="726ec-141">Test the configuration</span></span>

<span data-ttu-id="726ec-142">`Start-DSCConfiguration` cmdlet 完成后，便应在指定的位置看到“HelloWorld.txt”文件。</span><span class="sxs-lookup"><span data-stu-id="726ec-142">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="726ec-143">可以使用 [Get-content](/powershell/module/microsoft.powershell.management/get-content) cmdlet 验证内容。</span><span class="sxs-lookup"><span data-stu-id="726ec-143">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="726ec-144">还可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 测试  当前状态。</span><span class="sxs-lookup"><span data-stu-id="726ec-144">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="726ec-145">如果节点当前符合所应用的配置，则输出应为“True”。</span><span class="sxs-lookup"><span data-stu-id="726ec-145">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="726ec-146">重新应用配置</span><span class="sxs-lookup"><span data-stu-id="726ec-146">Re-applying the configuration</span></span>

<span data-ttu-id="726ec-147">若要再次应用配置，可以删除配置所创建的文本文件。</span><span class="sxs-lookup"><span data-stu-id="726ec-147">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="726ec-148">将 `Start-DSCConfiguration` cmdlet 与 `-UseExisting` 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="726ec-148">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="726ec-149">`-UseExisting` 参数指示 `Start-DSCConfiguration` 重新应用“current.mof”文件，它表示最近成功应用的配置。</span><span class="sxs-lookup"><span data-stu-id="726ec-149">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="726ec-150">后续步骤</span><span class="sxs-lookup"><span data-stu-id="726ec-150">Next steps</span></span>

- <span data-ttu-id="726ec-151">在 [DSC 配置](configurations.md)中了解有关 DSC 配置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="726ec-151">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="726ec-152">查看哪些 DSC 资源可用，以及如何在 [DSC 资源](../resources/resources.md)中创建自定义 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="726ec-152">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="726ec-153">在 [PowerShell 库](https://www.powershellgallery.com/)中查找 DSC 配置和资源。</span><span class="sxs-lookup"><span data-stu-id="726ec-153">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
