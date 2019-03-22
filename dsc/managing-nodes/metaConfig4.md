---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 在早期版本的 Windows PowerShell 中配置本地配置管理器
ms.openlocfilehash: cea32c9aa8144bc52f3d44f2ad852f577f6a5e6d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055302"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a><span data-ttu-id="440de-103">在早期版本的 Windows PowerShell 中配置本地配置管理器</span><span class="sxs-lookup"><span data-stu-id="440de-103">Configuring the Local Configuration Manager in Previous Versions of Windows PowerShell</span></span>

><span data-ttu-id="440de-104">适用于：Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="440de-104">Applies To: Windows PowerShell 4.0</span></span>

<span data-ttu-id="440de-105">**有关 Windows PowerShell 5.0 和更高版本的信息，请参阅[配置本地配置管理器](metaConfig.md)。**</span><span class="sxs-lookup"><span data-stu-id="440de-105">**For information related to Windows PowerShell 5.0 and later, see [Configuring the Local Configuration Manager](metaConfig.md).**</span></span>

<span data-ttu-id="440de-106">本地配置管理器是 Windows PowerShell Desired State Configuration (DSC) 引擎。</span><span class="sxs-lookup"><span data-stu-id="440de-106">Local Configuration Manager is the Windows PowerShell Desired State Configuration (DSC) engine.</span></span>
<span data-ttu-id="440de-107">它在所有的目标节点上运行，负责调用 DSC 配置脚本中包含的配置资源。</span><span class="sxs-lookup"><span data-stu-id="440de-107">It runs on all target nodes, and it is responsible for calling the configuration resources that are included in a DSC configuration script.</span></span>
<span data-ttu-id="440de-108">本主题列出了本地配置管理器的属性，并介绍如何在目标节点上修改本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="440de-108">This topic lists the properties of Local Configuration Manager and describes how you can modify the Local Configuration Manager settings on a target node.</span></span>

## <a name="local-configuration-manager-properties"></a><span data-ttu-id="440de-109">本地配置管理器属性</span><span class="sxs-lookup"><span data-stu-id="440de-109">Local Configuration Manager properties</span></span>

<span data-ttu-id="440de-110">以下列出了可以设置或检索的本地配置管理器属性。</span><span class="sxs-lookup"><span data-stu-id="440de-110">The following lists the Local Configuration Manager properties that you can set or retrieve.</span></span>

