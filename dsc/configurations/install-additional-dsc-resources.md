---
ms.date: 12/12/2018
keywords: dsc，powershell、 资源、 库、 安装程序
title: 安全其他 DSC 资源
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400834"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="35172-103">安全其他 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="35172-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="35172-104">PowerShell Desired State Configuration (DSC) 中包含多个开箱资源。</span><span class="sxs-lookup"><span data-stu-id="35172-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="35172-105">**PSDesiredStateConfiguration**模块包含的所有 OOB DSC 资源的 PowerShell 特定实例上可用。</span><span class="sxs-lookup"><span data-stu-id="35172-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="35172-106">这是在 PowerShell 4.0 和资源的功能的说明中包含的 OOB 资源的列表。</span><span class="sxs-lookup"><span data-stu-id="35172-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="35172-107">这是不完整列表，因为 OOB 资源数已增加每个版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="35172-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="35172-108">资源</span><span class="sxs-lookup"><span data-stu-id="35172-108">Resource</span></span>  |<span data-ttu-id="35172-109">说明</span><span class="sxs-lookup"><span data-stu-id="35172-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="35172-110">**文件**</span><span class="sxs-lookup"><span data-stu-id="35172-110">**File**</span></span>|<span data-ttu-id="35172-111">控制文件和目录的状态。</span><span class="sxs-lookup"><span data-stu-id="35172-111">Controls the state of files and directories.</span></span> <span data-ttu-id="35172-112">将文件从复制**源**到**目标**，然后更新它们时**源**通过比较日期、 校验和和哈希值的更改。</span><span class="sxs-lookup"><span data-stu-id="35172-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="35172-113">**存档**</span><span class="sxs-lookup"><span data-stu-id="35172-113">**Archive**</span></span>|<span data-ttu-id="35172-114">解压缩存档和指定的位置。</span><span class="sxs-lookup"><span data-stu-id="35172-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="35172-115">验证与指定存档**校验和**。</span><span class="sxs-lookup"><span data-stu-id="35172-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="35172-116">**环境**</span><span class="sxs-lookup"><span data-stu-id="35172-116">**Environment**</span></span>|<span data-ttu-id="35172-117">管理的环境变量。</span><span class="sxs-lookup"><span data-stu-id="35172-117">Manages environment variables.</span></span>|
|<span data-ttu-id="35172-118">**组**</span><span class="sxs-lookup"><span data-stu-id="35172-118">**Group**</span></span>|<span data-ttu-id="35172-119">管理本地组并控制组成员身份。</span><span class="sxs-lookup"><span data-stu-id="35172-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="35172-120">**日志**</span><span class="sxs-lookup"><span data-stu-id="35172-120">**Log**</span></span>|<span data-ttu-id="35172-121">写入到消息`Microsoft-Windows-Desired State Configuration/Analytic`事件日志。</span><span class="sxs-lookup"><span data-stu-id="35172-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="35172-122">**包**</span><span class="sxs-lookup"><span data-stu-id="35172-122">**Package**</span></span>|<span data-ttu-id="35172-123">安装或卸载程序包使用**自变量**， **LogPath**， **ReturnCode**，其他设置。</span><span class="sxs-lookup"><span data-stu-id="35172-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="35172-124">**注册表**</span><span class="sxs-lookup"><span data-stu-id="35172-124">**Registry**</span></span>|<span data-ttu-id="35172-125">管理注册表项和值。</span><span class="sxs-lookup"><span data-stu-id="35172-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="35172-126">**脚本**</span><span class="sxs-lookup"><span data-stu-id="35172-126">**Script**</span></span>|<span data-ttu-id="35172-127">可用于设计您自己[get 测试集](../resources/get-test-set.md)脚本块。</span><span class="sxs-lookup"><span data-stu-id="35172-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="35172-128">**服务**</span><span class="sxs-lookup"><span data-stu-id="35172-128">**Service**</span></span>|<span data-ttu-id="35172-129">配置 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="35172-129">Configures Windows services.</span></span>|
|<span data-ttu-id="35172-130">**用户**</span><span class="sxs-lookup"><span data-stu-id="35172-130">**User**</span></span> |<span data-ttu-id="35172-131">管理本地用户和属性。</span><span class="sxs-lookup"><span data-stu-id="35172-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="35172-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="35172-132">**WindowsFeature**</span></span>|<span data-ttu-id="35172-133">管理角色和功能。</span><span class="sxs-lookup"><span data-stu-id="35172-133">Manages roles and features.</span></span>|
|<span data-ttu-id="35172-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="35172-134">**WindowsProcess**</span></span>|<span data-ttu-id="35172-135">配置 Windows 进程。</span><span class="sxs-lookup"><span data-stu-id="35172-135">Configures Windows processes.</span></span>|

