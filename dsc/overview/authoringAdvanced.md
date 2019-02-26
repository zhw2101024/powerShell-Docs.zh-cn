---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 了解 CI/CD 管道中的 DSC 角色
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803372"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="f1b73-103">了解 CI/CD 管道中的 DSC 角色</span><span class="sxs-lookup"><span data-stu-id="f1b73-103">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="f1b73-104">本文介绍了可用于组合配置和资源的方法类型。</span><span class="sxs-lookup"><span data-stu-id="f1b73-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="f1b73-105">每种方案的目标都是相同的，即在首选多个配置时降低复杂性以达到服务器部署最终状态。</span><span class="sxs-lookup"><span data-stu-id="f1b73-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="f1b73-106">为服务器部署结果做出贡献的多个团队可作为该方面的一个示例，例如维护应用程序状态的应用程序所有者和释放安全基线更改的中央团队。</span><span class="sxs-lookup"><span data-stu-id="f1b73-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="f1b73-107">此处详细介绍了每种方法的细微差别，包括收益和风险。</span><span class="sxs-lookup"><span data-stu-id="f1b73-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![管道](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="f1b73-109">协同创作技术的类型</span><span class="sxs-lookup"><span data-stu-id="f1b73-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="f1b73-110">本地 Configuration Manager 内置两个解决方案来启用此概念：</span><span class="sxs-lookup"><span data-stu-id="f1b73-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="f1b73-111">概念</span><span class="sxs-lookup"><span data-stu-id="f1b73-111">Concept</span></span> | <span data-ttu-id="f1b73-112">详细信息</span><span class="sxs-lookup"><span data-stu-id="f1b73-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="f1b73-113">部分配置</span><span class="sxs-lookup"><span data-stu-id="f1b73-113">Partial Configurations</span></span> | [<span data-ttu-id="f1b73-114">文档</span><span class="sxs-lookup"><span data-stu-id="f1b73-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="f1b73-115">复合资源</span><span class="sxs-lookup"><span data-stu-id="f1b73-115">Composite Resources</span></span> | [<span data-ttu-id="f1b73-116">文档</span><span class="sxs-lookup"><span data-stu-id="f1b73-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="f1b73-117">了解每种方法的影响</span><span class="sxs-lookup"><span data-stu-id="f1b73-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="f1b73-118">这些解决方案中的任何一个都可用于管理服务器部署的结果。</span><span class="sxs-lookup"><span data-stu-id="f1b73-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="f1b73-119">但是，使用每种方法的影响存在显著差异。</span><span class="sxs-lookup"><span data-stu-id="f1b73-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="f1b73-120">部分配置</span><span class="sxs-lookup"><span data-stu-id="f1b73-120">Partial Configurations</span></span>

<span data-ttu-id="f1b73-121">使用部分配置时，将本地 Configuration Manager 配置为独立管理多个配置。</span><span class="sxs-lookup"><span data-stu-id="f1b73-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="f1b73-122">独立编译配置，然后将其分配给节点。</span><span class="sxs-lookup"><span data-stu-id="f1b73-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="f1b73-123">这需要提前使用每个配置的名称配置 LCM。</span><span class="sxs-lookup"><span data-stu-id="f1b73-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="f1b73-125">部分配置提供两个或以上完全控制服务器配置的团队，通常没有通信或协作的权益。</span><span class="sxs-lookup"><span data-stu-id="f1b73-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="f1b73-126">客户提供的反馈表明，这可能导致资源冲突、无意覆盖，并最终导致资产的真实配置控制丢失。</span><span class="sxs-lookup"><span data-stu-id="f1b73-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="f1b73-127">除此之外，客户还提供了反馈，在使用此模型时，每个控制团队的配置更改都不太可能通过发布管道进行全面测试，从而导致生产中出现意外结果。</span><span class="sxs-lookup"><span data-stu-id="f1b73-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="f1b73-128">使用单个管道评估发布到服务器的所有更改至关重要。</span><span class="sxs-lookup"><span data-stu-id="f1b73-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="f1b73-129">在下图中，团队 B 将其部分配置发布到团队 A，然后团队 A 针对应用了两种配置的服务器运行测试。</span><span class="sxs-lookup"><span data-stu-id="f1b73-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="f1b73-130">在此模型中，只有一个机构有权在生产中进行更改。</span><span class="sxs-lookup"><span data-stu-id="f1b73-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="f1b73-132">团队 B 需要进行更改时，他们应针对团队 A 的源代码管理环境提交拉取请求。</span><span class="sxs-lookup"><span data-stu-id="f1b73-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="f1b73-133">若确信更改不会导致服务器托管的应用程序或服务出现错误，则团队 A 将使用测试自动化审阅更改并将其发布到生产中。</span><span class="sxs-lookup"><span data-stu-id="f1b73-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="f1b73-134">复合资源</span><span class="sxs-lookup"><span data-stu-id="f1b73-134">Composite Resources</span></span>

<span data-ttu-id="f1b73-135">复合资源只是作为资源打包的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="f1b73-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="f1b73-136">配置 LCM 以接受复合资源没有特殊要求。</span><span class="sxs-lookup"><span data-stu-id="f1b73-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="f1b73-137">在新配置中使用资源，在一个 MOF 文件中生成单个编译结果。</span><span class="sxs-lookup"><span data-stu-id="f1b73-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="f1b73-139">复合资源有两种常见方案。</span><span class="sxs-lookup"><span data-stu-id="f1b73-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="f1b73-140">第一个方案是降低复杂性和抽象独特概念。</span><span class="sxs-lookup"><span data-stu-id="f1b73-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="f1b73-141">第二个方案是允许为应用程序团队打包基线，以便在所有测试通过后通过其发布管道将其安全地部署到生产。</span><span class="sxs-lookup"><span data-stu-id="f1b73-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="f1b73-142">复合资源在构建操作成熟度的同时使用管道促进组合和协作</span><span class="sxs-lookup"><span data-stu-id="f1b73-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="f1b73-143">你可能已在使用复合资源却没有意识到这一点。</span><span class="sxs-lookup"><span data-stu-id="f1b73-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="f1b73-144">ServiceSet 就是一个示例。</span><span class="sxs-lookup"><span data-stu-id="f1b73-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="f1b73-145">此资源管理多个 Windows 服务的状态，而无需单独列出它们。</span><span class="sxs-lookup"><span data-stu-id="f1b73-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="f1b73-146">Name 属性接受一个字符串数组，以提供每个服务的名称。</span><span class="sxs-lookup"><span data-stu-id="f1b73-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="f1b73-147">编译配置时，MOF 将包含传递给 ServiceSet 的每个名称的唯一服务部分。</span><span class="sxs-lookup"><span data-stu-id="f1b73-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="f1b73-148">组织可能具有应安装在每台服务器上的“代理”或“中间件”。</span><span class="sxs-lookup"><span data-stu-id="f1b73-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="f1b73-149">复合资源是管理任何此类工具和实用程序的依赖关系、设置和配置的最佳答案。</span><span class="sxs-lookup"><span data-stu-id="f1b73-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="f1b73-150">负责跨多个服务器的解决方案的人员或团队对包含其要求的配置进行编写。</span><span class="sxs-lookup"><span data-stu-id="f1b73-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="f1b73-151">接下来，使用复合资源文档中提供的指令将配置打包为复合资源。</span><span class="sxs-lookup"><span data-stu-id="f1b73-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="f1b73-152">最后，应将新的复合资源发布到诸如文件共享或 NuGet 源之类的位置，在此处应用程序团队可在其配置中使用它。</span><span class="sxs-lookup"><span data-stu-id="f1b73-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="f1b73-153">每次团队发布新版本时，他们都会在模块清单中为其复合资源递增版本号。</span><span class="sxs-lookup"><span data-stu-id="f1b73-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="f1b73-154">应用程序团队将复合资源包含在他们为管理应用程序依赖性而创建的配置中。</span><span class="sxs-lookup"><span data-stu-id="f1b73-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="f1b73-155">当操作/安全团队发布其资源的新版本时，他们会通知应用程序团队有新的更改。</span><span class="sxs-lookup"><span data-stu-id="f1b73-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="f1b73-156">应用程序团队可能会触发发布到生产，其中唯一的变化是基线。</span><span class="sxs-lookup"><span data-stu-id="f1b73-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="f1b73-157">但是，这提供了在服务中断风险之前评估对应用程序的影响的机会。</span><span class="sxs-lookup"><span data-stu-id="f1b73-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="f1b73-158">注 - 关于使用复合资源的反馈包括批评，即进行更改需要编译和发布新 MOF。</span><span class="sxs-lookup"><span data-stu-id="f1b73-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="f1b73-159">这是设计使然。</span><span class="sxs-lookup"><span data-stu-id="f1b73-159">This is by design.</span></span>
<span data-ttu-id="f1b73-160">每个新配置版本都应包含对每个资源的特定版本的静态引用，并且应在到达生产服务器节点之前通过测试进行验证。</span><span class="sxs-lookup"><span data-stu-id="f1b73-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="f1b73-161">从源代码管理中测试和发布更改的过程创建了一个安全的环境，用于在小型但频繁的批处理中发布更改。</span><span class="sxs-lookup"><span data-stu-id="f1b73-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="f1b73-162">有关使用发布管道管理核心基础结构的详细信息，请参阅白皮书：[发布管道模型](../further-reading/whitepapers.md)。</span><span class="sxs-lookup"><span data-stu-id="f1b73-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
