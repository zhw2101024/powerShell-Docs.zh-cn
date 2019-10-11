---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 应用、获取并测试节点上的配置
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953834"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="e4851-103">应用、获取并测试节点上的配置</span><span class="sxs-lookup"><span data-stu-id="e4851-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="e4851-104">本指南将演示如何处理目标节点上的配置。</span><span class="sxs-lookup"><span data-stu-id="e4851-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="e4851-105">本指南分为以下几个步骤：</span><span class="sxs-lookup"><span data-stu-id="e4851-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="e4851-106">应用配置</span><span class="sxs-lookup"><span data-stu-id="e4851-106">Apply a Configuration</span></span>

<span data-ttu-id="e4851-107">为了应用和管理配置，我们需要生成一个“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="e4851-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="e4851-108">下面的代码表示将在整个指南中使用的一个简单配置。</span><span class="sxs-lookup"><span data-stu-id="e4851-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="e4851-109">编译此配置将产生两个“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="e4851-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="e4851-110">若要应用配置，请使用 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e4851-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="e4851-111">参数 `-Path` 指定“.mof”文件所在的目录。</span><span class="sxs-lookup"><span data-stu-id="e4851-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="e4851-112">如果未指定 `-Computername`，`Start-DSCConfiguration` 将尝试将每个配置应用于由“.mof”文件（\<computername \>.mof）的名称指定的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="e4851-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="e4851-113">将 `-Verbose` 指定为 `Start-DSCConfiguration`，以查看更详细的输出。</span><span class="sxs-lookup"><span data-stu-id="e4851-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="e4851-114">如果未指定 `-Wait`，你将看到创建了一个作业。</span><span class="sxs-lookup"><span data-stu-id="e4851-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="e4851-115">创建的作业将为每个由 `Start-DSCConfiguration` 处理的“.mof”文件提供一个 ChildJob  。</span><span class="sxs-lookup"><span data-stu-id="e4851-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="e4851-116">如果配置需要很长时间，并且你想要停止它，则可以使用 [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) 来停止本地节点上的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e4851-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="e4851-117">完成后，可以通过由 [Get-Job](/powershell/module/microsoft.powershell.core/get-job) 返回的作业对象查看作业状态。</span><span class="sxs-lookup"><span data-stu-id="e4851-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="e4851-118">要查看详细  输出，请使用以下命令查看每个 ChildJob  的详细  流。</span><span class="sxs-lookup"><span data-stu-id="e4851-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="e4851-119">有关 PowerShell 作业的详细信息，请参阅 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)。</span><span class="sxs-lookup"><span data-stu-id="e4851-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="e4851-120">从 PowerShell 5.0 开始，`-UseExisting` 参数已添加到 `Start-DSCConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="e4851-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="e4851-121">通过指定 `-UseExisting`，可以指示 cmdlet 使用现有的已应用配置，而不使用由 `-Path` 参数指定的配置。</span><span class="sxs-lookup"><span data-stu-id="e4851-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="e4851-122">测试配置</span><span class="sxs-lookup"><span data-stu-id="e4851-122">Test a Configuration</span></span>

<span data-ttu-id="e4851-123">可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 测试当前应用的配置。</span><span class="sxs-lookup"><span data-stu-id="e4851-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="e4851-124">如果节点兼容，`Test-DSCConfiguration` 将返回 `True`；如果不兼容，则返回 `False`。</span><span class="sxs-lookup"><span data-stu-id="e4851-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="e4851-125">从 PowerShell 5.0 开始，添加了 `-Detailed` 参数，该参数返回一个对象，其中包含 ResourcesInDesiredState  和 ResourcesNotInDesiredState  的集合</span><span class="sxs-lookup"><span data-stu-id="e4851-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="e4851-126">从 PowerShell 5.0 开始，可以在不应用配置的情况下对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="e4851-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="e4851-127">`-ReferenceConfiguration` 参数接受要对其测试节点的“.mof”文件的路径。</span><span class="sxs-lookup"><span data-stu-id="e4851-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="e4851-128">没有对节点执行任何设置  操作。</span><span class="sxs-lookup"><span data-stu-id="e4851-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="e4851-129">在 PowerShell 4.0 中，有一些解决方法可在不应用配置的情况下对其进行测试，但在这里不予讨论。</span><span class="sxs-lookup"><span data-stu-id="e4851-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="e4851-130">获取配置值</span><span class="sxs-lookup"><span data-stu-id="e4851-130">Get Configuration Values</span></span>

<span data-ttu-id="e4851-131">[Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 返回当前应用的配置中任何已配置资源的当前值。</span><span class="sxs-lookup"><span data-stu-id="e4851-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="e4851-132">如果应用成功，示例配置的输出将如下所示。</span><span class="sxs-lookup"><span data-stu-id="e4851-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="e4851-133">获取配置状态</span><span class="sxs-lookup"><span data-stu-id="e4851-133">Get Configuration Status</span></span>

<span data-ttu-id="e4851-134">从 PowerShell 5.0 开始，借助 [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet，用户可查看节点的已应用配置的历史记录。</span><span class="sxs-lookup"><span data-stu-id="e4851-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="e4851-135">PowerShell DSC 跟踪在推送  或拉取  模式下应用的最后 {{N}} 个配置。</span><span class="sxs-lookup"><span data-stu-id="e4851-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="e4851-136">这包括 LCM 执行的任何一致性  检查。</span><span class="sxs-lookup"><span data-stu-id="e4851-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="e4851-137">默认情况下，`Get-DSCConfigurationStatus` 只显示最后一个历史记录条目。</span><span class="sxs-lookup"><span data-stu-id="e4851-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="e4851-138">使用 `-All` 参数查看所有配置状态历史记录。</span><span class="sxs-lookup"><span data-stu-id="e4851-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="e4851-139">为简洁起见，输出将被截断。</span><span class="sxs-lookup"><span data-stu-id="e4851-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="e4851-140">管理配置文档</span><span class="sxs-lookup"><span data-stu-id="e4851-140">Manage Configuration Documents</span></span>

<span data-ttu-id="e4851-141">LCM 通过处理配置文档  来管理节点配置。</span><span class="sxs-lookup"><span data-stu-id="e4851-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="e4851-142">这些“.mof”文件驻留在“C:\Windows\System32\Configuration”目录中。</span><span class="sxs-lookup"><span data-stu-id="e4851-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="e4851-143">从 PowerShell 5.0 开始，借助 [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)用户可删除“.mof”文件来停止未来的一致性检查，或删除应用时出现错误的配置。</span><span class="sxs-lookup"><span data-stu-id="e4851-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="e4851-144">`-Stage` 参数允许用户指定要删除的“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="e4851-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="e4851-145">在 PowerShell 4.0 中，仍可以使用 [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) 来直接删除这些“.mof”文件。</span><span class="sxs-lookup"><span data-stu-id="e4851-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="e4851-146">发布配置</span><span class="sxs-lookup"><span data-stu-id="e4851-146">Publish Configurations</span></span>

<span data-ttu-id="e4851-147">从 PowerShell 5.0 开始，添加了 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e4851-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="e4851-148">可通过此 cmdlet 将“.mof”文件发布到远程计算机，而无需应用它。</span><span class="sxs-lookup"><span data-stu-id="e4851-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="e4851-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4851-149">See also</span></span>

- [<span data-ttu-id="e4851-150">获取、测试并设置</span><span class="sxs-lookup"><span data-stu-id="e4851-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