- <span data-ttu-id="440de-111">**AllowModuleOverwrite**：控制是否允许从配置服务下载的新配置覆盖目标节点上的旧配置。</span><span class="sxs-lookup"><span data-stu-id="440de-111">**AllowModuleOverwrite**: Controls whether new configurations downloaded from the configuration service are allowed to overwrite the old ones on the target node.</span></span> <span data-ttu-id="440de-112">可能的值为 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="440de-112">Possible values are True and False.</span></span>
- <span data-ttu-id="440de-113">**CertificateID**:用于保护在配置中传递的凭据的证书指纹。</span><span class="sxs-lookup"><span data-stu-id="440de-113">**CertificateID**: The thumbprint of a certificate used to secure credentials passed in a configuration.</span></span> <span data-ttu-id="440de-114">更多详细信息，请参阅 [Want to secure credentials in Windows PowerShell Desired State Configuration?（希望在 Windows PowerShell Desired State Configuration 中保护凭据？）](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/)。</span><span class="sxs-lookup"><span data-stu-id="440de-114">For more information see [Want to secure credentials in Windows PowerShell Desired State Configuration?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).</span></span>
- <span data-ttu-id="440de-115">**ConfigurationID**：指示用于从请求服务获取特定配置文件的 GUID。</span><span class="sxs-lookup"><span data-stu-id="440de-115">**ConfigurationID**: Indicates a GUID which is used to get a particular configuration file from a pull service.</span></span> <span data-ttu-id="440de-116">GUID 可确保访问正确的配置文件。</span><span class="sxs-lookup"><span data-stu-id="440de-116">The GUID ensures that the correct configuration file is accessed.</span></span>
- <span data-ttu-id="440de-117">**ConfigurationMode**：指定本地配置管理器实际如何将配置应用到目标节点。</span><span class="sxs-lookup"><span data-stu-id="440de-117">**ConfigurationMode**: Specifies how the Local Configuration Manager actually applies the configuration to the target nodes.</span></span> <span data-ttu-id="440de-118">可以有下列值：</span><span class="sxs-lookup"><span data-stu-id="440de-118">It can take the following values:</span></span>
  - <span data-ttu-id="440de-119">**ApplyOnly**：使用此选项，DSC 将应用配置，但在检测到新配置之前不会执行任何进一步操作。检测新配置的方式可以是向目标节点直接发送新配置；也可以是连接请求服务后，DSC 检查请求服务时发现新配置。</span><span class="sxs-lookup"><span data-stu-id="440de-119">**ApplyOnly**: With this option, DSC applies the configuration and does nothing further unless a new configuration is detected, either by you sending a new configuration directly to the target node or if you are connecting to a pull service and DSC discovers a new configuration when it checks with the pull service.</span></span> <span data-ttu-id="440de-120">如果目标节点的配置偏离，则不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="440de-120">If the target node’s configuration drifts, no action is taken.</span></span>
  - <span data-ttu-id="440de-121">**ApplyAndMonitor**：使用此选项（默认），DSC 会应用任何由你直接发送到目标节点的或者在请求服务上发现的新配置。</span><span class="sxs-lookup"><span data-stu-id="440de-121">**ApplyAndMonitor**: With this option (which is the default), DSC applies any new configurations, whether sent by you directly to the target node or discovered on a pull service.</span></span> <span data-ttu-id="440de-122">此后，如果目标节点的配置偏离配置文件，DSC 将在日志中报告差异。</span><span class="sxs-lookup"><span data-stu-id="440de-122">Thereafter, if the configuration of the target node drifts from the configuration file, DSC reports the discrepancy in logs.</span></span> <span data-ttu-id="440de-123">有关 DSC 日志记录的详细信息，请参阅 [Using Event Logs to Diagnose Errors in Desired State Configuration（在 Desired State Configuration 中使用事件日志诊断错误）](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx)。</span><span class="sxs-lookup"><span data-stu-id="440de-123">For more about DSC logging, see [Using Event Logs to Diagnose Errors in Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).</span></span>
  - <span data-ttu-id="440de-124">**ApplyAndAutoCorrect**：使用此选项，DSC 会应用任何由你直接发送到目标节点的或者在请求服务上发现的新配置。</span><span class="sxs-lookup"><span data-stu-id="440de-124">**ApplyAndAutoCorrect**: With this option, DSC applies any new configurations, whether sent by you directly to the target node or discovered on a pull service.</span></span> <span data-ttu-id="440de-125">此后，如果目标节点的配置偏离配置文件，DSC 将在日志中报告差异，并尝试调整目标节点配置，使其与配置文件相容。</span><span class="sxs-lookup"><span data-stu-id="440de-125">Thereafter, if the configuration of the target node drifts from the configuration file, DSC reports the discrepancy in logs, and then attempts to adjust the target node configuration to bring in compliance with the configuration file.</span></span>
