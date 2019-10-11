---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用 DSC 生成持续集成和连续部署管道
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954234"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>使用 DSC 生成持续集成和连续部署管道

此示例展示了如何使用 PowerShell、DSC、Pester 和 Visual Studio Team Foundation Server (TFS) 生成持续集成/连续部署 (CI/CD) 管道。

生成和配置管道后，可以用它来完全部署、配置和测试 DNS 服务器及关联的主机记录。
此过程模拟了将用于开发环境的管道第一部分。

自动 CI/CD 管道有助于更快、更可靠地更新软件，确保所有代码都经过测试，并确保最新版代码始终可用。

## <a name="prerequisites"></a>必备条件

若要使用此示例，应熟悉以下内容：

- CI-CD 概念。 [发布管道模型](https://aka.ms/thereleasepipelinemodelpdf)提供了很好的参考资源。
- [Git](https://git-scm.com/) 源控件
- [Pester](https://github.com/pester/Pester) 测试框架
- [Team Foundation Server](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a>将需要

若要生成并运行此示例，需要一个包含多台计算机和/或虚拟机的环境。

### <a name="client"></a>客户端

将在这台计算机上执行生成和运行此示例所需的全部工作。

客户端计算机必须是安装以下项的 Windows 计算机：

- [Git](https://git-scm.com/)
- 从 https://github.com/PowerShell/Demo_CI 克隆的本地 Git 存储库
- 文本编辑器（如 [Visual Studio Code](https://code.visualstudio.com/)）

### <a name="tfssrv1"></a>TFSSrv1

托管 TFS 服务器的计算机，将在其中定义生成和发布。
必须在此计算机上安装 [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/)。

### <a name="buildagent"></a>BuildAgent

运行用于生成项目的 Windows 生成代理的计算机。
必须在此计算机上安装并运行 Windows 生成代理。
若要了解如何安装和运行 Windows 生成代理，请参阅[在 Windows 上部署代理](/azure/devops/pipelines/agents/v2-windows)。

还需要在此计算机上安装 `xDnsServer` 和 `xNetworking` DSC 模块。

### <a name="testagent1"></a>TestAgent1

在此示例中，DSC 配置将这台计算机配置为 DNS 服务器。
此计算机必须运行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。

### <a name="testagent2"></a>TestAgent2

这是托管此示例配置的网站的计算机。
此计算机必须运行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。

## <a name="add-the-code-to-tfs"></a>将代码添加到 TFS

首先，我们将在 TFS 中创建 Git 存储库，并导入客户端计算机上本地存储库中的代码。
如果尚未将 Demo_CI 存储库克隆到客户端计算机，请立即运行以下 git 命令：

`git clone https://github.com/PowerShell/Demo_CI`

1. 在客户端计算机上的 Web 浏览器中，转到 TFS 服务器。
1. 在 TFS 中，[新建名为“Demo_CI”的团队项目](/azure/devops/organizations/projects/create-project)。

   请务必将“版本控制”  设置为“Git”  。
1. 在客户端计算机上运行以下命令，添加对刚刚在 TFS 中创建的存储库的远程控制：

   `git remote add tfs <YourTFSRepoURL>`

   其中，`<YourTFSRepoURL>` 是在上一步中创建的 TFS 存储库的克隆 URL。

   如果不知道在何处找到此 URL，请参阅[克隆现有 Git 存储库](/azure/devops/repos/git/clone)。
1. 运行以下命令，将代码从本地存储库推送到 TFS 存储库：

   `git push tfs --all`
1. 此时，TFS 存储库将填充有 Demo_CI 代码。

> [!NOTE]
> 此示例使用 Git 存储库 `ci-cd-example` 分支中的代码。
> 请务必将此分支指定为 TFS 项目和创建的 CI/CD 触发器的默认分支。

## <a name="understanding-the-code"></a>了解代码

创建生成和部署管道前，我们先来分析一些代码，以便了解具体情况。
在客户端计算机上，打开常用文本编辑器，再转到 Demo_CI Git 存储库根。

### <a name="the-dsc-configuration"></a>DSC 配置

从本地 Demo_CI 存储库根 `./InfraDNS/Configs/DNSServer.ps1` 打开文件 `DNSServer.ps1`。

此文件包含用于设置 DNS 服务器的 DSC 配置。 完整内容如下：

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

请注意 `Node` 语句：

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

此语句可查找所有定义为在 `DevEnv.ps1` 脚本创建的[配置数据](../configurations/configData.md)中担任 `DNSServer` 角色的节点。

可阅读 [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays) 了解有关 `Where` 方法的详细信息

请务必在执行 CI 时使用配置数据定义节点，因为节点信息可能会在不同环境中进行切换，而使用配置数据则可以轻松更改节点信息，无需更改配置代码。

在第一个资源块中，配置调用 **WindowsFeature**，以确保启用 DNS 功能。
后面的资源块调用 [xDnsServer](https://github.com/PowerShell/xDnsServer) 模块中的资源，以配置主要区域和 DNS 记录。

请注意，这两个 `xDnsRecord` 块包装在循环访问配置数据数组的 `foreach` 循环中。
再强调一遍，配置数据是由 `DevEnv.ps1` 脚本创建，接下来我们将对此进行分析。

### <a name="configuration-data"></a>配置数据

`DevEnv.ps1` 文件位于本地 Demo_CI 存储库的根目录 `./InfraDNS/DevEnv.ps1`，在哈希表中指定环境专属配置数据，并将哈希表传递给 `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`) 中定义的 `New-DscConfigurationDataDocument` 函数调用。

`DevEnv.ps1` 文件：

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

`New-DscConfigurationDataDocument` 函数是在 `\Assets\DscPipelineTools\DscPipelineTools.psm1` 中进行定义，以编程方式通过作为 `RawEnvData` 和 `OtherEnvData` 参数传递的哈希表（节点数据）和数组（非节点数据）创建配置数据文档。

此示例只使用了 `RawEnvData` 参数。

### <a name="the-psake-build-script"></a>psake 生成脚本

在 `Build.ps1`（位于 Demo_CI 存储库的根目录 `./InfraDNS/Build.ps1`）中定义的 [psake](https://github.com/psake/psake) 生成脚本定义了生成任务。
它还定义了每个任务依赖的其他任务。
调用时，psake 脚本可确保指定的任务（或名为“`Default`”的任务，如果未指定的话）能够正常运行，并确保所有依赖项也能正常运行（这具有递归性，以便依赖项的依赖项也能正常运行，依此类推）。

在此示例中，`Default` 任务被定义为：

```powershell
Task Default -depends UnitTests
```

虽然 `Default` 任务本身并无实现代码，但却依赖 `CompileConfigs` 任务。
生成的任务依赖关系链可确保生成脚本中的所有任务都能正常运行。

在此示例中，通过调用 `Initiate.ps1` 文件（位于 Demo_CI 存储库的根目录）中的 `Invoke-PSake` 来调用 psake 脚本：

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

在 TFS 中为此示例创建生成定义时，将提供 psake 脚本文件作为这个脚本的 `fileName` 参数。

生成脚本定义以下任务：

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

运行用于生成配置数据文件的 `DevEnv.ps1`。

#### <a name="installmodules"></a>InstallModules

安装配置 `DNSServer.ps1` 所需的模块。

#### <a name="scriptanalysis"></a>ScriptAnalysis

调用 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)。

#### <a name="unittests"></a>UnitTests

运行 [Pester](https://github.com/pester/Pester/wiki) 单元测试。

#### <a name="compileconfigs"></a>CompileConfigs

使用 `GenerateEnvironmentFiles` 任务生成的配置数据，将配置 (`DNSServer.ps1`) 编译到 MOF 文件中。

#### <a name="clean"></a>clean

创建用于此示例的文件夹，并删除在之前运行中生成的所有测试结果、配置数据文件和模块。

### <a name="the-psake-deploy-script"></a>psake 部署脚本

在 `Deploy.ps1`（位于 Demo_CI 存储库的根目录 `./InfraDNS/Deploy.ps1`）中定义的 [psake](https://github.com/psake/psake) 部署脚本定义了部署和运行配置的任务。

`Deploy.ps1` 定义以下任务：

#### <a name="deploymodules"></a>DeployModules

在 `TestAgent1` 上启动 PowerShell 会话，并安装包含配置所需 DSC 资源的模块。

#### <a name="deployconfigs"></a>DeployConfigs

调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet，以在 `TestAgent1` 上运行配置。

#### <a name="integrationtests"></a>IntegrationTests

运行 [Pester](https://github.com/pester/Pester/wiki) 集成测试。

#### <a name="acceptancetests"></a>AcceptanceTests

运行 [Pester](https://github.com/pester/Pester/wiki) 验收测试。

#### <a name="clean"></a>clean

删除在之前运行中安装的所有模块，并确保有测试结果文件夹。

### <a name="test-scripts"></a>测试脚本

验收测试、集成测试和单元测试在 `Tests` 文件夹（位于 Demo_CI 存储库的根目录 `./InfraDNS/Tests`）的脚本中进行定义，每个脚本位于各自文件夹内名为“`DNSServer.tests.ps1`”的文件中。

测试脚本使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 语法。

#### <a name="unit-tests"></a>单元测试

单元测试用于测试 DSC 配置本身，以确保配置能够按预期运行。
单元测试脚本使用 [Pester](https://github.com/pester/Pester/wiki)。

#### <a name="integration-tests"></a>集成测试

集成测试用于测试系统配置，以确保在与其他组件集成时，能够按预期配置系统。 使用 DSC 配置的此类测试在目标节点上运行。
集成测试脚本混用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 语法。

#### <a name="acceptance-tests"></a>验收测试

验收测试用于测试系统，以确保其行为符合预期。
例如，它执行测试，以确保网页在查询时返回正确的信息。
此类测试是从目标节点远程运行，以测试实际方案。
集成测试脚本混用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 语法。

## <a name="define-the-build"></a>定义生成

至此，我们已经将代码上传到了 TFS 并分析了代码用途，让我们来定义生成吧。

本文将只介绍要添加到生成定义的生成步骤。 若要了解如何在 TFS 中创建生成定义，请参阅[创建并将生成定义排入队列](/azure/devops/pipelines/create-first-pipeline)。

新建名为“InfraDNS”的生成定义（选择“空”  模板）。
向生成定义添加以下步骤：

- PowerShell 脚本
- 发布测试结果
- 复制文件
- 发布项目

在添加这些生成步骤之后，编辑每个步骤的属性，如下所述：

### <a name="powershell-script"></a>PowerShell 脚本

1. 将“类型”  属性设置为“`File Path`”。
1. 将“脚本路径”  属性设置为“`initiate.ps1`”。
1. 向“参数”  属性添加“`-fileName build`”。

此生成步骤运行用于调用 psake 生成脚本的 `initiate.ps1` 文件。

### <a name="publish-test-results"></a>发布测试结果

1. 将“测试结果格式”  设置为“`NUnit`”
1. 将“测试结果文件”  设置为“`InfraDNS/Tests/Results/*.xml`”
1. 将“测试运行标题”  设置为“`Unit`”。
1. 请务必选中“控制选项已启用”   和“始终运行”  。

此生成步骤在我们前面分析的 Pester 脚本中运行单元测试，并将结果存储在 `InfraDNS/Tests/Results/*.xml` 文件夹中。

### <a name="copy-files"></a>复制文件

1. 将以下代码行添加到“内容”  ：

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. 将“目标文件夹”  设置为“`$(Build.ArtifactStagingDirectory)\`”

此步骤将生成和测试脚本复制到临时目录，以便它们可以在下一步中作为生成项目发布。

### <a name="publish-artifact"></a>发布项目

1. 将“发布路径”  设置为“`$(Build.ArtifactStagingDirectory)\`”
1. 将“项目名称”  设置为“`Deploy`”
1. 将“项目类型”  设置为“`Server`”
1. 在“控制选项”  中选择“`Enabled`”

## <a name="enable-continuous-integration"></a>启用持续集成

现在，我们将设置一个触发器，这样只要有更改签入 git 存储库的 `ci-cd-example` 分支，便会触发项目生成。

1. 在 TFS 中，单击“生成和发布”  选项卡
1. 选择“`DNS Infra`”生成定义，再单击“编辑” 
1. 单击“触发器”  选项卡
1. 依次选择“持续集成(CI)”  和分支下拉列表中的“`refs/heads/ci-cd-example`”
1. 依次单击“保存”  和“确定” 

此时，只要 TFS git 存储库中有任何更改，都会触发自动生成。

## <a name="create-the-release-definition"></a>创建发布定义

让我们来创建发布定义，以便将项目部署到包含每个代码签入信息的开发环境。

为此，添加与之前创建的 `InfraDNS` 生成定义相关联的新发布定义。
请务必选择“连续部署”  ，以便只要有新生成完成，都会触发新发布。
（请参阅[发布管道是什么？](/azure/devops/pipelines/release/)），然后按如下进行配置：

向发布定义添加以下步骤：

- PowerShell 脚本
- 发布测试结果
- 发布测试结果

按如下所述编辑步骤：

### <a name="powershell-script"></a>PowerShell 脚本

1. 将“脚本路径”  字段设置为“`$(Build.DefinitionName)\Deploy\initiate.ps1"`”
1. 将“参数”  字段设置为“`-fileName Deploy`”

### <a name="first-publish-test-results"></a>第一次发布测试结果

1. 为“测试结果格式”  字段选择“`NUnit`”
1. 将“测试结果文件”  字段设置为“`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`”
1. 将“测试运行标题”  设置为“`Integration`”
1. 在“控制选项”  下，选中“始终运行” 

### <a name="second-publish-test-results"></a>第二次发布测试结果

1. 为“测试结果格式”  字段选择“`NUnit`”
1. 将“测试结果文件”  字段设置为“`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`”
1. 将“测试运行标题”  设置为“`Acceptance`”
1. 在“控制选项”  下，选中“始终运行” 

## <a name="verify-your-results"></a>验证结果

此时，只要将 `ci-cd-example` 中的更改推送到 TFS，都会启动新生成。
如果生成成功完成，便会触发新部署。

可以在客户端计算机上打开浏览器并转到 `www.contoso.com`，从而检查部署结果。

## <a name="next-steps"></a>后续步骤

此示例配置 DNS 服务器 `TestAgent1`，以便 URL `www.contoso.com` 解析为 `TestAgent2`，但实际并不部署网站。
存储库中的 `WebApp` 文件夹下提供了执行此操作的相关框架。
可以使用所提供的存根来创建 psake 脚本、Pester 测试和 DSC 配置，从而部署自己的网站。
