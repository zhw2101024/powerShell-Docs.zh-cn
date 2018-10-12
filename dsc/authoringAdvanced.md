# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a><span data-ttu-id="76ce1-101">用于组合和协作的高级 DSC 创作</span><span class="sxs-lookup"><span data-stu-id="76ce1-101">Advanced DSC Authoring for Composition and Collaboration</span></span>

<span data-ttu-id="76ce1-102">本文介绍了可用于组合配置和资源的方法类型。</span><span class="sxs-lookup"><span data-stu-id="76ce1-102">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="76ce1-103">每种方案的目标都是相同的，即在首选多个配置时降低复杂性以达到服务器部署最终状态。</span><span class="sxs-lookup"><span data-stu-id="76ce1-103">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="76ce1-104">为服务器部署结果做出贡献的多个团队可作为该方面的一个示例，例如维护应用程序状态的应用程序所有者和释放安全基线更改的中央团队。</span><span class="sxs-lookup"><span data-stu-id="76ce1-104">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="76ce1-105">此处详细介绍了每种方法的细微差别，包括收益和风险。</span><span class="sxs-lookup"><span data-stu-id="76ce1-105">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![管道](images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="76ce1-107">协同创作技术的类型</span><span class="sxs-lookup"><span data-stu-id="76ce1-107">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="76ce1-108">本地 Configuration Manager 内置两个解决方案来启用此概念：</span><span class="sxs-lookup"><span data-stu-id="76ce1-108">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="76ce1-109">概念</span><span class="sxs-lookup"><span data-stu-id="76ce1-109">Concept</span></span> | <span data-ttu-id="76ce1-110">详细信息</span><span class="sxs-lookup"><span data-stu-id="76ce1-110">Detailed Information</span></span>
|-|-
| <span data-ttu-id="76ce1-111">部分配置</span><span class="sxs-lookup"><span data-stu-id="76ce1-111">Partial Configurations</span></span> | [<span data-ttu-id="76ce1-112">文档</span><span class="sxs-lookup"><span data-stu-id="76ce1-112">Documentation</span></span>](partialconfigs.md)
| <span data-ttu-id="76ce1-113">复合资源</span><span class="sxs-lookup"><span data-stu-id="76ce1-113">Composite Resources</span></span> | [<span data-ttu-id="76ce1-114">文档</span><span class="sxs-lookup"><span data-stu-id="76ce1-114">Documentation</span></span>](authoringresourcecomposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="76ce1-115">了解每种方法的影响</span><span class="sxs-lookup"><span data-stu-id="76ce1-115">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="76ce1-116">这些解决方案中的任何一个都可用于管理服务器部署的结果。</span><span class="sxs-lookup"><span data-stu-id="76ce1-116">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="76ce1-117">但是，使用每种方法的影响存在显著差异。</span><span class="sxs-lookup"><span data-stu-id="76ce1-117">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="76ce1-118">部分配置</span><span class="sxs-lookup"><span data-stu-id="76ce1-118">Partial Configurations</span></span>

<span data-ttu-id="76ce1-119">使用部分配置时，将本地 Configuration Manager 配置为独立管理多个配置。</span><span class="sxs-lookup"><span data-stu-id="76ce1-119">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="76ce1-120">独立编译配置，然后将其分配给节点。</span><span class="sxs-lookup"><span data-stu-id="76ce1-120">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="76ce1-121">这需要提前使用每个配置的名称配置 LCM。</span><span class="sxs-lookup"><span data-stu-id="76ce1-121">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](images/PartialConfiguration.jpg)

<span data-ttu-id="76ce1-123">部分配置提供两个或以上完全控制服务器配置的团队，通常没有通信或协作的权益。</span><span class="sxs-lookup"><span data-stu-id="76ce1-123">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="76ce1-124">客户提供的反馈表明，这可能导致资源冲突、无意覆盖，并最终导致资产的真实配置控制丢失。</span><span class="sxs-lookup"><span data-stu-id="76ce1-124">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="76ce1-125">除此之外，客户还提供了反馈，在使用此模型时，每个控制团队的配置更改都不太可能通过发布管道进行全面测试，从而导致生产中出现意外结果。</span><span class="sxs-lookup"><span data-stu-id="76ce1-125">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="76ce1-126">使用单个管道评估发布到服务器的所有更改至关重要。</span><span class="sxs-lookup"><span data-stu-id="76ce1-126">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="76ce1-127">在下图中，团队 B 将其部分配置发布到团队 A，然后团队 A 针对应用了两种配置的服务器运行测试。</span><span class="sxs-lookup"><span data-stu-id="76ce1-127">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="76ce1-128">在此模型中，只有一个机构有权在生产中进行更改。</span><span class="sxs-lookup"><span data-stu-id="76ce1-128">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](images/PartialSinglePipeline.jpg)

<span data-ttu-id="76ce1-130">团队 B 需要进行更改时，他们应针对团队 A 的源代码管理环境提交拉取请求。</span><span class="sxs-lookup"><span data-stu-id="76ce1-130">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="76ce1-131">若确信更改不会导致服务器托管的应用程序或服务出现错误，则团队 A 将使用测试自动化审阅更改并将其发布到生产中。</span><span class="sxs-lookup"><span data-stu-id="76ce1-131">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="76ce1-132">复合资源</span><span class="sxs-lookup"><span data-stu-id="76ce1-132">Composite Resources</span></span>

