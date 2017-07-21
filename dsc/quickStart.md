---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "Desired State Configuration 快速入门"
ms.openlocfilehash: 64c9cea7d65d0723e76c205aea104c3ec9423c1d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
> <span data-ttu-id="68990-103">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="68990-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="desired-state-configuration-quick-start"></a><span data-ttu-id="68990-104">Desired State Configuration 快速入门</span><span class="sxs-lookup"><span data-stu-id="68990-104">Desired State Configuration Quick Start</span></span>

<span data-ttu-id="68990-105">本练习演示创建和应用 Desired State Configuration (DSC) 配置的完整过程。</span><span class="sxs-lookup"><span data-stu-id="68990-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="68990-106">我们使用的示例可确保服务器启用了 `Web-Server`(IIS) 功能，并且该服务器的 `intetpub\wwwroot` 目录中存在一个简单“Hello World”网站的内容。</span><span class="sxs-lookup"><span data-stu-id="68990-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="68990-107">有关什么是 DSC 及其工作原理的概述，请参阅[适用于决策者的 Desired State Configuration 概述](DscForEngineers.md)。</span><span class="sxs-lookup"><span data-stu-id="68990-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](DscForEngineers.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="68990-108">要求</span><span class="sxs-lookup"><span data-stu-id="68990-108">Requirements</span></span>

<span data-ttu-id="68990-109">要运行此示例，需要运行 Windows Server 201 2或更高版本以及 PowerShell 4.0 或更高版本的计算机。</span><span class="sxs-lookup"><span data-stu-id="68990-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="68990-110">编写并放置 index.htm 文件</span><span class="sxs-lookup"><span data-stu-id="68990-110">Write and place the index.htm file</span></span>

<span data-ttu-id="68990-111">首先，创建用作网站内容的 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="68990-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="68990-112">在根文件夹中，创建名为 `test` 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="68990-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="68990-113">在文本编辑器中键入以下文本：</span><span class="sxs-lookup"><span data-stu-id="68990-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="68990-114">在之前创建的 `test` 文件夹中将它另存为 `index.htm`。</span><span class="sxs-lookup"><span data-stu-id="68990-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span> 

## <a name="write-the-configuration"></a><span data-ttu-id="68990-115">写入配置</span><span class="sxs-lookup"><span data-stu-id="68990-115">Write the configuration</span></span>

<span data-ttu-id="68990-116">[DSC 配置](configurations.md)是一个特殊的 PowerShell 功能，可定义用于配置一个或多个目标计算机（节点）的方式。</span><span class="sxs-lookup"><span data-stu-id="68990-116">A [DSC configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="68990-117">在 PowerShell ISE 中键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="68990-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name =  "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
} 
```

<span data-ttu-id="68990-118">将该文件另存为 `WebsiteTest.ps1`。</span><span class="sxs-lookup"><span data-stu-id="68990-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="68990-119">你会发现它类似于 PowerShell 函数，在函数名称之前添加了关键字 **Configuration**。</span><span class="sxs-lookup"><span data-stu-id="68990-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="68990-120">**节点**块指定要配置的目标节点，在本示例中为 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="68990-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="68990-121">此配置调用两个 [resource](resources.md)、[WindowsFeature](windowsFeatureResource.md) 和 [File](fileResource.md)。</span><span class="sxs-lookup"><span data-stu-id="68990-121">The configuration calls two [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) and [File](fileResource.md).</span></span>
<span data-ttu-id="68990-122">资源负责确保目标节点处于由配置定义的状态。</span><span class="sxs-lookup"><span data-stu-id="68990-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="68990-123">编译配置</span><span class="sxs-lookup"><span data-stu-id="68990-123">Compile the configuration</span></span>

<span data-ttu-id="68990-124">对于要应用于节点的 DSC 配置，必须首先将其编译为 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="68990-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="68990-125">为此，你可以如运行功能一样运行配置。</span><span class="sxs-lookup"><span data-stu-id="68990-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="68990-126">在 PowerShell 控制台中，导航到保存配置的同一文件夹，并运行以下命令将配置编译为 MOF 文件：</span><span class="sxs-lookup"><span data-stu-id="68990-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="68990-127">此操作生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="68990-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name                                                                                                                                                       
----                -------------         ------ ----                                                                                                                                                       
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="68990-128">第一行使配置功能在控制台中可用。</span><span class="sxs-lookup"><span data-stu-id="68990-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="68990-129">第二行运行配置。</span><span class="sxs-lookup"><span data-stu-id="68990-129">The second line runs the configuration.</span></span>
<span data-ttu-id="68990-130">结果是创建了一个名为 `WebsiteTest` 的新文件夹作为当前文件夹的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="68990-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="68990-131">`WebsiteTest` 文件夹包含一个名为 `localhost.mof` 的文件。</span><span class="sxs-lookup"><span data-stu-id="68990-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span> <span data-ttu-id="68990-132">然后可将此文件应用于目标节点。</span><span class="sxs-lookup"><span data-stu-id="68990-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="68990-133">应用配置</span><span class="sxs-lookup"><span data-stu-id="68990-133">Apply the configuration</span></span>

<span data-ttu-id="68990-134">现在你已编译好 MOF，可以通过调用 [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet 将配置应用于目标节点（在本例中为本地计算机）。</span><span class="sxs-lookup"><span data-stu-id="68990-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet.</span></span>

<span data-ttu-id="68990-135">`Start-DscConfiguration` cmdlet 通知作为 DSC 引擎的[本地配置管理器 (LCM)](metaConfig.md)应用配置。</span><span class="sxs-lookup"><span data-stu-id="68990-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="68990-136">LCM 的工作是调用 DSC 资源以应用配置。</span><span class="sxs-lookup"><span data-stu-id="68990-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="68990-137">在 PowerShell 控制台中，导航到保存配置的同一文件夹，并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="68990-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="68990-138">测试配置</span><span class="sxs-lookup"><span data-stu-id="68990-138">Test the configuration</span></span>

<span data-ttu-id="68990-139">你可以调用 [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus.md) cmdlet 查看配置是否成功。</span><span class="sxs-lookup"><span data-stu-id="68990-139">You can call the [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus.md) cmdlet to see whether the configuration succeeded.</span></span> 

<span data-ttu-id="68990-140">此外，还可以直接测试结果，在本例中可通过浏览 Web 浏览器中的 `http://localhost/` 进行测试。</span><span class="sxs-lookup"><span data-stu-id="68990-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span> <span data-ttu-id="68990-141">你将看到在本示例的第一步中所创建的“Hello World”HTML 页面。</span><span class="sxs-lookup"><span data-stu-id="68990-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="68990-142">后续步骤</span><span class="sxs-lookup"><span data-stu-id="68990-142">Next steps</span></span>

- <span data-ttu-id="68990-143">在 [DSC 配置](configurations.md)中了解有关 DSC 配置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="68990-143">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="68990-144">查看哪些 DSC 资源可用，以及如何在 [DSC 资源](resources.md)中创建自定义 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="68990-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](resources.md).</span></span>
- <span data-ttu-id="68990-145">在 [PowerShell 库](https://www.powershellgallery.com/)中查找 DSC 配置和资源。</span><span class="sxs-lookup"><span data-stu-id="68990-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>



