---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: DSC 资源
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676942"
---
# <a name="dsc-resources"></a><span data-ttu-id="f48b9-103">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-103">DSC Resources</span></span>

><span data-ttu-id="f48b9-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f48b9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f48b9-105">Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。</span><span class="sxs-lookup"><span data-stu-id="f48b9-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="f48b9-106">资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。</span><span class="sxs-lookup"><span data-stu-id="f48b9-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="f48b9-107">资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。</span><span class="sxs-lookup"><span data-stu-id="f48b9-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="f48b9-108">资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。</span><span class="sxs-lookup"><span data-stu-id="f48b9-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="f48b9-109">每个资源都有 \* 确定使用中的资源所需的语法的架构[配置](../configurations/configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="f48b9-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="f48b9-110">可以按以下方式定义资源的架构：</span><span class="sxs-lookup"><span data-stu-id="f48b9-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="f48b9-111">**Schema.Mof**文件：最多的资源定义其*架构*中 schema.mof 文件，请使用[托管对象格式](/windows/desktop/wmisdk/managed-object-format--mof-)。</span><span class="sxs-lookup"><span data-stu-id="f48b9-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="f48b9-112">**'\<资源名称\>。 schema.psm1**文件：[复合资源](../configurations/compositeConfigs.md)定义其*架构*中<ResourceName>。 schema.psm1 文件中使用[参数块](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)。</span><span class="sxs-lookup"><span data-stu-id="f48b9-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="f48b9-113">**'\<资源名称\>.psm1**文件：基于的 DSC 资源定义的类及其*架构*类定义中。</span><span class="sxs-lookup"><span data-stu-id="f48b9-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="f48b9-114">语法项表示为类的属性。</span><span class="sxs-lookup"><span data-stu-id="f48b9-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="f48b9-115">有关详细信息，请参阅[about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。</span><span class="sxs-lookup"><span data-stu-id="f48b9-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="f48b9-116">若要检索的 DSC 资源的语法，请使用[Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 与`-Syntax`参数。</span><span class="sxs-lookup"><span data-stu-id="f48b9-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="f48b9-117">这种用法是使用类似[Get-command](/powershell/module/microsoft.powershell.core/get-command)与`-Syntax`参数，以获取 cmdlet 的语法。</span><span class="sxs-lookup"><span data-stu-id="f48b9-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="f48b9-118">您所看到的输出将显示你指定的资源的资源块中使用的模板。</span><span class="sxs-lookup"><span data-stu-id="f48b9-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="f48b9-119">尽管此资源的语法可能会在将来更改，您所看到的输出应类似于下面的输出。</span><span class="sxs-lookup"><span data-stu-id="f48b9-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="f48b9-120">喜欢的 cmdlet 语法*密钥*方括号中所示，都是可选的。</span><span class="sxs-lookup"><span data-stu-id="f48b9-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="f48b9-121">类型指定每个密钥需要的数据的类型。</span><span class="sxs-lookup"><span data-stu-id="f48b9-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="f48b9-122">**确保**密钥是可选的因为它默认为"Present"。</span><span class="sxs-lookup"><span data-stu-id="f48b9-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="f48b9-123">在配置**服务**资源块可能如下所示向**确保**后台处理程序服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="f48b9-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="f48b9-124">之前在配置中使用的资源，你必须使用导入[Import-dscresource](../configurations/import-dscresource.md)。</span><span class="sxs-lookup"><span data-stu-id="f48b9-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="f48b9-125">配置可以包含相同的资源类型的多个实例。</span><span class="sxs-lookup"><span data-stu-id="f48b9-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="f48b9-126">每个实例必须具有唯一名称。</span><span class="sxs-lookup"><span data-stu-id="f48b9-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="f48b9-127">在以下示例中，第二个**服务**资源块已添加用于配置"DHCP"服务。</span><span class="sxs-lookup"><span data-stu-id="f48b9-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="f48b9-128">从 PowerShell 5.0 开始，intellisense 添加了对 DSC。</span><span class="sxs-lookup"><span data-stu-id="f48b9-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="f48b9-129">这一新功能，可使用\<选项卡\>并\<Ctrl + 空格键\>到自动补全键名。</span><span class="sxs-lookup"><span data-stu-id="f48b9-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![资源 Tab 自动补全](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="f48b9-131">内置资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-131">Built-in resources</span></span>

<span data-ttu-id="f48b9-132">除了社区资源，还有适用于 Windows、 Linux、 资源和资源的跨节点依赖关系内置资源。</span><span class="sxs-lookup"><span data-stu-id="f48b9-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="f48b9-133">可以使用上述步骤以确定这些资源以及如何使用它们的语法。</span><span class="sxs-lookup"><span data-stu-id="f48b9-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="f48b9-134">这些资源提供服务的页面已存档下**引用**。</span><span class="sxs-lookup"><span data-stu-id="f48b9-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="f48b9-135">Windows 内置资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-135">Windows built-in resources</span></span>

* [<span data-ttu-id="f48b9-136">存档资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="f48b9-137">环境资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="f48b9-138">文件资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="f48b9-139">组资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="f48b9-140">GroupSet 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="f48b9-141">日志资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="f48b9-142">包资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="f48b9-143">ProcessSet 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="f48b9-144">注册表资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="f48b9-145">脚本资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="f48b9-146">服务资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="f48b9-147">ServiceSet 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="f48b9-148">用户资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="f48b9-149">WindowsFeature 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="f48b9-150">WindowsFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="f48b9-151">WindowsOptionalFeature 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="f48b9-152">WindowsOptionalFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="f48b9-153">WindowsPackageCabResource Resource</span><span class="sxs-lookup"><span data-stu-id="f48b9-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="f48b9-154">WindowsProcess 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="f48b9-155">[跨节点依赖关系](../configurations/crossNodeDependencies.md)资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="f48b9-156">WaitForAll 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="f48b9-157">WaitForSome 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="f48b9-158">WaitForAny 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="f48b9-159">包管理资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-159">Package Management resources</span></span>

* [<span data-ttu-id="f48b9-160">PackageManagement 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="f48b9-161">PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="f48b9-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="f48b9-162">Linux 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-162">Linux resources</span></span>

* [<span data-ttu-id="f48b9-163">Linux 存档资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="f48b9-164">Linux 环境资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="f48b9-165">Linux FileLine 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="f48b9-166">Linux 文件资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="f48b9-167">Linux 组资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="f48b9-168">Linux 包资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="f48b9-169">Linux 脚本资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="f48b9-170">Linux 服务资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="f48b9-171">Linux SshAuthorizedKeys 资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="f48b9-172">Linux 用户资源</span><span class="sxs-lookup"><span data-stu-id="f48b9-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
