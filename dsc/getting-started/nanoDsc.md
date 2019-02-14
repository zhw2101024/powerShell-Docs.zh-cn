---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用 Nano Server 上的 DSC
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400461"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="cc814-103">使用 Nano Server 上的 DSC</span><span class="sxs-lookup"><span data-stu-id="cc814-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="cc814-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cc814-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="cc814-105">**Nano Server 上的 DSC** 是 Windows Server 2016 媒体 `NanoServer\Packages` 文件夹中的可选包。</span><span class="sxs-lookup"><span data-stu-id="cc814-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="cc814-106">通过以下方法为 Nano Server 创建 VHD 后可以安装此包：将 **Microsoft-NanoServer-DSC-Package** 指定为 **New-NanoServerImage** 函数的 **Packages** 参数值。</span><span class="sxs-lookup"><span data-stu-id="cc814-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="cc814-107">例如，如果你要为虚拟机创建 VHD，则命令如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc814-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="cc814-108">若要了解如何安装和使用 Nano Server，以及如何使用 PowerShell 远程处理来管理 Nano Server，请参阅 [Getting Started with Nano Server（Nano Server 入门）](/windows-server/get-started/getting-started-with-nano-server)。</span><span class="sxs-lookup"><span data-stu-id="cc814-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="cc814-109">Nano Server 上可用的 DSC 功能</span><span class="sxs-lookup"><span data-stu-id="cc814-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="cc814-110">由于与完整版的 Windows Server 相比，Nano Server 仅支持一组数量有限的 API，因此 Nano Server 上的 DSC 暂时没有与完整 SKU 上运行的 DSC 等同的完整功能。</span><span class="sxs-lookup"><span data-stu-id="cc814-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="cc814-111">Nano Server 上的 DSC 正处于积极开发中，且功能尚未完善。</span><span class="sxs-lookup"><span data-stu-id="cc814-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="cc814-112">下面的 DSC 功能当前在 Nano Server 上均可用：</span><span class="sxs-lookup"><span data-stu-id="cc814-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="cc814-113">推送和请求模式</span><span class="sxs-lookup"><span data-stu-id="cc814-113">Both push and pull modes</span></span>

