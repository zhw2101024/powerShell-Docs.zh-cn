---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 使用 Import-DSCResource
ms.openlocfilehash: f6c1260bac7d4c545f5a6bc4c098ca90ebb186b5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954054"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="ef8d4-103">使用 Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="ef8d4-103">Using Import-DSCResource</span></span>

<span data-ttu-id="ef8d4-104">`Import-DScResource` 是只能在配置脚本块内使用的动态关键字。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="ef8d4-105">用于导入配置中所需的任何资源的 `Import-DSCResource` 关键字。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="ef8d4-106">`$pshome` 下的资源是自动导入的，但显式导入[配置](Configurations.md)中使用的所有资源仍被视为是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="ef8d4-107">`Import-DSCResource` 的语法如下所示。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="ef8d4-108">按名称指定模块时，要求在新行中列出每个模块。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|<span data-ttu-id="ef8d4-109">参数</span><span class="sxs-lookup"><span data-stu-id="ef8d4-109">Parameter</span></span>  |<span data-ttu-id="ef8d4-110">说明</span><span class="sxs-lookup"><span data-stu-id="ef8d4-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="ef8d4-111">必须导入的 DSC 资源名称。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="ef8d4-112">如果指定了模块名称，命令将在该模块中搜索这些 DSC 资源；否则，命令将在所有 DSC 资源路径中搜索 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="ef8d4-113">支持使用通配符。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="ef8d4-114">模块名称或模块规范。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-114">The module name, or module specification.</span></span>  <span data-ttu-id="ef8d4-115">如果指定要从模块导入的资源，该命令将尝试只导入这些资源。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="ef8d4-116">如果仅指定模块，则命令将导入模块中的所有 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|
|`-ModuleVersion`|<span data-ttu-id="ef8d4-117">从 PowerShell 5.0 开始，可以指定配置应使用的模块版本。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-117">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="ef8d4-118">有关详细信息，请参阅[导入已安装资源的特定版本](sxsresource.md)。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-118">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="ef8d4-119">例如：在配置中使用 Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="ef8d4-119">Example: Use Import-DSCResource within a configuration</span></span>

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
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="ef8d4-120">不支持在同一命令中为资源名称和模块名称指定多个值。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-120">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="ef8d4-121">当相同的资源存在于多个模块中时，可能会存在从哪个模块加载哪个资源的非确定性行为。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-121">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="ef8d4-122">下面的命令将在编译期间导致错误。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-122">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="ef8d4-123">仅使用 Name 参数时要考虑的事项：</span><span class="sxs-lookup"><span data-stu-id="ef8d4-123">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="ef8d4-124">它是一种资源密集型操作，具体取决于安装在计算机上的模块数量。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-124">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="ef8d4-125">它将加载使用给定名称找到的第一个资源。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-125">It will load the first resource found with the given name.</span></span> <span data-ttu-id="ef8d4-126">如果安装了多个具有相同名称的资源，则可能加载错误资源。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-126">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="ef8d4-127">建议的用法是使用 `-Name` 参数指定 `–ModuleName`，如下所述。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-127">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="ef8d4-128">这种用法具有以下优势：</span><span class="sxs-lookup"><span data-stu-id="ef8d4-128">This usage has the following benefits:</span></span>