- <span data-ttu-id="440de-126">**ConfigurationModeFrequencyMins**：表示 DSC 的后台应用程序尝试在目标节点上执行当前配置的频率（以分钟为单位）。</span><span class="sxs-lookup"><span data-stu-id="440de-126">**ConfigurationModeFrequencyMins**: Represents the frequency (in minutes) at which the background application of DSC attempts to implement the current configuration on the target node.</span></span> <span data-ttu-id="440de-127">默认值为 15。</span><span class="sxs-lookup"><span data-stu-id="440de-127">The default value is 15.</span></span> <span data-ttu-id="440de-128">可将此值设置为与 RefreshMode 结合使用。</span><span class="sxs-lookup"><span data-stu-id="440de-128">This value can be set in conjunction with RefreshMode.</span></span> <span data-ttu-id="440de-129">当 RefreshMode 设置为 PULL 时，目标节点按 RefreshFrequencyMins 所设置的时间间隔与配置服务联系并下载当前配置。</span><span class="sxs-lookup"><span data-stu-id="440de-129">When RefreshMode is set to PULL, the target node contacts the configuration service at an interval set by RefreshFrequencyMins and downloads the current configuration.</span></span> <span data-ttu-id="440de-130">无论 RefreshMode 值如何，一致性引擎都会在由 ConfigurationModeFrequencyMins 设置的时间间隔将下载的最新配置应用到目标节点。</span><span class="sxs-lookup"><span data-stu-id="440de-130">Regardless of the RefreshMode value, at the interval set by ConfigurationModeFrequencyMins, the consistency engine applies the latest configuration that was downloaded to the target node.</span></span> <span data-ttu-id="440de-131">RefreshFrequencyMins 应设置为 ConfigurationModeFrequencyMins 的整倍数。</span><span class="sxs-lookup"><span data-stu-id="440de-131">RefreshFrequencyMins should be set to an integer multiple of ConfigurationModeFrequencyMins.</span></span>
- <span data-ttu-id="440de-132">**Credential**：指示访问远程资源（例如联系配置服务）所需的凭据（与 Get-Credential 相同）。</span><span class="sxs-lookup"><span data-stu-id="440de-132">**Credential**: Indicates credentials (as with Get-Credential) required to access remote resources, such as to contact the configuration service.</span></span>
- <span data-ttu-id="440de-133">**DownloadManagerCustomData**：表示包含特定于下载管理器的自定义数据的数组。</span><span class="sxs-lookup"><span data-stu-id="440de-133">**DownloadManagerCustomData**: Represents an array that contains custom data specific to the download manager.</span></span>
- <span data-ttu-id="440de-134">**DownloadManagerName**：指示配置和模块下载管理器的名称。</span><span class="sxs-lookup"><span data-stu-id="440de-134">**DownloadManagerName**: Indicates the name of the configuration and module download manager.</span></span>
- <span data-ttu-id="440de-135">**RebootNodeIfNeeded**：将此设置为 `$true` 可使资源使用 `$global:DSCMachineStatus` 标志重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="440de-135">**RebootNodeIfNeeded**: Set this to `$true` to allow resources to reboot the Node using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="440de-136">否则，你必须为要求重启的配置手动重启节点。</span><span class="sxs-lookup"><span data-stu-id="440de-136">Otherwise, you will have to manually reboot the node for any configuration that requires it.</span></span> <span data-ttu-id="440de-137">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="440de-137">The default value is `$false`.</span></span> <span data-ttu-id="440de-138">若要在通过 DSC（例如 Windows Installer）以外的其他配置执行重启条件时使用此设置，请将此设置和 [xPendingReboot](https://github.com/powershell/xpendingreboot) 模块组合使用。</span><span class="sxs-lookup"><span data-stu-id="440de-138">To use this setting when a reboot condition is enacted by something other than DSC (such as Windows Installer), combine this setting with the [xPendingReboot](https://github.com/powershell/xpendingreboot) module.</span></span>
- <span data-ttu-id="440de-139">**RefreshFrequencyMins**：设置请求服务后使用。</span><span class="sxs-lookup"><span data-stu-id="440de-139">**RefreshFrequencyMins**: Used when you have set up a pull service.</span></span> <span data-ttu-id="440de-140">表示本地配置管理器联系请求服务下载当前配置的频率（以分钟为单位）。</span><span class="sxs-lookup"><span data-stu-id="440de-140">Represents the frequency (in minutes) at which the Local Configuration Manager contacts a pull service to download the current configuration.</span></span> <span data-ttu-id="440de-141">可将此值设置为与 ConfigurationModeFrequencyMins 结合使用。</span><span class="sxs-lookup"><span data-stu-id="440de-141">This value can be set in conjunction with ConfigurationModeFrequencyMins.</span></span> <span data-ttu-id="440de-142">当 RefreshMode 设置为 PULL 时，目标节点按 RefreshFrequencyMins 所设置的时间间隔与请求服务联系并下载当前配置。</span><span class="sxs-lookup"><span data-stu-id="440de-142">When RefreshMode is set to PULL, the target node contacts the pull service at an interval set by RefreshFrequencyMins and downloads the current configuration.</span></span> <span data-ttu-id="440de-143">一致性引擎将在由 ConfigurationModeFrequencyMins 设置的时间间隔将下载的最新配置应用到目标节点。</span><span class="sxs-lookup"><span data-stu-id="440de-143">At the interval set by ConfigurationModeFrequencyMins, the consistency engine then applies the latest configuration that was downloaded to the target node.</span></span> <span data-ttu-id="440de-144">若 RefreshFrequencyMins 未设置为 ConfigurationModeFrequencyMins 的整倍数，系统将会向上进行舍入。</span><span class="sxs-lookup"><span data-stu-id="440de-144">If RefreshFrequencyMins is not set to an integer multiple of ConfigurationModeFrequencyMins, the system will round it up.</span></span> <span data-ttu-id="440de-145">默认值为 30。</span><span class="sxs-lookup"><span data-stu-id="440de-145">The default value is 30.</span></span>
- <span data-ttu-id="440de-146">**RefreshMode**：可能的值为 Push（默认值）和 Pull。</span><span class="sxs-lookup"><span data-stu-id="440de-146">**RefreshMode**: Possible values are **Push** (the default) and **Pull**.</span></span> <span data-ttu-id="440de-147">在“推送”配置下，必须在每个目标节点上放置配置文件（可使用任何客户端计算机进行此操作）。</span><span class="sxs-lookup"><span data-stu-id="440de-147">In the “push” configuration, you must place a configuration file on each target node, using any client computer.</span></span> <span data-ttu-id="440de-148">在“请求”模式下，必须为本地配置管理器设置请求服务，以便其联系和访问配置文件。</span><span class="sxs-lookup"><span data-stu-id="440de-148">In the “pull” mode, you must set up a pull service for Local Configuration Manager to contact and access the configuration files.</span></span>

> [!NOTE]
> <span data-ttu-id="440de-149">LCM 基于以下条件启动 ConfigurationModeFrequencyMins 周期：</span><span class="sxs-lookup"><span data-stu-id="440de-149">The LCM starts the **ConfigurationModeFrequencyMins** cycle based on:</span></span>
>
> - <span data-ttu-id="440de-150">使用 `Set-DscLocalConfigurationManager` 应用新的元配置</span><span class="sxs-lookup"><span data-stu-id="440de-150">A new metaconfig is applied using `Set-DscLocalConfigurationManager`</span></span>
> - <span data-ttu-id="440de-151">计算机重新启动</span><span class="sxs-lookup"><span data-stu-id="440de-151">A machine restart</span></span>
>
> <span data-ttu-id="440de-152">对于计时器进程遇到故障的任何状况，会在 30 秒内检测到该状况，并且会重新启动周期。</span><span class="sxs-lookup"><span data-stu-id="440de-152">For any condition where the timer process experiences a crash, that will be detected within 30 seconds and the cycle will be restarted.</span></span>
> <span data-ttu-id="440de-153">并发操作可能会延迟周期启动，如果此操作的持续时间超过配置的频率，则下一个计时器不会启动。</span><span class="sxs-lookup"><span data-stu-id="440de-153">A concurrent operation could delay the cycle from being started, if the duration of this operation exceeds the configured cycle frequency, the next timer will not start.</span></span>
>
> <span data-ttu-id="440de-154">例如，元配置以 15 分钟请求频率进行配置，请求会在 T1 进行。</span><span class="sxs-lookup"><span data-stu-id="440de-154">Example, the metaconfig is configured at a 15 minute pull frequency and a pull occurs at T1.</span></span>  <span data-ttu-id="440de-155">节点未在 16 分钟内完成工作。</span><span class="sxs-lookup"><span data-stu-id="440de-155">The Node does not finish work for 16 minutes.</span></span>  <span data-ttu-id="440de-156">第一个 15 分钟周期会被忽略，下一个请求会在 T1+15+15 进行。</span><span class="sxs-lookup"><span data-stu-id="440de-156">The first 15 minute cycle is ignored, and next pull will happen at T1+15+15.</span></span>

### <a name="example-of-updating-local-configuration-manager-settings"></a><span data-ttu-id="440de-157">更新本地配置管理器设置的示例</span><span class="sxs-lookup"><span data-stu-id="440de-157">Example of updating Local Configuration Manager settings</span></span>

<span data-ttu-id="440de-158">可以通过在节点块内包含 **LocalConfigurationManager** 块来更新目标节点的本地配置管理器设置，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="440de-158">You can update the Local Configuration Manager settings of a target node by including a **LocalConfigurationManager** block inside the node block in a configuration script, as shown in the following example.</span></span>

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

<span data-ttu-id="440de-159">运行以上示例中的脚本将生成一个 MOF 文件，它指定并存储了所需设置。</span><span class="sxs-lookup"><span data-stu-id="440de-159">Running the script in the previous example generates a MOF file that specifies and stores the desired settings.</span></span>
<span data-ttu-id="440de-160">若要应用这些设置，可以使用 **Set-DscLocalConfigurationManager** cmdlet，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="440de-160">To apply the settings, you can use the **Set-DscLocalConfigurationManager** cmdlet, as shown in the following example.</span></span>

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> <span data-ttu-id="440de-161">调用以上示例中的配置时，必须为 **Path** 参数指定与 **OutputPath** 参数相同的路径。</span><span class="sxs-lookup"><span data-stu-id="440de-161">For the **Path** parameter, you must specify the same path that you specified for the **OutputPath** parameter when you invoked the configuration in the previous example.</span></span>

<span data-ttu-id="440de-162">若要查看当前本地配置管理器设置，可以使用 **Get-DscLocalConfigurationManager** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="440de-162">To see the current Local Configuration Manager settings, you can use the **Get-DscLocalConfigurationManager** cmdlet.</span></span>
<span data-ttu-id="440de-163">如果不带任何参数调用此 cmdlet，默认情况下它将获取其运行于的节点上的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="440de-163">If you invoke this cmdlet with no parameters, by default it will get the Local Configuration Manager settings for the node on which you run it.</span></span>
<span data-ttu-id="440de-164">若要指定另一个节点，请将 **CimSession** 参数用于此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="440de-164">To specify another node, use the **CimSession** parameter with this cmdlet.</span></span>
