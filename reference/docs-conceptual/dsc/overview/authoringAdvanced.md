---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 了解 CI/CD 管道中的 DSC 角色
ms.openlocfilehash: 79740225c030974546035b67e0f873fa00aa690a
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279331"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>了解 CI/CD 管道中的 DSC 角色

本文介绍了可用于组合配置和资源的方法类型。
每种方案的目标都是相同的，即在首选多个配置时降低复杂性以达到服务器部署最终状态。 为服务器部署结果做出贡献的多个团队可作为该方面的一个示例，例如维护应用程序状态的应用程序所有者和释放安全基线更改的中央团队。 此处详细介绍了每种方法的细微差别，包括收益和风险。

![管道](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>协同创作技术的类型

本地 Configuration Manager 内置两个解决方案来启用此概念：

|        概念         |                    详细信息                     |
| ---------------------- | ----------------------------------------------------------- |
| 部分配置 | [文档](../pull-server/partialConfigs.md)           |
| 复合资源    | [文档](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a>了解每种方法的影响

这些解决方案中的任何一个都可用于管理服务器部署的结果。 但是，使用每种方法的影响存在显著差异。

## <a name="partial-configurations"></a>部分配置

使用部分配置时，将本地 Configuration Manager 配置为独立管理多个配置。 独立编译配置，然后将其分配给节点。 这需要提前使用每个配置的名称配置 LCM。

![PartialConfiguration](media/authoringAdvanced/PartialConfiguration.jpg)

部分配置提供两个或以上完全控制服务器配置的团队，通常没有通信或协作的权益。

客户提供的反馈表明，这可能导致资源冲突、无意覆盖，并最终导致资产的真实配置控制丢失。

除此之外，客户还提供了反馈，在使用此模型时，每个控制团队的配置更改都不太可能通过发布管道进行全面测试，从而导致生产中出现意外结果。

使用单个管道评估发布到服务器的所有更改至关重要  。

在下图中，团队 B 将其部分配置发布到团队 A，然后团队 A 针对应用了两种配置的服务器运行测试。 在此模型中，只有一个机构有权在生产中进行更改。

![PartialSinglePipeline](media/authoringAdvanced/PartialSinglePipeline.jpg)

团队 B 需要进行更改时，他们应针对团队 A 的源代码管理环境提交拉取请求。 若确信更改不会导致服务器托管的应用程序或服务出现错误，则团队 A 将使用测试自动化审阅更改并将其发布到生产中。

## <a name="composite-resources"></a>复合资源

复合资源只是作为资源打包的 DSC 配置。 配置 LCM 以接受复合资源没有特殊要求。 在新配置中使用资源，在一个 MOF 文件中生成单个编译结果。

![CompositeResource](media/authoringAdvanced/CompositeResource.jpg)

复合资源有两种常见方案。 第一个方案是降低复杂性和抽象独特概念。 第二个方案是允许为应用程序团队打包基线，以便在所有测试通过后通过其发布管道将其安全地部署到生产。

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

复合资源在构建操作成熟度的同时使用管道促进组合和协作。

你可能已在使用复合资源却没有意识到这一点。 ServiceSet 就是一个示例  。
此资源管理多个 Windows 服务的状态，而无需单独列出它们。 Name 属性接受一个字符串数组，以提供每个服务的名称。 编译配置时，MOF 将包含传递给 ServiceSet 的每个名称的唯一服务部分。

组织可能具有应安装在每台服务器上的“代理”或“中间件”。 复合资源是管理任何此类工具和实用程序的依赖关系、设置和配置的最佳答案。

负责跨多个服务器的解决方案的人员或团队对包含其要求的配置进行编写。 接下来，使用复合资源文档中提供的指令将配置打包为复合资源。 最后，应将新的复合资源发布到诸如文件共享或 NuGet 源之类的位置，在此处应用程序团队可在其配置中使用它。

每次团队发布新版本时，他们都会在模块清单中为其复合资源递增版本号。 应用程序团队将复合资源包含在他们为管理应用程序依赖性而创建的配置中。 当操作/安全团队发布其资源的新版本时，他们会通知应用程序团队有新的更改。

应用程序团队可能会触发发布到生产，其中唯一的变化是基线。
但是，这提供了在服务中断风险之前评估对应用程序的影响的机会。

> [!NOTE]
> 关于使用复合资源的反馈包括批评，即进行更改需要编译和发布新 MOF。 这是设计的结果。 每个新配置版本都应包含对每个资源的特定版本的静态引用，并且应在到达生产服务器节点之前通过测试进行验证。 从源代码管理中测试和发布更改的过程创建了一个安全的环境，用于在小型但频繁的批处理中发布更改。

有关使用发布管道管理核心基础结构的详细信息，请参阅白皮书：[发布管道模型](../further-reading/whitepapers.md)。