<span data-ttu-id="76ce1-133">复合资源只是作为资源打包的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="76ce1-133">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="76ce1-134">配置 LCM 以接受复合资源没有特殊要求。</span><span class="sxs-lookup"><span data-stu-id="76ce1-134">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="76ce1-135">在新配置中使用资源，在一个 MOF 文件中生成单个编译结果。</span><span class="sxs-lookup"><span data-stu-id="76ce1-135">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](images/CompositeResource.jpg)

<span data-ttu-id="76ce1-137">复合资源有两种常见方案。</span><span class="sxs-lookup"><span data-stu-id="76ce1-137">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="76ce1-138">第一个方案是降低复杂性和抽象独特概念。</span><span class="sxs-lookup"><span data-stu-id="76ce1-138">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="76ce1-139">第二个方案是允许为应用程序团队打包基线，以便在所有测试通过后通过其发布管道将其安全地部署到生产。</span><span class="sxs-lookup"><span data-stu-id="76ce1-139">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

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

<span data-ttu-id="76ce1-140">复合资源在构建操作成熟度的同时使用管道促进组合和协作</span><span class="sxs-lookup"><span data-stu-id="76ce1-140">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="76ce1-141">你可能已在使用复合资源却没有意识到这一点。</span><span class="sxs-lookup"><span data-stu-id="76ce1-141">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="76ce1-142">ServiceSet 就是一个示例。</span><span class="sxs-lookup"><span data-stu-id="76ce1-142">An example is **ServiceSet**.</span></span>
<span data-ttu-id="76ce1-143">此资源管理多个 Windows 服务的状态，而无需单独列出它们。</span><span class="sxs-lookup"><span data-stu-id="76ce1-143">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="76ce1-144">Name 属性接受一个字符串数组，以提供每个服务的名称。</span><span class="sxs-lookup"><span data-stu-id="76ce1-144">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="76ce1-145">编译配置时，MOF 将包含传递给 ServiceSet 的每个名称的唯一服务部分。</span><span class="sxs-lookup"><span data-stu-id="76ce1-145">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="76ce1-146">组织可能具有应安装在每台服务器上的“代理”或“中间件”。</span><span class="sxs-lookup"><span data-stu-id="76ce1-146">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="76ce1-147">复合资源是管理任何此类工具和实用程序的依赖关系、设置和配置的最佳答案。</span><span class="sxs-lookup"><span data-stu-id="76ce1-147">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="76ce1-148">负责跨多个服务器的解决方案的人员或团队对包含其要求的配置进行编写。</span><span class="sxs-lookup"><span data-stu-id="76ce1-148">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="76ce1-149">接下来，使用复合资源文档中提供的指令将配置打包为复合资源。</span><span class="sxs-lookup"><span data-stu-id="76ce1-149">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="76ce1-150">最后，应将新的复合资源发布到诸如文件共享或 NuGet 源之类的位置，在此处应用程序团队可在其配置中使用它。</span><span class="sxs-lookup"><span data-stu-id="76ce1-150">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="76ce1-151">每次团队发布新版本时，他们都会在模块清单中为其复合资源递增版本号。</span><span class="sxs-lookup"><span data-stu-id="76ce1-151">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="76ce1-152">应用程序团队将复合资源包含在他们为管理应用程序依赖性而创建的配置中。</span><span class="sxs-lookup"><span data-stu-id="76ce1-152">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="76ce1-153">当操作/安全团队发布其资源的新版本时，他们会通知应用程序团队有新的更改。</span><span class="sxs-lookup"><span data-stu-id="76ce1-153">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="76ce1-154">应用程序团队可能会触发发布到生产，其中唯一的变化是基线。</span><span class="sxs-lookup"><span data-stu-id="76ce1-154">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="76ce1-155">但是，这提供了在服务中断风险之前评估对应用程序的影响的机会。</span><span class="sxs-lookup"><span data-stu-id="76ce1-155">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="76ce1-156">注 - 关于使用复合资源的反馈包括批评，即进行更改需要编译和发布新 MOF。</span><span class="sxs-lookup"><span data-stu-id="76ce1-156">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="76ce1-157">这是设计使然。</span><span class="sxs-lookup"><span data-stu-id="76ce1-157">This is by design.</span></span>
<span data-ttu-id="76ce1-158">每个新配置版本都应包含对每个资源的特定版本的静态引用，并且应在到达生产服务器节点之前通过测试进行验证。</span><span class="sxs-lookup"><span data-stu-id="76ce1-158">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="76ce1-159">从源代码管理中测试和发布更改的过程创建了一个安全的环境，用于在小型但频繁的批处理中发布更改。</span><span class="sxs-lookup"><span data-stu-id="76ce1-159">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="76ce1-160">有关使用发布管道管理核心基础结构的详细信息，请参阅白皮书：[发布管道模型](http://aka.ms/thereleasepipelinemodel)。</span><span class="sxs-lookup"><span data-stu-id="76ce1-160">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodel).</span></span>