- <span data-ttu-id="ef8d4-129">它通过限制指定资源的搜索范围来降低性能影响。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-129">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="ef8d4-130">它显式定义定义资源的模块，以确保加载正确资源。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-130">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="ef8d4-131">在 PowerShell 5.0 中，DSC 资源可以拥有多个版本，并且这些版本可以并行安装在计算机上。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-131">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="ef8d4-132">这是通过将多个版本的资源模块包含在同一个模块文件夹中实现的。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-132">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="ef8d4-133">有关详细信息，请参阅[使用具有多个版本的资源](sxsresource.md)。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-133">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="ef8d4-134">Intellisense 与 Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="ef8d4-134">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="ef8d4-135">在 ISE 中编写 DSC 配置时，PowerShell 为资源和资源属性提供 IntelliSence。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-135">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="ef8d4-136">`$pshome` 模块路径下的资源定义将自动加载。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-136">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="ef8d4-137">当使用 `Import-DSCResource` 关键字导入资源时，将添加指定的资源定义，并扩展 Intellisense 以包含导入的资源架构。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-137">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![资源 Intellisense](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="ef8d4-139">从 PowerShell 5.0 开始，已将 Tab 自动补全添加到 DSC 资源及其属性的 ISE 中。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-139">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="ef8d4-140">有关详细信息，请参阅[资源](../resources/resources.md)。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-140">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="ef8d4-141">在编译配置时，PowerShell 使用导入的资源定义来验证配置中的所有资源块。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-141">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="ef8d4-142">根据以下规则，使用资源的架构定义对每个资源块进行验证。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-142">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="ef8d4-143">仅使用架构中定义的属性。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-143">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="ef8d4-144">每个属性的数据类型均正确无误。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-144">The data types for each property are correct.</span></span>
- <span data-ttu-id="ef8d4-145">指定键属性。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-145">Keys properties are specified.</span></span>
- <span data-ttu-id="ef8d4-146">不使用只读属性。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-146">No read-only property is used.</span></span>
- <span data-ttu-id="ef8d4-147">验证值映射类型。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-147">Validation on value maps types.</span></span>

<span data-ttu-id="ef8d4-148">请考虑以下配置：</span><span class="sxs-lookup"><span data-stu-id="ef8d4-148">Consider the following configuration:</span></span>

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
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="ef8d4-149">编译此配置会导致错误。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-149">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="ef8d4-150">Intellisense 和架构验证允许在解析和编译期间捕获更多错误，从而避免了运行时的复杂性。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-150">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="ef8d4-151">每个 DSC 资源都可以有一个名称，以及一个由资源架构定义的 FriendlyName  。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-151">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="ef8d4-152">下面是“MSFT_ServiceResource.shema.mof”的前两行。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-152">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="ef8d4-153">在配置中使用此资源时，可以指定 MSFT_ServiceResource  或 Service  。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-153">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="ef8d4-154">PowerShell v4 和 v5 差异</span><span class="sxs-lookup"><span data-stu-id="ef8d4-154">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="ef8d4-155">你会发现，在 PowerShell 4.0 中编写配置与在 PowerShell 5.0 及更高版本中编写配置有许多不同之处。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-155">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="ef8d4-156">本节将重点介绍你所看到的与本文相关的差异。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-156">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="ef8d4-157">多个资源版本</span><span class="sxs-lookup"><span data-stu-id="ef8d4-157">Multiple Resource Versions</span></span>

<span data-ttu-id="ef8d4-158">PowerShell 4.0 不支持同时安装和使用多个资源版本。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-158">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="ef8d4-159">如果注意到将资源导入配置时存在问题，请确保只安装一个资源版本。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-159">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="ef8d4-160">在下图中，安装了两个版本的 xPSDesiredStateConfiguration  模块。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-160">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![修复了多个资源版本](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="ef8d4-162">将所需模块版本的内容复制到模块目录的顶层。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-162">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![修复了多个资源版本](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="ef8d4-164">资源位置</span><span class="sxs-lookup"><span data-stu-id="ef8d4-164">Resource location</span></span>

<span data-ttu-id="ef8d4-165">在编写和编译配置时，资源可以存储在 [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path) 指定的任何目录中。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-165">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="ef8d4-166">在 PowerShell 4.0 中，LCM 要求所有 DSC 资源模块都存储在“Program Files\WindowsPowerShell\Modules”或 `$pshome\Modules` 下。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-166">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="ef8d4-167">从 PowerShell 5.0 开始，此要求已被删除，资源模块可以存储在 `PSModulePath` 指定的任何目录中。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-167">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="ef8d4-168">已添加 ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="ef8d4-168">ModuleVersion added</span></span>

<span data-ttu-id="ef8d4-169">从 PowerShell 5.0 开始，使用 `-ModuleVersion` 参数可以指定在配置中使用的模块版本。</span><span class="sxs-lookup"><span data-stu-id="ef8d4-169">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef8d4-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef8d4-170">See also</span></span>

- [<span data-ttu-id="ef8d4-171">资源</span><span class="sxs-lookup"><span data-stu-id="ef8d4-171">Resources</span></span>](../resources/resources.md)
