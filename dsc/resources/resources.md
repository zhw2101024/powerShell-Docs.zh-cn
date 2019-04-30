---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: DSC 资源
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076614"
---
# <a name="dsc-resources"></a><span data-ttu-id="67ca7-103">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-103">DSC Resources</span></span>

><span data-ttu-id="67ca7-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="67ca7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="67ca7-105">Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。</span><span class="sxs-lookup"><span data-stu-id="67ca7-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="67ca7-106">资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。</span><span class="sxs-lookup"><span data-stu-id="67ca7-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="67ca7-107">资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。</span><span class="sxs-lookup"><span data-stu-id="67ca7-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="67ca7-108">资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。</span><span class="sxs-lookup"><span data-stu-id="67ca7-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="67ca7-109">每个资源都具有用于确定使用[配置](../configurations/configurations.md)中的资源所需的语法的 \*架构。</span><span class="sxs-lookup"><span data-stu-id="67ca7-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="67ca7-110">可以按以下方式定义资源的架构：</span><span class="sxs-lookup"><span data-stu-id="67ca7-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="67ca7-111">“Schema.Mof”文件：大多数资源使用[托管对象格式](/windows/desktop/wmisdk/managed-object-format--mof-)定义它们在“schema.mof”文件中的架构。</span><span class="sxs-lookup"><span data-stu-id="67ca7-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="67ca7-112">“\<Resource Name\>.schema.psm1”文件：[复合资源](../configurations/compositeConfigs.md)使用[参数块](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)定义它们在“<ResourceName>.schema.psm1”文件中的架构。</span><span class="sxs-lookup"><span data-stu-id="67ca7-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="67ca7-113">“\<Resource Name\>.psm1”文件：基于类的 DSC 资源定义它们在类定义中的架构。</span><span class="sxs-lookup"><span data-stu-id="67ca7-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="67ca7-114">语法项表示为类属性。</span><span class="sxs-lookup"><span data-stu-id="67ca7-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="67ca7-115">有关详细信息，请参阅 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。</span><span class="sxs-lookup"><span data-stu-id="67ca7-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="67ca7-116">若要检索 DSC 资源的语法，请将 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 与 `-Syntax` 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="67ca7-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="67ca7-117">此用法类似于将 [Get-Command](/powershell/module/microsoft.powershell.core/get-command) 与 `-Syntax` 参数一起使用以获取 cmdlet 语法。</span><span class="sxs-lookup"><span data-stu-id="67ca7-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="67ca7-118">所看到的输出将显示用于指定资源的资源块的模板。</span><span class="sxs-lookup"><span data-stu-id="67ca7-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="67ca7-119">所看到的输出应类似于以下输出，尽管此资源的语法在将来可能会发生改变也是如此。</span><span class="sxs-lookup"><span data-stu-id="67ca7-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="67ca7-120">类似于 cmdlet 语法，方括号中所示的键是可选的。</span><span class="sxs-lookup"><span data-stu-id="67ca7-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="67ca7-121">类型指定每个键所需的数据类型。</span><span class="sxs-lookup"><span data-stu-id="67ca7-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="67ca7-122">确保键是可选的，因为它默认为“Present”。</span><span class="sxs-lookup"><span data-stu-id="67ca7-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="67ca7-123">在配置内，Service 资源块可能如下所示以确保 Spooler 服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="67ca7-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="67ca7-124">在使用配置中的资源之前，必须使用 [Import-DSCResource](../configurations/import-dscresource.md) 导入该资源。</span><span class="sxs-lookup"><span data-stu-id="67ca7-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="67ca7-125">配置可以包含同一资源类型的多个实例。</span><span class="sxs-lookup"><span data-stu-id="67ca7-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="67ca7-126">每个实例必须具有唯一名称。</span><span class="sxs-lookup"><span data-stu-id="67ca7-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="67ca7-127">在以下示例中，添加了第二个 Service 资源块以配置“DHCP”服务。</span><span class="sxs-lookup"><span data-stu-id="67ca7-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="67ca7-128">从 PowerShell 5.0 开始，为 DSC 添加了 Intellisense。</span><span class="sxs-lookup"><span data-stu-id="67ca7-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="67ca7-129">借助这一新功能，可以使用 \<TAB\> 和 \<Ctrl+Space\> 自动补全键名称。</span><span class="sxs-lookup"><span data-stu-id="67ca7-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![资源 Tab 自动补全](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="67ca7-131">内置资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-131">Built-in resources</span></span>

<span data-ttu-id="67ca7-132">除了社区资源之外，还有适用于 Windows 的内置资源、适用于 Linux 的资源和适用于跨节点依赖项的资源。</span><span class="sxs-lookup"><span data-stu-id="67ca7-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="67ca7-133">可以使用上述步骤确定这些资源的语法以及如何使用这些资源。</span><span class="sxs-lookup"><span data-stu-id="67ca7-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="67ca7-134">已在“参考”下存档提供这些资源的页面。</span><span class="sxs-lookup"><span data-stu-id="67ca7-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="67ca7-135">Windows 内置资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-135">Windows built-in resources</span></span>

* [<span data-ttu-id="67ca7-136">存档资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="67ca7-137">环境资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="67ca7-138">文件资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="67ca7-139">组资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="67ca7-140">GroupSet 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="67ca7-141">日志资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="67ca7-142">包资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="67ca7-143">ProcessSet 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="67ca7-144">注册表资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="67ca7-145">脚本资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="67ca7-146">服务资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="67ca7-147">ServiceSet 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="67ca7-148">用户资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="67ca7-149">WindowsFeature 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="67ca7-150">WindowsFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="67ca7-151">WindowsOptionalFeature 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="67ca7-152">WindowsOptionalFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="67ca7-153">WindowsPackageCabResource 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="67ca7-154">WindowsProcess 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="67ca7-155">[跨节点依赖项](../configurations/crossNodeDependencies.md)资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="67ca7-156">WaitForAll 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="67ca7-157">WaitForSome 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="67ca7-158">WaitForAny 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="67ca7-159">包管理资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-159">Package Management resources</span></span>

* [<span data-ttu-id="67ca7-160">PackageManagement 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="67ca7-161">PackageManagementSource 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="67ca7-162">Linux 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-162">Linux resources</span></span>

* [<span data-ttu-id="67ca7-163">Linux 存档资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="67ca7-164">Linux 环境资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="67ca7-165">Linux FileLine 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="67ca7-166">Linux 文件资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="67ca7-167">Linux 组资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="67ca7-168">Linux 包资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="67ca7-169">Linux 脚本资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="67ca7-170">Linux 服务资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="67ca7-171">Linux SshAuthorizedKeys 资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="67ca7-172">Linux 用户资源</span><span class="sxs-lookup"><span data-stu-id="67ca7-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