- <span data-ttu-id="cc814-114">完整版 Windows Server 上存在的所有 DSC cmdlet，包括：</span><span class="sxs-lookup"><span data-stu-id="cc814-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="cc814-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cc814-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="cc814-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cc814-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="cc814-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="cc814-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="cc814-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="cc814-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="cc814-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc814-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="cc814-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc814-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="cc814-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc814-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="cc814-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc814-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="cc814-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="cc814-123">Publish-DscConfiguraiton</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="cc814-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc814-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="cc814-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc814-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="cc814-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="cc814-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="cc814-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="cc814-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="cc814-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="cc814-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="cc814-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="cc814-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="cc814-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="cc814-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="cc814-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="cc814-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="cc814-132">编译配置（请参阅 [DSC 配置](../configurations/configurations.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="cc814-133">**问题 #1629**密码加密 (请参阅[保护 MOF 文件](../pull-server/secureMOF.md)) 在配置期间，编译不起作用。</span><span class="sxs-lookup"><span data-stu-id="cc814-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="cc814-134">编译元配置（请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="cc814-135">在用户上下文内运行资源（请参阅[使用用户凭据运行 DSC (RunAs)](../configurations/runAsUser.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="cc814-136">基于类的资源（请参阅[使用 PowerShell 类编写自定义 DSC 资源](../resources/authoringResourceClass.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="cc814-137">调试 DSC 资源（见[调试 DSC 资源](../troubleshooting/debugResource.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="cc814-138">**问题 #1629**如果资源使用 PsDscRunAsCredential 不起作用 (请参阅[使用用户凭据运行 DSC](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="cc814-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="cc814-139">指定跨节点依赖关系</span><span class="sxs-lookup"><span data-stu-id="cc814-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="cc814-140">资源版本控制</span><span class="sxs-lookup"><span data-stu-id="cc814-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="cc814-141">请求客户端（配置和资源）（请参阅[使用配置名称设置请求客户端](../pull-server/pullClientConfigNames.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="cc814-142">部分配置（请求和推送）</span><span class="sxs-lookup"><span data-stu-id="cc814-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="cc814-143">向请求服务器报告</span><span class="sxs-lookup"><span data-stu-id="cc814-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="cc814-144">MOF 加密</span><span class="sxs-lookup"><span data-stu-id="cc814-144">MOF encryption</span></span>

- <span data-ttu-id="cc814-145">事件日志记录</span><span class="sxs-lookup"><span data-stu-id="cc814-145">Event logging</span></span>

- <span data-ttu-id="cc814-146">Azure 自动化 DSC 报告</span><span class="sxs-lookup"><span data-stu-id="cc814-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="cc814-147">功能齐全的资源</span><span class="sxs-lookup"><span data-stu-id="cc814-147">Resources that are fully functional</span></span>

- <span data-ttu-id="cc814-148">**存档**</span><span class="sxs-lookup"><span data-stu-id="cc814-148">**Archive**</span></span>
- <span data-ttu-id="cc814-149">**环境**</span><span class="sxs-lookup"><span data-stu-id="cc814-149">**Environment**</span></span>
- <span data-ttu-id="cc814-150">**文件**</span><span class="sxs-lookup"><span data-stu-id="cc814-150">**File**</span></span>
- <span data-ttu-id="cc814-151">**日志**</span><span class="sxs-lookup"><span data-stu-id="cc814-151">**Log**</span></span>
- <span data-ttu-id="cc814-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="cc814-152">**ProcessSet**</span></span>
- <span data-ttu-id="cc814-153">**注册表**</span><span class="sxs-lookup"><span data-stu-id="cc814-153">**Registry**</span></span>
- <span data-ttu-id="cc814-154">**脚本**</span><span class="sxs-lookup"><span data-stu-id="cc814-154">**Script**</span></span>
- <span data-ttu-id="cc814-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="cc814-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="cc814-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="cc814-156">**WindowsProcess**</span></span>
- <span data-ttu-id="cc814-157">**WaitForAll**（请参阅[请参阅指定跨节点依赖关系](../configurations/crossNodeDependencies.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="cc814-158">**WaitForAny**（请参阅[指定跨节点依赖关系](../configurations/crossNodeDependencies.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="cc814-159">**WaitForSome**（请参阅[指定跨节点依赖关系](../configurations/crossNodeDependencies.md)）</span><span class="sxs-lookup"><span data-stu-id="cc814-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="cc814-160">实现部分功能的资源</span><span class="sxs-lookup"><span data-stu-id="cc814-160">Resources that are partially functional</span></span>
- <span data-ttu-id="cc814-161">**组**</span><span class="sxs-lookup"><span data-stu-id="cc814-161">**Group**</span></span>
- <span data-ttu-id="cc814-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="cc814-162">**GroupSet**</span></span>

  <span data-ttu-id="cc814-163">**问题 #1629**上面的资源失败，如果调用了两次特定实例 （运行两次相同的配置）</span><span class="sxs-lookup"><span data-stu-id="cc814-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="cc814-164">**服务**</span><span class="sxs-lookup"><span data-stu-id="cc814-164">**Service**</span></span>
- <span data-ttu-id="cc814-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="cc814-165">**ServiceSet**</span></span>

  <span data-ttu-id="cc814-166">**问题 #1629**仅适用于启动/停止 （状态） 的服务。</span><span class="sxs-lookup"><span data-stu-id="cc814-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="cc814-167">如果有人尝试更改其他服务属性（如 startuptype、credentials、description 等），则会失败。</span><span class="sxs-lookup"><span data-stu-id="cc814-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="cc814-168">引发的错误类似于：</span><span class="sxs-lookup"><span data-stu-id="cc814-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="cc814-169">找不到类型 [management.managementobject]: 请验证包含此类型的程序集是否已加载。</span><span class="sxs-lookup"><span data-stu-id="cc814-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="cc814-170">无法实现功能的资源</span><span class="sxs-lookup"><span data-stu-id="cc814-170">Resources that are not functional</span></span>
- <span data-ttu-id="cc814-171">**用户**</span><span class="sxs-lookup"><span data-stu-id="cc814-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="cc814-172">Nano Server 上不可用的 DSC 功能</span><span class="sxs-lookup"><span data-stu-id="cc814-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="cc814-173">下面的 DSC 功能当前在 Nano 服务器上不可用：</span><span class="sxs-lookup"><span data-stu-id="cc814-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="cc814-174">使用加密的密码解密 MOF 文档</span><span class="sxs-lookup"><span data-stu-id="cc814-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="cc814-175">请求服务器 - 当前不能在 Nano Server 上设置请求服务器</span><span class="sxs-lookup"><span data-stu-id="cc814-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="cc814-176">不在功能工作列表中的任何内容</span><span class="sxs-lookup"><span data-stu-id="cc814-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="cc814-177">在 Nano Server 上使用自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="cc814-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="cc814-178">由于 Nano Server 上仅可使用的有限的 Windows API 集和 CLR 库，因此在完整 CLR 版的 Windows 上运行的 DSC 资源并不一定适用于 Nano Server。</span><span class="sxs-lookup"><span data-stu-id="cc814-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="cc814-179">在部署任意 DSC 资源到生产环境之前，先完成端到端测试。</span><span class="sxs-lookup"><span data-stu-id="cc814-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc814-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc814-180">See Also</span></span>

- [<span data-ttu-id="cc814-181">Nano Server 入门</span><span class="sxs-lookup"><span data-stu-id="cc814-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)