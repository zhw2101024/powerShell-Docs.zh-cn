---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 使用 Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803406"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="d1b81-103">使用 Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="d1b81-103">Using Import-DSCResource</span></span>

<span data-ttu-id="d1b81-104">`Import-DScResource` 是只能在配置脚本块内使用的动态关键字。</span><span class="sxs-lookup"><span data-stu-id="d1b81-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="d1b81-105">`Import-DSCResource`关键字来导入你的配置中所需的任何资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="d1b81-106">下的资源`$pshome`将自动导入它仍被视为显式导入中使用的所有资源的最佳做法，但您[配置](Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b81-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="d1b81-107">语法`Import-DSCResource`如下所示。</span><span class="sxs-lookup"><span data-stu-id="d1b81-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="d1b81-108">按名称指定模块，时，需要列出每个新行上。</span><span class="sxs-lookup"><span data-stu-id="d1b81-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="d1b81-109">参数</span><span class="sxs-lookup"><span data-stu-id="d1b81-109">Parameter</span></span>  |<span data-ttu-id="d1b81-110">说明</span><span class="sxs-lookup"><span data-stu-id="d1b81-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="d1b81-111">必须导入 DSC 资源名称。</span><span class="sxs-lookup"><span data-stu-id="d1b81-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="d1b81-112">如果指定模块名称，该命令将搜索在此模块中; 这些 DSC 资源否则该命令在所有 DSC 资源路径中搜索的 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="d1b81-113">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d1b81-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="d1b81-114">模块名称或模块规范。</span><span class="sxs-lookup"><span data-stu-id="d1b81-114">The module name, or module specification.</span></span>  <span data-ttu-id="d1b81-115">如果指定要从模块导入的资源，该命令将尝试导入的资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="d1b81-116">如果指定的模块仅，命令将导入模块中的所有 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="d1b81-117">在配置的示例： 使用导入-DSCResource</span><span class="sxs-lookup"><span data-stu-id="d1b81-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="d1b81-118">不支持在同一命令中指定资源名称和模块名称的多个值。</span><span class="sxs-lookup"><span data-stu-id="d1b81-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="d1b81-119">它可以具有相同的资源存在多个模块中的情况下，从哪些模块加载哪些资源有关的非确定性行为。</span><span class="sxs-lookup"><span data-stu-id="d1b81-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="d1b81-120">以下命令将导致错误在编译过程。</span><span class="sxs-lookup"><span data-stu-id="d1b81-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="d1b81-121">使用仅 Name 参数时要考虑的事项：</span><span class="sxs-lookup"><span data-stu-id="d1b81-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="d1b81-122">它是资源密集型操作具体取决于计算机上安装的模块数量。</span><span class="sxs-lookup"><span data-stu-id="d1b81-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="d1b81-123">它将加载找到具有给定名称的第一个资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="d1b81-124">在这种情况中的多个具有相同名称安装资源，它可以加载错误的资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="d1b81-125">建议的用法是指定`–ModuleName`与`-Name`参数，如下所述。</span><span class="sxs-lookup"><span data-stu-id="d1b81-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="d1b81-126">这种用法具有以下优势：</span><span class="sxs-lookup"><span data-stu-id="d1b81-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="d1b81-127">它可减少性能造成影响限制搜索范围为指定的资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="d1b81-128">它显式定义的模块定义的资源，确保加载正确的资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="d1b81-129">在 PowerShell 5.0 中，DSC 资源可以拥有多个版本，并且这些版本可以并行安装在计算机上。</span><span class="sxs-lookup"><span data-stu-id="d1b81-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="d1b81-130">这是通过将多个版本的资源模块包含在同一个模块文件夹中实现的。</span><span class="sxs-lookup"><span data-stu-id="d1b81-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="d1b81-131">有关详细信息，请参阅[使用具有多个版本的资源](sxsresource.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b81-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="d1b81-132">使用导入 DSCResource 的 Intellisense</span><span class="sxs-lookup"><span data-stu-id="d1b81-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="d1b81-133">在创作时在 ISE 中的 DSC 配置，PowerShell 提供 IntelliSence 资源和资源属性。</span><span class="sxs-lookup"><span data-stu-id="d1b81-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="d1b81-134">在资源定义`$pshome`会自动加载模块路径。</span><span class="sxs-lookup"><span data-stu-id="d1b81-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="d1b81-135">导入使用的资源时`Import-DSCResource`关键字指定的资源定义添加和 Intellisense 扩展以包含导入的资源的架构。</span><span class="sxs-lookup"><span data-stu-id="d1b81-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![资源的 Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="d1b81-137">从 PowerShell 5.0 开始，tab 自动补全已添加到 ISE 有关 DSC 资源及其属性。</span><span class="sxs-lookup"><span data-stu-id="d1b81-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="d1b81-138">有关详细信息，请参阅[资源](../resources/resources.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b81-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="d1b81-139">在编译配置时，PowerShell 将使用导入的资源定义来验证配置中的所有资源块。</span><span class="sxs-lookup"><span data-stu-id="d1b81-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="d1b81-140">使用资源的架构定义的以下规则，验证每个资源块。</span><span class="sxs-lookup"><span data-stu-id="d1b81-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="d1b81-141">使用仅在架构中定义的属性。</span><span class="sxs-lookup"><span data-stu-id="d1b81-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="d1b81-142">每个属性的数据类型正确。</span><span class="sxs-lookup"><span data-stu-id="d1b81-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="d1b81-143">指定密钥属性。</span><span class="sxs-lookup"><span data-stu-id="d1b81-143">Keys properties are specified.</span></span>
- <span data-ttu-id="d1b81-144">不使用任何只读属性。</span><span class="sxs-lookup"><span data-stu-id="d1b81-144">No read-only property is used.</span></span>
- <span data-ttu-id="d1b81-145">验证的值将类型映射。</span><span class="sxs-lookup"><span data-stu-id="d1b81-145">Validation on value maps types.</span></span>

<span data-ttu-id="d1b81-146">请考虑以下配置：</span><span class="sxs-lookup"><span data-stu-id="d1b81-146">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="d1b81-147">编译此配置会导致错误。</span><span class="sxs-lookup"><span data-stu-id="d1b81-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="d1b81-148">Intellisense 和架构验证，可以在运行时避免复杂情况分析和编译时间，在捕获更多的错误。</span><span class="sxs-lookup"><span data-stu-id="d1b81-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="d1b81-149">每个 DSC 资源可以具有一个名称，和一个**FriendlyName**由资源的架构定义。</span><span class="sxs-lookup"><span data-stu-id="d1b81-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="d1b81-150">以下是"MSFT_ServiceResource.shema.mof"的前两行。</span><span class="sxs-lookup"><span data-stu-id="d1b81-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="d1b81-151">当在配置中使用此资源，可以指定**MSFT_ServiceResource**或**服务**。</span><span class="sxs-lookup"><span data-stu-id="d1b81-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="d1b81-152">PowerShell v4 和 v5 差异</span><span class="sxs-lookup"><span data-stu-id="d1b81-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="d1b81-153">有多个差异在 PowerShell 4.0 vs 中创作配置时，将显示。PowerShell 5.0 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="d1b81-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="d1b81-154">本部分将突出显示差异，您会看到与本文相关。</span><span class="sxs-lookup"><span data-stu-id="d1b81-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="d1b81-155">多个资源版本</span><span class="sxs-lookup"><span data-stu-id="d1b81-155">Multiple Resource Versions</span></span>

<span data-ttu-id="d1b81-156">在 PowerShell 4.0 中，不支持安装和使用的资源并排显示多个版本。</span><span class="sxs-lookup"><span data-stu-id="d1b81-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="d1b81-157">如果你注意到问题的资源导入你的配置，请确保只有一个版本安装的资源。</span><span class="sxs-lookup"><span data-stu-id="d1b81-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="d1b81-158">在下面的两个版本的映像**xPSDesiredStateConfiguration**安装模块。</span><span class="sxs-lookup"><span data-stu-id="d1b81-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![修复了多个资源版本](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="d1b81-160">将所需的模块版本的内容复制到模块目录的顶层。</span><span class="sxs-lookup"><span data-stu-id="d1b81-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![修复了多个资源版本](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="d1b81-162">资源位置</span><span class="sxs-lookup"><span data-stu-id="d1b81-162">Resource location</span></span>

<span data-ttu-id="d1b81-163">你的资源时创作和编译配置，可以存储在指定的任何目录中您[PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)。</span><span class="sxs-lookup"><span data-stu-id="d1b81-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="d1b81-164">在 PowerShell 4.0 中，LCM 将要求要存储在"程序 Files\WindowsPowerShell\Modules"下的所有 DSC 资源模块或`$pshome\Modules`。</span><span class="sxs-lookup"><span data-stu-id="d1b81-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="d1b81-165">从 PowerShell 5.0 开始，此要求已被删除，并且可以指定任何目录中存储资源模块`PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="d1b81-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1b81-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1b81-166">See also</span></span>

- [<span data-ttu-id="d1b81-167">资源</span><span class="sxs-lookup"><span data-stu-id="d1b81-167">Resources</span></span>](../resources/resources.md)
