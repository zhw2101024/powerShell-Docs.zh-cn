---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC 配置"
ms.openlocfilehash: 2c2f8183ef586ff9371e4af7ea83db3e04fa68a4
ms.sourcegitcommit: 378c7ed4e8c8c1c5fe71417b9ba672a4c990630b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2018
---
# <a name="dsc-configurations"></a><span data-ttu-id="f66b0-103">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="f66b0-103">DSC Configurations</span></span>

><span data-ttu-id="f66b0-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f66b0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f66b0-105">DSC 配置是定义某一特殊类型函数的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="f66b0-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="f66b0-106">若要定义配置，你可使用 PowerShell 关键字 **Configuration**。</span><span class="sxs-lookup"><span data-stu-id="f66b0-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="f66b0-107">将脚本保存为 .ps1 文件。</span><span class="sxs-lookup"><span data-stu-id="f66b0-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="f66b0-108">配置语法</span><span class="sxs-lookup"><span data-stu-id="f66b0-108">Configuration syntax</span></span>

<span data-ttu-id="f66b0-109">配置脚本由以下部分组成：</span><span class="sxs-lookup"><span data-stu-id="f66b0-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="f66b0-110">**配置**块。</span><span class="sxs-lookup"><span data-stu-id="f66b0-110">The **Configuration** block.</span></span> <span data-ttu-id="f66b0-111">这是最外层的脚本块。</span><span class="sxs-lookup"><span data-stu-id="f66b0-111">This is the outermost script block.</span></span> <span data-ttu-id="f66b0-112">你可通过使用 **Configuration** 关键字并提供配置名进行定义。</span><span class="sxs-lookup"><span data-stu-id="f66b0-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="f66b0-113">在这种情况下，该配置名为“MyDscConfiguration”。</span><span class="sxs-lookup"><span data-stu-id="f66b0-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="f66b0-114">一个或多个**节点**块。</span><span class="sxs-lookup"><span data-stu-id="f66b0-114">One or more **Node** blocks.</span></span> <span data-ttu-id="f66b0-115">这些将定义正在配置的节点（计算机或 VM）。</span><span class="sxs-lookup"><span data-stu-id="f66b0-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="f66b0-116">在以上配置中，有一个以计算机为目标的名为“TEST-PC1”的**节点**块。</span><span class="sxs-lookup"><span data-stu-id="f66b0-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="f66b0-117">一个或多个资源块。</span><span class="sxs-lookup"><span data-stu-id="f66b0-117">One or more resource blocks.</span></span> <span data-ttu-id="f66b0-118">这是此配置为其正在配置的资源设置属性的位置。</span><span class="sxs-lookup"><span data-stu-id="f66b0-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="f66b0-119">在这种情况下，有两个资源块，每个资源块都调用“WindowsFeature”资源。</span><span class="sxs-lookup"><span data-stu-id="f66b0-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="f66b0-120">在**配置**块中，可执行在 PowerShell 函数中通常可执行的任何操作。</span><span class="sxs-lookup"><span data-stu-id="f66b0-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="f66b0-121">例如，在上一示例中，如果不想在配置中对目标计算机名进行硬编码，则可以为节点名添加参数：</span><span class="sxs-lookup"><span data-stu-id="f66b0-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName <MyComputer>

```

<span data-ttu-id="f66b0-122">在此示例中，指定节点名称，具体方法为在编译配置时以 ComputerName 参数的形式传递节点名称。</span><span class="sxs-lookup"><span data-stu-id="f66b0-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="f66b0-123">该名称默认为“localhost”。</span><span class="sxs-lookup"><span data-stu-id="f66b0-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="f66b0-124">正在编译配置</span><span class="sxs-lookup"><span data-stu-id="f66b0-124">Compiling the configuration</span></span>

<span data-ttu-id="f66b0-125">必须将其编译为 MOF 文档才能执行配置。</span><span class="sxs-lookup"><span data-stu-id="f66b0-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="f66b0-126">你可通过调用配置（像调用 PowerShell 函数一样）以执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f66b0-126">You do this by calling the configuration like you would a PowerShell function.</span></span>  
<span data-ttu-id="f66b0-127">此示例的最后一行仅包含配置名称，用于调用配置。</span><span class="sxs-lookup"><span data-stu-id="f66b0-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="f66b0-128">**注意：**若要调用配置，该函数必须在全局范围内（与任何其他 PowerShell 函数一样）。</span><span class="sxs-lookup"><span data-stu-id="f66b0-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> 
><span data-ttu-id="f66b0-129">可通过以下方式来实现此操作：对脚本执行“dot-source”操作，或者使用 F5 或单击 ISE 中的“运行脚本”按钮以运行配置脚本。</span><span class="sxs-lookup"><span data-stu-id="f66b0-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> 
><span data-ttu-id="f66b0-130">若要对脚本执行“dot-source”操作，请运行命令 `. .\myConfig.ps1`，其中 `myConfig.ps1` 是包含配置的脚本文件的名称。</span><span class="sxs-lookup"><span data-stu-id="f66b0-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="f66b0-131">调用配置时，它会：</span><span class="sxs-lookup"><span data-stu-id="f66b0-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="f66b0-132">解析所有变量</span><span class="sxs-lookup"><span data-stu-id="f66b0-132">Resolves all variables</span></span> 
- <span data-ttu-id="f66b0-133">在当前目录中使用与配置相同的名称创建文件夹。</span><span class="sxs-lookup"><span data-stu-id="f66b0-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="f66b0-134">在新目录中创建名为 _NodeName_.mof 的文件，其中 _NodeName_ 为配置的目标节点名称。</span><span class="sxs-lookup"><span data-stu-id="f66b0-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> 
    <span data-ttu-id="f66b0-135">如果有多个节点，则将为每个节点创建 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="f66b0-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="f66b0-136">**请注意**：此 MOF 文件包含目标节点的所有配置信息。</span><span class="sxs-lookup"><span data-stu-id="f66b0-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="f66b0-137">因此，务必确保其安全性。</span><span class="sxs-lookup"><span data-stu-id="f66b0-137">Because of this, it’s important to keep it secure.</span></span> 
><span data-ttu-id="f66b0-138">有关详细信息，请参阅[保护 MOF 文件](secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="f66b0-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="f66b0-139">编译上述第一个配置会形成以下文件夹结构：</span><span class="sxs-lookup"><span data-stu-id="f66b0-139">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```  

