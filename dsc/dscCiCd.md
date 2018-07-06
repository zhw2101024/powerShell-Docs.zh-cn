---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用 DSC 生成持续集成和连续部署管道
ms.openlocfilehash: faeef5022cbd984cab0620b69db19de8b84cca0e
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940338"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="431f8-103">使用 DSC 生成持续集成和连续部署管道</span><span class="sxs-lookup"><span data-stu-id="431f8-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="431f8-104">此示例展示了如何使用 PowerShell、DSC、Pester 和 Visual Studio Team Foundation Server (TFS) 生成持续集成/连续部署 (CI/CD) 管道。</span><span class="sxs-lookup"><span data-stu-id="431f8-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="431f8-105">生成和配置管道后，可以用它来完全部署、配置和测试 DNS 服务器及关联的主机记录。</span><span class="sxs-lookup"><span data-stu-id="431f8-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="431f8-106">此过程模拟了将用于开发环境的管道第一部分。</span><span class="sxs-lookup"><span data-stu-id="431f8-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="431f8-107">自动 CI/CD 管道有助于更快、更可靠地更新软件，确保所有代码都经过测试，并确保最新版代码始终可用。</span><span class="sxs-lookup"><span data-stu-id="431f8-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="431f8-108">必备条件</span><span class="sxs-lookup"><span data-stu-id="431f8-108">Prerequisites</span></span>