<span data-ttu-id="35172-136">OOB 资源允许常见操作的良好起点。</span><span class="sxs-lookup"><span data-stu-id="35172-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="35172-137">如果 OOB 资源不能满足您的需要，可以编写您自己[自定义资源](../resources/authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="35172-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="35172-138">编写自定义资源以解决你的问题之前，您应查找通过大量的已创建由 Microsoft 和 PowerShell 社区的 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="35172-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="35172-139">可以在这种查找 DSC 资源[PowerShell 库](https://www.powershellgallery.com/)并[GitHub](https://github.com/)。</span><span class="sxs-lookup"><span data-stu-id="35172-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="35172-140">此外可以直接从 PowerShell 控制台中使用安装 DSC 资源[PowerShellGet](/powershell/module/powershellget/)。</span><span class="sxs-lookup"><span data-stu-id="35172-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="35172-141">安装 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="35172-141">Installing PowerShellGet</span></span>

<span data-ttu-id="35172-142">若要确定是否已有**PowerShell**获取，或若要获取安装的帮助，请参阅以下指南：[安装 PowerShellGet](/powershell/gallery/installing-psget)</span><span class="sxs-lookup"><span data-stu-id="35172-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="35172-143">查找 DSC 资源使用 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="35172-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="35172-144">一次**PowerShellGet**安装在系统上，您可以找到并安装在中托管的 DSC 资源[PowerShell 库](https://www.powershellgallery.com/)。</span><span class="sxs-lookup"><span data-stu-id="35172-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="35172-145">首先，使用[Find-dscresource](/powershell/module/powershellget/find-dscresource) cmdlet 查找 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="35172-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="35172-146">当你运行`Find-DSCResource`第一次，您将看到以下提示安装"NuGet 提供程序"。</span><span class="sxs-lookup"><span data-stu-id="35172-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="35172-147">后按 y，在"NuGet"提供程序安装，请参阅可从 PowerShell 库安装的 DSC 资源的列表。</span><span class="sxs-lookup"><span data-stu-id="35172-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="35172-148">因为它是非常大，不会显示列表。</span><span class="sxs-lookup"><span data-stu-id="35172-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="35172-149">此外可以指定`-Name`参数使用通配符，或`-Filter`不带通配符来缩小搜索的参数。</span><span class="sxs-lookup"><span data-stu-id="35172-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="35172-150">此示例尝试查找使用通配符的"时区"DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="35172-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35172-151">目前没有中的 bug`Find-DSCResource`可防止在这种使用通配符的 cmdlet`-Name`和`-Filter`参数。</span><span class="sxs-lookup"><span data-stu-id="35172-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="35172-152">下面的第二个示例显示了解决方法使用`Where-Object`。</span><span class="sxs-lookup"><span data-stu-id="35172-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="35172-153">此外可以使用`Where-Object`查找 DSC 资源使用更精细的筛选。</span><span class="sxs-lookup"><span data-stu-id="35172-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="35172-154">此方法将比使用内置的筛选参数。</span><span class="sxs-lookup"><span data-stu-id="35172-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="35172-155">有关筛选的详细信息，请参阅[Where-object](/powershell/module/microsoft.powershell.core/where-object)。</span><span class="sxs-lookup"><span data-stu-id="35172-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="35172-156">使用 PowerShellGet 安装 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="35172-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="35172-157">若要安装 DSC 资源，请使用[Install-module](/powershell/module/PowershellGet/Install-Module) cmdlet，指定下显示的模块的名称**模块**名称搜索结果中。</span><span class="sxs-lookup"><span data-stu-id="35172-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="35172-158">"时区"资源存在于"ComputerManagementDSC"模块，因此，它是此示例将安装该模块。</span><span class="sxs-lookup"><span data-stu-id="35172-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="35172-159">如果你有不受信任的 PowerShell 库，请参阅下面要求确认，该警告，并指示如何避免后续提示上安装。</span><span class="sxs-lookup"><span data-stu-id="35172-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="35172-160">按 y 以继续安装模块。</span><span class="sxs-lookup"><span data-stu-id="35172-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="35172-161">安装后，可以验证使用安装的新资源[Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)。</span><span class="sxs-lookup"><span data-stu-id="35172-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="35172-162">你还可以查看其他资源在新安装的模块中，通过指定`-ModuleName`参数。</span><span class="sxs-lookup"><span data-stu-id="35172-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="35172-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35172-163">See also</span></span>

- [<span data-ttu-id="35172-164">什么是资源？</span><span class="sxs-lookup"><span data-stu-id="35172-164">What are Resources?</span></span>](../resources/resources.md)