<span data-ttu-id="f66b0-140">如果配置采用了参数（如示例 2 所述），则需在编译时提供该参数。</span><span class="sxs-lookup"><span data-stu-id="f66b0-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="f66b0-141">其形式如下：</span><span class="sxs-lookup"><span data-stu-id="f66b0-141">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## <a name="using-dependson"></a><span data-ttu-id="f66b0-142">使用 DependsOn</span><span class="sxs-lookup"><span data-stu-id="f66b0-142">Using DependsOn</span></span>

<span data-ttu-id="f66b0-143">有效的 DSC 关键字为 **DependsOn**。</span><span class="sxs-lookup"><span data-stu-id="f66b0-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="f66b0-144">通常（但不一定总是），DSC 将按资源在配置中显示的顺序来应用这些资源。</span><span class="sxs-lookup"><span data-stu-id="f66b0-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span> <span data-ttu-id="f66b0-145">但是，由 **DependsOn** 指定哪些资源依赖于其他资源，而 LCM 则确保这些资源的应用顺序正确（无论资源实例是以何种顺序定义的）。</span><span class="sxs-lookup"><span data-stu-id="f66b0-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span> <span data-ttu-id="f66b0-146">例如，配置可能会指定**用户**资源实例依赖于**组**实例的存在：</span><span class="sxs-lookup"><span data-stu-id="f66b0-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="f66b0-147">在配置中使用新的资源</span><span class="sxs-lookup"><span data-stu-id="f66b0-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="f66b0-148">如果运行了前面的示例，你可能注意到你已收到警告信息，提示你正在使用未显式导入的资源。</span><span class="sxs-lookup"><span data-stu-id="f66b0-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="f66b0-149">现在，DSC 附带 12 种资源作为 PSDesiredStateConfiguration 模块的一部分。</span><span class="sxs-lookup"><span data-stu-id="f66b0-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span> <span data-ttu-id="f66b0-150">外部模块中的其他资源须置于 `$env:PSModulePath` 中以便 LCM 能够识别。</span><span class="sxs-lookup"><span data-stu-id="f66b0-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span> <span data-ttu-id="f66b0-151">新的 cmdlet - [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)，可用来确定哪些资源已安装在系统上并且可供 LCM 使用。</span><span class="sxs-lookup"><span data-stu-id="f66b0-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span> <span data-ttu-id="f66b0-152">一旦这些模块已置于 `$env:PSModulePath` 中并由 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 正确识别，你仍需在配置中加载它们。</span><span class="sxs-lookup"><span data-stu-id="f66b0-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span> 
<span data-ttu-id="f66b0-153">**Import-DscResource** 是仅可在**配置**块中识别的动态关键字（即它不是 cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="f66b0-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span> 
<span data-ttu-id="f66b0-154">**Import-DscResource** 支持两种参数：</span><span class="sxs-lookup"><span data-stu-id="f66b0-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="f66b0-155">**ModuleName** 是使用 **Import-DscResource** 的推荐方法。</span><span class="sxs-lookup"><span data-stu-id="f66b0-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="f66b0-156">它接受包含要导入资源的模块名称以及模块名称的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="f66b0-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span> 
- <span data-ttu-id="f66b0-157">**Name** 是要导入资源的名称。</span><span class="sxs-lookup"><span data-stu-id="f66b0-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="f66b0-158">这不是由 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 返回为“Name”的友好名称，而是定义资源架构时使用的类名（由 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 返回为 **ResourceType**）。</span><span class="sxs-lookup"><span data-stu-id="f66b0-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span></span> 

## <a name="see-also"></a><span data-ttu-id="f66b0-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f66b0-159">See Also</span></span>
* [<span data-ttu-id="f66b0-160">Windows PowerShell Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="f66b0-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="f66b0-161">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="f66b0-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="f66b0-162">配置本地配置管理器</span><span class="sxs-lookup"><span data-stu-id="f66b0-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