<span data-ttu-id="431f8-109">若要使用此示例，应熟悉以下内容：</span><span class="sxs-lookup"><span data-stu-id="431f8-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="431f8-110">CI-CD 概念。</span><span class="sxs-lookup"><span data-stu-id="431f8-110">CI-CD concepts.</span></span> <span data-ttu-id="431f8-111">[发布管道模型](http://aka.ms/thereleasepipelinemodelpdf)提供了很好的参考资源。</span><span class="sxs-lookup"><span data-stu-id="431f8-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="431f8-112">[Git](https://git-scm.com/) 源控件</span><span class="sxs-lookup"><span data-stu-id="431f8-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="431f8-113">[Pester](https://github.com/pester/Pester) 测试框架</span><span class="sxs-lookup"><span data-stu-id="431f8-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="431f8-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="431f8-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="431f8-115">将需要</span><span class="sxs-lookup"><span data-stu-id="431f8-115">What you will need</span></span>

<span data-ttu-id="431f8-116">若要生成并运行此示例，需要一个包含多台计算机和/或虚拟机的环境。</span><span class="sxs-lookup"><span data-stu-id="431f8-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="431f8-117">客户端</span><span class="sxs-lookup"><span data-stu-id="431f8-117">Client</span></span>

<span data-ttu-id="431f8-118">将在这台计算机上执行生成和运行此示例所需的全部工作。</span><span class="sxs-lookup"><span data-stu-id="431f8-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="431f8-119">客户端计算机必须是安装以下项的 Windows 计算机：</span><span class="sxs-lookup"><span data-stu-id="431f8-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="431f8-120">Git</span><span class="sxs-lookup"><span data-stu-id="431f8-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="431f8-121">从 https://github.com/PowerShell/Demo_CI 克隆的本地 Git 存储库</span><span class="sxs-lookup"><span data-stu-id="431f8-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="431f8-122">文本编辑器（如 [Visual Studio Code](https://code.visualstudio.com/)）</span><span class="sxs-lookup"><span data-stu-id="431f8-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="431f8-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="431f8-123">TFSSrv1</span></span>

<span data-ttu-id="431f8-124">托管 TFS 服务器的计算机，将在其中定义生成和发布。</span><span class="sxs-lookup"><span data-stu-id="431f8-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="431f8-125">必须在此计算机上安装 [Team Foundation Server 2017](https://www.visualstudio.com/tfs/)。</span><span class="sxs-lookup"><span data-stu-id="431f8-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="431f8-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="431f8-126">BuildAgent</span></span>

<span data-ttu-id="431f8-127">运行用于生成项目的 Windows 生成代理的计算机。</span><span class="sxs-lookup"><span data-stu-id="431f8-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="431f8-128">必须在此计算机上安装并运行 Windows 生成代理。</span><span class="sxs-lookup"><span data-stu-id="431f8-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="431f8-129">若要了解如何安装和运行 Windows 生成代理，请参阅[在 Windows 上部署代理](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows)。</span><span class="sxs-lookup"><span data-stu-id="431f8-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="431f8-130">还需要在此计算机上安装 `xDnsServer` 和 `xNetworking` DSC 模块。</span><span class="sxs-lookup"><span data-stu-id="431f8-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="431f8-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="431f8-131">TestAgent1</span></span>

<span data-ttu-id="431f8-132">在此示例中，DSC 配置将这台计算机配置为 DNS 服务器。</span><span class="sxs-lookup"><span data-stu-id="431f8-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="431f8-133">此计算机必须运行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="431f8-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="431f8-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="431f8-134">TestAgent2</span></span>

<span data-ttu-id="431f8-135">这是托管此示例配置的网站的计算机。</span><span class="sxs-lookup"><span data-stu-id="431f8-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="431f8-136">此计算机必须运行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="431f8-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="431f8-137">将代码添加到 TFS</span><span class="sxs-lookup"><span data-stu-id="431f8-137">Add the code to TFS</span></span>

<span data-ttu-id="431f8-138">首先，我们将在 TFS 中创建 Git 存储库，并导入客户端计算机上本地存储库中的代码。</span><span class="sxs-lookup"><span data-stu-id="431f8-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="431f8-139">如果尚未将 Demo_CI 存储库克隆到客户端计算机，请立即运行以下 git 命令：</span><span class="sxs-lookup"><span data-stu-id="431f8-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="431f8-140">在客户端计算机上的 Web 浏览器中，转到 TFS 服务器。</span><span class="sxs-lookup"><span data-stu-id="431f8-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="431f8-141">在 TFS 中，[新建名为“Demo_CI”的团队项目](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project)。</span><span class="sxs-lookup"><span data-stu-id="431f8-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

   <span data-ttu-id="431f8-142">请务必将“版本控制”设置为“Git”。</span><span class="sxs-lookup"><span data-stu-id="431f8-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="431f8-143">在客户端计算机上运行以下命令，添加对刚刚在 TFS 中创建的存储库的远程控制：</span><span class="sxs-lookup"><span data-stu-id="431f8-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="431f8-144">其中，`<YourTFSRepoURL>` 是在上一步中创建的 TFS 存储库的克隆 URL。</span><span class="sxs-lookup"><span data-stu-id="431f8-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="431f8-145">如果不知道在何处找到此 URL，请参阅[克隆现有 Git 存储库](https://www.visualstudio.com/en-us/docs/git/tutorial/clone)。</span><span class="sxs-lookup"><span data-stu-id="431f8-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="431f8-146">运行以下命令，将代码从本地存储库推送到 TFS 存储库：</span><span class="sxs-lookup"><span data-stu-id="431f8-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="431f8-147">此时，TFS 存储库将填充有 Demo_CI 代码。</span><span class="sxs-lookup"><span data-stu-id="431f8-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="431f8-148">此示例使用 Git 存储库 `ci-cd-example` 分支中的代码。</span><span class="sxs-lookup"><span data-stu-id="431f8-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="431f8-149">请务必将此分支指定为 TFS 项目和创建的 CI/CD 触发器的默认分支。</span><span class="sxs-lookup"><span data-stu-id="431f8-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="431f8-150">了解代码</span><span class="sxs-lookup"><span data-stu-id="431f8-150">Understanding the code</span></span>

<span data-ttu-id="431f8-151">创建生成和部署管道前，我们先来分析一些代码，以便了解具体情况。</span><span class="sxs-lookup"><span data-stu-id="431f8-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="431f8-152">在客户端计算机上，打开常用文本编辑器，再转到 Demo_CI Git 存储库根。</span><span class="sxs-lookup"><span data-stu-id="431f8-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="431f8-153">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="431f8-153">The DSC configuration</span></span>

<span data-ttu-id="431f8-154">从本地 Demo_CI 存储库根 `./InfraDNS/Configs/DNSServer.ps1` 打开文件 `DNSServer.ps1`。</span><span class="sxs-lookup"><span data-stu-id="431f8-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="431f8-155">此文件包含用于设置 DNS 服务器的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="431f8-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="431f8-156">完整内容如下：</span><span class="sxs-lookup"><span data-stu-id="431f8-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="431f8-157">请注意 `Node` 语句：</span><span class="sxs-lookup"><span data-stu-id="431f8-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="431f8-158">此语句可查找所有定义为在 `DevEnv.ps1` 脚本创建的[配置数据](configData.md)中担任 `DNSServer` 角色的节点。</span><span class="sxs-lookup"><span data-stu-id="431f8-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="431f8-159">可阅读 [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md) 了解有关 `Where` 方法的详细信息</span><span class="sxs-lookup"><span data-stu-id="431f8-159">You can read more about the `Where` method in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

<span data-ttu-id="431f8-160">请务必在执行 CI 时使用配置数据定义节点，因为节点信息可能会在不同环境中进行切换，而使用配置数据则可以轻松更改节点信息，无需更改配置代码。</span><span class="sxs-lookup"><span data-stu-id="431f8-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="431f8-161">在第一个资源块中，配置调用 [WindowsFeature](windowsFeatureResource.md)，以确保启用 DNS 功能。</span><span class="sxs-lookup"><span data-stu-id="431f8-161">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="431f8-162">后面的资源块调用 [xDnsServer](https://github.com/PowerShell/xDnsServer) 模块中的资源，以配置主要区域和 DNS 记录。</span><span class="sxs-lookup"><span data-stu-id="431f8-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="431f8-163">请注意，这两个 `xDnsRecord` 块包装在循环访问配置数据数组的 `foreach` 循环中。</span><span class="sxs-lookup"><span data-stu-id="431f8-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="431f8-164">再强调一遍，配置数据是由 `DevEnv.ps1` 脚本创建，接下来我们将对此进行分析。</span><span class="sxs-lookup"><span data-stu-id="431f8-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="431f8-165">配置数据</span><span class="sxs-lookup"><span data-stu-id="431f8-165">Configuration data</span></span>

<span data-ttu-id="431f8-166">`DevEnv.ps1` 文件位于本地 Demo_CI 存储库的根目录 `./InfraDNS/DevEnv.ps1`，在哈希表中指定环境专属配置数据，并将哈希表传递给 `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`) 中定义的 `New-DscConfigurationDataDocument` 函数调用。</span><span class="sxs-lookup"><span data-stu-id="431f8-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="431f8-167">`DevEnv.ps1` 文件：</span><span class="sxs-lookup"><span data-stu-id="431f8-167">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="431f8-168">`New-DscConfigurationDataDocument` 函数是在 `\Assets\DscPipelineTools\DscPipelineTools.psm1` 中进行定义，以编程方式通过作为 `RawEnvData` 和 `OtherEnvData` 参数传递的哈希表（节点数据）和数组（非节点数据）创建配置数据文档。</span><span class="sxs-lookup"><span data-stu-id="431f8-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="431f8-169">此示例只使用了 `RawEnvData` 参数。</span><span class="sxs-lookup"><span data-stu-id="431f8-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="431f8-170">psake 生成脚本</span><span class="sxs-lookup"><span data-stu-id="431f8-170">The psake build script</span></span>

<span data-ttu-id="431f8-171">在 `Build.ps1`（位于 Demo_CI 存储库的根目录 `./InfraDNS/Build.ps1`）中定义的 [psake](https://github.com/psake/psake) 生成脚本定义了生成任务。</span><span class="sxs-lookup"><span data-stu-id="431f8-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="431f8-172">它还定义了每个任务依赖的其他任务。</span><span class="sxs-lookup"><span data-stu-id="431f8-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="431f8-173">调用时，psake 脚本可确保指定的任务（或名为“`Default`”的任务，如果未指定的话）能够正常运行，并确保所有依赖项也能正常运行（这具有递归性，以便依赖项的依赖项也能正常运行，依此类推）。</span><span class="sxs-lookup"><span data-stu-id="431f8-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="431f8-174">在此示例中，`Default` 任务被定义为：</span><span class="sxs-lookup"><span data-stu-id="431f8-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="431f8-175">虽然 `Default` 任务本身并无实现代码，但却依赖 `CompileConfigs` 任务。</span><span class="sxs-lookup"><span data-stu-id="431f8-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="431f8-176">生成的任务依赖关系链可确保生成脚本中的所有任务都能正常运行。</span><span class="sxs-lookup"><span data-stu-id="431f8-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="431f8-177">在此示例中，通过调用 `Initiate.ps1` 文件（位于 Demo_CI 存储库的根目录）中的 `Invoke-PSake` 来调用 psake 脚本：</span><span class="sxs-lookup"><span data-stu-id="431f8-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="431f8-178">在 TFS 中为此示例创建生成定义时，将提供 psake 脚本文件作为这个脚本的 `fileName` 参数。</span><span class="sxs-lookup"><span data-stu-id="431f8-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="431f8-179">生成脚本定义以下任务：</span><span class="sxs-lookup"><span data-stu-id="431f8-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="431f8-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="431f8-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="431f8-181">运行用于生成配置数据文件的 `DevEnv.ps1`。</span><span class="sxs-lookup"><span data-stu-id="431f8-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="431f8-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="431f8-182">InstallModules</span></span>

<span data-ttu-id="431f8-183">安装配置 `DNSServer.ps1` 所需的模块。</span><span class="sxs-lookup"><span data-stu-id="431f8-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="431f8-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="431f8-184">ScriptAnalysis</span></span>

<span data-ttu-id="431f8-185">调用 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)。</span><span class="sxs-lookup"><span data-stu-id="431f8-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="431f8-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="431f8-186">UnitTests</span></span>

<span data-ttu-id="431f8-187">运行 [Pester](https://github.com/pester/Pester/wiki) 单元测试。</span><span class="sxs-lookup"><span data-stu-id="431f8-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="431f8-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="431f8-188">CompileConfigs</span></span>

<span data-ttu-id="431f8-189">使用 `GenerateEnvironmentFiles` 任务生成的配置数据，将配置 (`DNSServer.ps1`) 编译到 MOF 文件中。</span><span class="sxs-lookup"><span data-stu-id="431f8-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="431f8-190">clean</span><span class="sxs-lookup"><span data-stu-id="431f8-190">Clean</span></span>

<span data-ttu-id="431f8-191">创建用于此示例的文件夹，并删除在之前运行中生成的所有测试结果、配置数据文件和模块。</span><span class="sxs-lookup"><span data-stu-id="431f8-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="431f8-192">psake 部署脚本</span><span class="sxs-lookup"><span data-stu-id="431f8-192">The psake deploy script</span></span>

<span data-ttu-id="431f8-193">在 `Deploy.ps1`（位于 Demo_CI 存储库的根目录 `./InfraDNS/Deploy.ps1`）中定义的 [psake](https://github.com/psake/psake) 部署脚本定义了部署和运行配置的任务。</span><span class="sxs-lookup"><span data-stu-id="431f8-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="431f8-194">`Deploy.ps1` 定义以下任务：</span><span class="sxs-lookup"><span data-stu-id="431f8-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="431f8-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="431f8-195">DeployModules</span></span>

<span data-ttu-id="431f8-196">在 `TestAgent1` 上启动 PowerShell 会话，并安装包含配置所需 DSC 资源的模块。</span><span class="sxs-lookup"><span data-stu-id="431f8-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="431f8-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="431f8-197">DeployConfigs</span></span>

<span data-ttu-id="431f8-198">调用 [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet，以在 `TestAgent1` 上运行配置。</span><span class="sxs-lookup"><span data-stu-id="431f8-198">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="431f8-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="431f8-199">IntegrationTests</span></span>

<span data-ttu-id="431f8-200">运行 [Pester](https://github.com/pester/Pester/wiki) 集成测试。</span><span class="sxs-lookup"><span data-stu-id="431f8-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="431f8-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="431f8-201">AcceptanceTests</span></span>

<span data-ttu-id="431f8-202">运行 [Pester](https://github.com/pester/Pester/wiki) 验收测试。</span><span class="sxs-lookup"><span data-stu-id="431f8-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="431f8-203">clean</span><span class="sxs-lookup"><span data-stu-id="431f8-203">Clean</span></span>

<span data-ttu-id="431f8-204">删除在之前运行中安装的所有模块，并确保有测试结果文件夹。</span><span class="sxs-lookup"><span data-stu-id="431f8-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="431f8-205">测试脚本</span><span class="sxs-lookup"><span data-stu-id="431f8-205">Test scripts</span></span>

<span data-ttu-id="431f8-206">验收测试、集成测试和单元测试在 `Tests` 文件夹（位于 Demo_CI 存储库的根目录 `./InfraDNS/Tests`）的脚本中进行定义，每个脚本位于各自文件夹内名为“`DNSServer.tests.ps1`”的文件中。</span><span class="sxs-lookup"><span data-stu-id="431f8-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="431f8-207">测试脚本使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 语法。</span><span class="sxs-lookup"><span data-stu-id="431f8-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="431f8-208">单元测试</span><span class="sxs-lookup"><span data-stu-id="431f8-208">Unit tests</span></span>

<span data-ttu-id="431f8-209">单元测试用于测试 DSC 配置本身，以确保配置能够按预期运行。</span><span class="sxs-lookup"><span data-stu-id="431f8-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="431f8-210">单元测试脚本使用 [Pester](https://github.com/pester/Pester/wiki)。</span><span class="sxs-lookup"><span data-stu-id="431f8-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="431f8-211">集成测试</span><span class="sxs-lookup"><span data-stu-id="431f8-211">Integration tests</span></span>

<span data-ttu-id="431f8-212">集成测试用于测试系统配置，以确保在与其他组件集成时，能够按预期配置系统。</span><span class="sxs-lookup"><span data-stu-id="431f8-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="431f8-213">使用 DSC 配置的此类测试在目标节点上运行。</span><span class="sxs-lookup"><span data-stu-id="431f8-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="431f8-214">集成测试脚本混用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 语法。</span><span class="sxs-lookup"><span data-stu-id="431f8-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="431f8-215">验收测试</span><span class="sxs-lookup"><span data-stu-id="431f8-215">Acceptance tests</span></span>

<span data-ttu-id="431f8-216">验收测试用于测试系统，以确保其行为符合预期。</span><span class="sxs-lookup"><span data-stu-id="431f8-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="431f8-217">例如，它执行测试，以确保网页在查询时返回正确的信息。</span><span class="sxs-lookup"><span data-stu-id="431f8-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="431f8-218">此类测试是从目标节点远程运行，以测试实际方案。</span><span class="sxs-lookup"><span data-stu-id="431f8-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="431f8-219">集成测试脚本混用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 语法。</span><span class="sxs-lookup"><span data-stu-id="431f8-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="431f8-220">定义生成</span><span class="sxs-lookup"><span data-stu-id="431f8-220">Define the build</span></span>

<span data-ttu-id="431f8-221">至此，我们已经将代码上传到了 TFS 并分析了代码用途，让我们来定义生成吧。</span><span class="sxs-lookup"><span data-stu-id="431f8-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="431f8-222">本文将只介绍要添加到生成定义的生成步骤。</span><span class="sxs-lookup"><span data-stu-id="431f8-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="431f8-223">若要了解如何在 TFS 中创建生成定义，请参阅[创建并将生成定义排入队列](https://www.visualstudio.com/en-us/docs/build/define/create)。</span><span class="sxs-lookup"><span data-stu-id="431f8-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="431f8-224">新建名为“InfraDNS”的生成定义（选择“空”模板）。</span><span class="sxs-lookup"><span data-stu-id="431f8-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="431f8-225">向生成定义添加以下步骤：</span><span class="sxs-lookup"><span data-stu-id="431f8-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="431f8-226">PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="431f8-226">PowerShell Script</span></span>
- <span data-ttu-id="431f8-227">发布测试结果</span><span class="sxs-lookup"><span data-stu-id="431f8-227">Publish Test Results</span></span>
- <span data-ttu-id="431f8-228">复制文件</span><span class="sxs-lookup"><span data-stu-id="431f8-228">Copy Files</span></span>
- <span data-ttu-id="431f8-229">发布项目</span><span class="sxs-lookup"><span data-stu-id="431f8-229">Publish Artifact</span></span>

<span data-ttu-id="431f8-230">在添加这些生成步骤之后，编辑每个步骤的属性，如下所述：</span><span class="sxs-lookup"><span data-stu-id="431f8-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="431f8-231">PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="431f8-231">PowerShell Script</span></span>

1. <span data-ttu-id="431f8-232">将“类型”属性设置为“`File Path`”。</span><span class="sxs-lookup"><span data-stu-id="431f8-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="431f8-233">将“脚本路径”属性设置为“`initiate.ps1`”。</span><span class="sxs-lookup"><span data-stu-id="431f8-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="431f8-234">向“参数”属性添加“`-fileName build`”。</span><span class="sxs-lookup"><span data-stu-id="431f8-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="431f8-235">此生成步骤运行用于调用 psake 生成脚本的 `initiate.ps1` 文件。</span><span class="sxs-lookup"><span data-stu-id="431f8-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="431f8-236">发布测试结果</span><span class="sxs-lookup"><span data-stu-id="431f8-236">Publish Test Results</span></span>

1. <span data-ttu-id="431f8-237">将“测试结果格式”设置为“`NUnit`”</span><span class="sxs-lookup"><span data-stu-id="431f8-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="431f8-238">将“测试结果文件”设置为“`InfraDNS/Tests/Results/*.xml`”</span><span class="sxs-lookup"><span data-stu-id="431f8-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="431f8-239">将“测试运行标题”设置为“`Unit`”。</span><span class="sxs-lookup"><span data-stu-id="431f8-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="431f8-240">请务必选中“控制选项已启用”和“始终运行”。</span><span class="sxs-lookup"><span data-stu-id="431f8-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="431f8-241">此生成步骤在我们前面分析的 Pester 脚本中运行单元测试，并将结果存储在 `InfraDNS/Tests/Results/*.xml` 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="431f8-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="431f8-242">复制文件</span><span class="sxs-lookup"><span data-stu-id="431f8-242">Copy Files</span></span>

1. <span data-ttu-id="431f8-243">将以下代码行添加到“内容”：</span><span class="sxs-lookup"><span data-stu-id="431f8-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="431f8-244">将“目标文件夹”设置为“`$(Build.ArtifactStagingDirectory)\`”</span><span class="sxs-lookup"><span data-stu-id="431f8-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="431f8-245">此步骤将生成和测试脚本复制到临时目录，以便它们可以在下一步中作为生成项目发布。</span><span class="sxs-lookup"><span data-stu-id="431f8-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="431f8-246">发布项目</span><span class="sxs-lookup"><span data-stu-id="431f8-246">Publish Artifact</span></span>

1. <span data-ttu-id="431f8-247">将“发布路径”设置为“`$(Build.ArtifactStagingDirectory)\`”</span><span class="sxs-lookup"><span data-stu-id="431f8-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="431f8-248">将“项目名称”设置为“`Deploy`”</span><span class="sxs-lookup"><span data-stu-id="431f8-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="431f8-249">将“项目类型”设置为“`Server`”</span><span class="sxs-lookup"><span data-stu-id="431f8-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="431f8-250">在“控制选项”中选择“`Enabled`”</span><span class="sxs-lookup"><span data-stu-id="431f8-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="431f8-251">启用持续集成</span><span class="sxs-lookup"><span data-stu-id="431f8-251">Enable continuous integration</span></span>

<span data-ttu-id="431f8-252">现在，我们将设置一个触发器，这样只要有更改签入 git 存储库的 `ci-cd-example` 分支，便会触发项目生成。</span><span class="sxs-lookup"><span data-stu-id="431f8-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="431f8-253">在 TFS 中，单击“生成和发布”选项卡</span><span class="sxs-lookup"><span data-stu-id="431f8-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="431f8-254">选择“`DNS Infra`”生成定义，再单击“编辑”</span><span class="sxs-lookup"><span data-stu-id="431f8-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="431f8-255">单击“触发器”选项卡</span><span class="sxs-lookup"><span data-stu-id="431f8-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="431f8-256">依次选择“持续集成(CI)”和分支下拉列表中的“`refs/heads/ci-cd-example`”</span><span class="sxs-lookup"><span data-stu-id="431f8-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="431f8-257">依次单击“保存”和“确定”</span><span class="sxs-lookup"><span data-stu-id="431f8-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="431f8-258">此时，只要 TFS git 存储库中有任何更改，都会触发自动生成。</span><span class="sxs-lookup"><span data-stu-id="431f8-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="431f8-259">创建发布定义</span><span class="sxs-lookup"><span data-stu-id="431f8-259">Create the release definition</span></span>

<span data-ttu-id="431f8-260">让我们来创建发布定义，以便将项目部署到包含每个代码签入信息的开发环境。</span><span class="sxs-lookup"><span data-stu-id="431f8-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="431f8-261">为此，添加与之前创建的 `InfraDNS` 生成定义相关联的新发布定义。</span><span class="sxs-lookup"><span data-stu-id="431f8-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="431f8-262">请务必选择“连续部署”，以便只要有新生成完成，都会触发新发布。</span><span class="sxs-lookup"><span data-stu-id="431f8-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="431f8-263">请参阅[如何：使用发布定义](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)，并按如下进行配置：</span><span class="sxs-lookup"><span data-stu-id="431f8-263">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="431f8-264">向发布定义添加以下步骤：</span><span class="sxs-lookup"><span data-stu-id="431f8-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="431f8-265">PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="431f8-265">PowerShell Script</span></span>
- <span data-ttu-id="431f8-266">发布测试结果</span><span class="sxs-lookup"><span data-stu-id="431f8-266">Publish Test Results</span></span>
- <span data-ttu-id="431f8-267">发布测试结果</span><span class="sxs-lookup"><span data-stu-id="431f8-267">Publish Test Results</span></span>

<span data-ttu-id="431f8-268">按如下所述编辑步骤：</span><span class="sxs-lookup"><span data-stu-id="431f8-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="431f8-269">PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="431f8-269">PowerShell Script</span></span>

1. <span data-ttu-id="431f8-270">将“脚本路径”字段设置为“`$(Build.DefinitionName)\Deploy\initiate.ps1"`”</span><span class="sxs-lookup"><span data-stu-id="431f8-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="431f8-271">将“参数”字段设置为“`-fileName Deploy`”</span><span class="sxs-lookup"><span data-stu-id="431f8-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="431f8-272">第一次发布测试结果</span><span class="sxs-lookup"><span data-stu-id="431f8-272">First Publish Test Results</span></span>

1. <span data-ttu-id="431f8-273">为“测试结果格式”字段选择“`NUnit`”</span><span class="sxs-lookup"><span data-stu-id="431f8-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="431f8-274">将“测试结果文件”字段设置为“`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`”</span><span class="sxs-lookup"><span data-stu-id="431f8-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="431f8-275">将“测试运行标题”设置为“`Integration`”</span><span class="sxs-lookup"><span data-stu-id="431f8-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="431f8-276">在“控制选项”下，选中“始终运行”</span><span class="sxs-lookup"><span data-stu-id="431f8-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="431f8-277">第二次发布测试结果</span><span class="sxs-lookup"><span data-stu-id="431f8-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="431f8-278">为“测试结果格式”字段选择“`NUnit`”</span><span class="sxs-lookup"><span data-stu-id="431f8-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="431f8-279">将“测试结果文件”字段设置为“`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`”</span><span class="sxs-lookup"><span data-stu-id="431f8-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="431f8-280">将“测试运行标题”设置为“`Acceptance`”</span><span class="sxs-lookup"><span data-stu-id="431f8-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="431f8-281">在“控制选项”下，选中“始终运行”</span><span class="sxs-lookup"><span data-stu-id="431f8-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="431f8-282">验证结果</span><span class="sxs-lookup"><span data-stu-id="431f8-282">Verify your results</span></span>

<span data-ttu-id="431f8-283">此时，只要将 `ci-cd-example` 中的更改推送到 TFS，都会启动新生成。</span><span class="sxs-lookup"><span data-stu-id="431f8-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="431f8-284">如果生成成功完成，便会触发新部署。</span><span class="sxs-lookup"><span data-stu-id="431f8-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="431f8-285">可以在客户端计算机上打开浏览器并转到 `www.contoso.com`，从而检查部署结果。</span><span class="sxs-lookup"><span data-stu-id="431f8-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="431f8-286">后续步骤</span><span class="sxs-lookup"><span data-stu-id="431f8-286">Next steps</span></span>

<span data-ttu-id="431f8-287">此示例配置 DNS 服务器 `TestAgent1`，以便 URL `www.contoso.com` 解析为 `TestAgent2`，但实际并不部署网站。</span><span class="sxs-lookup"><span data-stu-id="431f8-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="431f8-288">存储库中的 `WebApp` 文件夹下提供了执行此操作的相关框架。</span><span class="sxs-lookup"><span data-stu-id="431f8-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="431f8-289">可以使用所提供的存根来创建 psake 脚本、Pester 测试和 DSC 配置，从而部署自己的网站。</span><span class="sxs-lookup"><span data-stu-id="431f8-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>