---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: Desired State Configuration (DSC) 已知问题和限制
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855472"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="9d0f8-103">Desired State Configuration (DSC) 已知问题和限制</span><span class="sxs-lookup"><span data-stu-id="9d0f8-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="9d0f8-104">重大更改：DSC 配置中用于对密码进行加密/解密的证书在安装 WMF 5.0 RTM 后可能失效</span><span class="sxs-lookup"><span data-stu-id="9d0f8-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="9d0f8-105">在 WMF 4.0 和 WMF 5.0 预览版本中，DSC 不允许配置中的密码长度超过 121 个字符。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="9d0f8-106">尽管使用较长的强密码更好，但 DSC 强制使用短密码。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="9d0f8-107">此项重大更改使 DSC 配置中的密码可为任意长度。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="9d0f8-108">**解决方法：** 使用数据加密或密钥加密密钥用法和文档加密增强型密钥用法 (1.3.6.1.4.1.311.80.1) 重新创建证书。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="9d0f8-109">有关详细信息，请参阅 [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="9d0f8-110">安装 WMF 5.0 RTM 后 DSC cmdlet 可能失败</span><span class="sxs-lookup"><span data-stu-id="9d0f8-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="9d0f8-111">安装 WMF 5.0 RTM 后，`Start-DscConfiguration` 和其他 DSC cmdlet 可能失败并出现以下错误：</span><span class="sxs-lookup"><span data-stu-id="9d0f8-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="9d0f8-112">**解决方法：** 通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行）来删除 DSCEngineCache.mof：</span><span class="sxs-lookup"><span data-stu-id="9d0f8-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="9d0f8-113">如果在 WMF 5.0 生产预览版的基础上安装 WMF 5.0 RTM，DSC cmdlet 可能失效</span><span class="sxs-lookup"><span data-stu-id="9d0f8-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="9d0f8-114">**解决方法：** 在提升的 PowerShell 会话中运行以下命令（以管理员身份运行）：</span><span class="sxs-lookup"><span data-stu-id="9d0f8-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="9d0f8-115">在 DebugMode 中使用 Get-DscConfiguration 时，LCM 可能进入不稳定状态</span><span class="sxs-lookup"><span data-stu-id="9d0f8-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="9d0f8-116">如果 LCM 处于 DebugMode，按 Ctrl+C 来停止 `Get-DscConfiguration` 处理可能导致 LCM 进入不稳定状态，从而导致大部分 DSC cmdlet 失效。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="9d0f8-117">**解决方法：** 调试 `Get-DscConfiguration` cmdlet 时，不要按 Ctrl+C。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="9d0f8-118">在 DebugMode 中，Stop-DscConfiguration 可能不响应</span><span class="sxs-lookup"><span data-stu-id="9d0f8-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="9d0f8-119">如果 LCM 处于 DebugMode，则试图停止由 `Get-DscConfiguration` 启动的操作时，`Stop-DscConfiguration` 可能不响应</span><span class="sxs-lookup"><span data-stu-id="9d0f8-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="9d0f8-120">**解决方法：** 按[调试 DSC 资源](/powershell/dsc/troubleshooting/debugResource)中所述完成由 `Get-DscConfiguration` 所启动操作的调试。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="9d0f8-121">DebugMode 中不显示详细错误消息</span><span class="sxs-lookup"><span data-stu-id="9d0f8-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="9d0f8-122">如果 LCM 处于 DebugMode，DSC 资源中将不显示详细错误消息。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="9d0f8-123">**解决方法：** 禁用 DebugMode 以从资源中查看详细消息</span><span class="sxs-lookup"><span data-stu-id="9d0f8-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="9d0f8-124">Get-DscConfigurationStatus cmdlet 无法检索 Invoke-DscResource 操作</span><span class="sxs-lookup"><span data-stu-id="9d0f8-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="9d0f8-125">使用 `Invoke-DscResource` cmdlet 直接调用资源的方法后，将无法再通过 `Get-DscConfigurationStatus` 检索此类操作的记录。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="9d0f8-126">**解决方法：** 无。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="9d0f8-127">Get-DscConfigurationStatus 将请求周期操作返回为 **Consistency** 类型</span><span class="sxs-lookup"><span data-stu-id="9d0f8-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="9d0f8-128">将节点设置为 PULL 刷新模式时，对于所执行的每个请求操作，`Get-DscConfigurationStatus` cmdlet 会将操作类型报告为 Consistency 而不是 Initial</span><span class="sxs-lookup"><span data-stu-id="9d0f8-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="9d0f8-129">**解决方法：** 无。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="9d0f8-130">Invoke-DscResource cmdlet 不按生成消息的顺序返回消息</span><span class="sxs-lookup"><span data-stu-id="9d0f8-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="9d0f8-131">`Invoke-DscResource` cmdlet 不按 LCM 或 DSC 资源生成详细、警告和错误消息的顺序返回这些消息。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="9d0f8-132">**解决方法：** 无。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="9d0f8-133">与 Invoke-DscResource 一起使用时，无法轻松调试 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="9d0f8-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="9d0f8-134">LCM 在调试模式下运行时，`Invoke-DscResource` cmdlet 不会给出有关连接到运行空间以进行调试的信息。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="9d0f8-135">有关详细信息，请参阅[调试 DSC 资源](/powershell/dsc/troubleshooting/debugResource)。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-135">For more information, see [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="9d0f8-136">**解决方法：** 使用 cmdlet `Get-PSHostProcessInfo`、`Enter-PSHostProcess`、`Get-Runspace` 和 `Debug-Runspace` 发现并连接到运行空间以调试 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="9d0f8-137">同一节点的各部分配置文档不能具有相同的资源名称</span><span class="sxs-lookup"><span data-stu-id="9d0f8-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="9d0f8-138">对于部署到单个节点上的多个部分配置，相同的资源名称可能导致运行时错误。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="9d0f8-139">**解决方法：** 即使对不同部分配置中的相同资源也使用不同的名称。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="9d0f8-140">Start-DscConfiguration –UseExisting 不可与 -Credential 一起使用</span><span class="sxs-lookup"><span data-stu-id="9d0f8-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="9d0f8-141">使用具有 UseExisting 参数的 `Start-DscConfiguration` 时，将忽略 Credential 参数。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="9d0f8-142">DSC 使用默认进程标识继续执行操作。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="9d0f8-143">当需要其他凭据才可在远程节点上继续执行时，这将导致错误。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="9d0f8-144">**解决方法：** 使用 CIM 会话进行远程 DSC 操作：</span><span class="sxs-lookup"><span data-stu-id="9d0f8-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="9d0f8-145">将 IPv6 地址作为 DSC 配置中的节点名称</span><span class="sxs-lookup"><span data-stu-id="9d0f8-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="9d0f8-146">此版本中不支持将 IPv6 地址作为 DSC 配置脚本中的节点名称。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="9d0f8-147">**解决方法：** 无。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="9d0f8-148">调试 `Class-Based` DSC 资源</span><span class="sxs-lookup"><span data-stu-id="9d0f8-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="9d0f8-149">此版本中不支持调试基于类的 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="9d0f8-150">**解决方法：** 无。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="9d0f8-151">在多次调用 DSC 资源之间，将不保留在 DSC 基于类的资源中 $script 作用域内定义的变量和函数</span><span class="sxs-lookup"><span data-stu-id="9d0f8-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="9d0f8-152">如果配置使用任何基于类的资源，而该资源包含在 `$script` 作用域内定义的变量或函数，则对 `Start-DSCConfiguration` 的多个连续调用将失败。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="9d0f8-153">**解决方法：** 在 DSC 资源类本身中定义所有变量和函数。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="9d0f8-154">没有 `$script` 作用域的变量/函数。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="9d0f8-155">在资源使用 PSDscRunAsCredential 时进行 DSC 资源调试</span><span class="sxs-lookup"><span data-stu-id="9d0f8-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="9d0f8-156">在此版本中，当资源使用配置中的 PSDscRunAsCredential 属性时，不支持进行 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="9d0f8-157">**解决方法：** 无。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="9d0f8-158">不支持将 PsDscRunAsCredential 用于 DSC 复合资源</span><span class="sxs-lookup"><span data-stu-id="9d0f8-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="9d0f8-159">**解决方法：** 尽可能使用 Credential 属性。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="9d0f8-160">示例 ServiceSet 和 WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="9d0f8-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="9d0f8-161">Get-DscResource -Syntax 不能正确地反映 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9d0f8-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="9d0f8-162">当资源将 Syntax 参数标记为强制使用或不支持它时，它将不能正确地反映 PsDscRunAsCredential。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="9d0f8-163">**解决方法：** 无。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-163">**Resolution:** None.</span></span> <span data-ttu-id="9d0f8-164">但是，使用 IntelliSense 时，在 ISE 中创作配置可以反映关于 PsDscRunAsCredential 属性的正确元数据。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="9d0f8-165">WindowsOptionalFeature 在 Windows 7 中不可用</span><span class="sxs-lookup"><span data-stu-id="9d0f8-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="9d0f8-166">WindowsOptionalFeature DSC 资源在 Windows 7 中不可用。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="9d0f8-167">此资源需要 DISM 模块以及在 Windows 8 和更新版 Windows 操作系统中开始提供的 DISM cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="9d0f8-168">对于基于类的 DSC 资源，Import-DscResource -ModuleVersion 可能未按预期运行</span><span class="sxs-lookup"><span data-stu-id="9d0f8-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="9d0f8-169">如果编译节点具有多个版本的基于类的 DSC 资源模块，`Import-DscResource -ModuleVersion` 不会获取指定版本，并导致产生以下编译错误。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="9d0f8-170">**解决方法：** 通过定义 ModuleSpecification 对象将所需版本导入到 ModuleName 参数，RequiredVersion 密钥按如下所示指定：</span><span class="sxs-lookup"><span data-stu-id="9d0f8-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="9d0f8-171">一些 DSC 资源，如注册表资源可能开始需要较长时间处理请求。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="9d0f8-172">**解决方法 1：** 创建定期清理以下文件夹的计划任务。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="9d0f8-173">**解决方法 2：** 更改 DSC 配置以在配置结束时清理 CommandAnalysis 文件夹。</span><span class="sxs-lookup"><span data-stu-id="9d0f8-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
