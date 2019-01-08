---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 调试 DSC 资源
ms.openlocfilehash: 9b2e7dd9b42332b869c4d7fabb21bd4b5a6b8800
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400448"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="e864d-103">调试 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="e864d-103">Debugging DSC resources</span></span>

> <span data-ttu-id="e864d-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e864d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e864d-105">在 PowerShell 5.0 中，Desired State Configuraiton (DSC) 引入了一项新功能，允许你在应用配置时调试 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="e864d-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="e864d-106">启用 DSC 调试</span><span class="sxs-lookup"><span data-stu-id="e864d-106">Enabling DSC debugging</span></span>
<span data-ttu-id="e864d-107">必须通过调用 [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet 启用调试后，才能调试资源。</span><span class="sxs-lookup"><span data-stu-id="e864d-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span>
<span data-ttu-id="e864d-108">此 cmdlet 采用强制参数，**BreakAll**。</span><span class="sxs-lookup"><span data-stu-id="e864d-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="e864d-109">你可通过查看调用 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) 的结果以验证是否已启用调试。</span><span class="sxs-lookup"><span data-stu-id="e864d-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="e864d-110">以下 PowerShell 输出显式了启用调试的结果：</span><span class="sxs-lookup"><span data-stu-id="e864d-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="e864d-111">启用调试时启动配置</span><span class="sxs-lookup"><span data-stu-id="e864d-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="e864d-112">若要调试 DSC 资源，首先需启动调用该资源的配置。</span><span class="sxs-lookup"><span data-stu-id="e864d-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="e864d-113">针对此示例，我们将查看调用 **WindowsFeature** 资源的简单配置以确保安装了“WindowsPowerShellWebAccess”功能：</span><span class="sxs-lookup"><span data-stu-id="e864d-113">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="e864d-114">编译配置后，通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) 启用该配置。</span><span class="sxs-lookup"><span data-stu-id="e864d-114">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span>
<span data-ttu-id="e864d-115">当本地配置管理器 (LCM) 调用配置中的首个资源时，配置会停止运行。</span><span class="sxs-lookup"><span data-stu-id="e864d-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="e864d-116">如果你使用 `-Verbose` 和 `-Wait` 参数，输出会显示你需要输入才能启动调试的各行内容。</span><span class="sxs-lookup"><span data-stu-id="e864d-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="e864d-117">此时，LCM 已调用该资源，并到达第一个断点。</span><span class="sxs-lookup"><span data-stu-id="e864d-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="e864d-118">输出中的最后三行表明了如何附加到进程并启动调试资源脚本。</span><span class="sxs-lookup"><span data-stu-id="e864d-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="e864d-119">调试资源脚本</span><span class="sxs-lookup"><span data-stu-id="e864d-119">Debugging the resource script</span></span>

<span data-ttu-id="e864d-120">启动 PowerShell ISE 的新实例。</span><span class="sxs-lookup"><span data-stu-id="e864d-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="e864d-121">在控制台窗格中，输入 `Start-DscConfiguration` 输出中最后三行的内容作为命令，将 `<credentials>` 替换为有效的用户凭据。</span><span class="sxs-lookup"><span data-stu-id="e864d-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="e864d-122">你现在应看到类似于下面这样的提示：</span><span class="sxs-lookup"><span data-stu-id="e864d-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="e864d-123">资源脚本会在脚本窗格中打开，调试器会在 **Test-TargetResource** 函数（基于类的资源的 **Test()** 方法）的第一行停止运行。</span><span class="sxs-lookup"><span data-stu-id="e864d-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="e864d-124">现在可以在 ISE 中使用调试命令来单步执行资源脚本、查看变量值、查看调用堆栈等等。</span><span class="sxs-lookup"><span data-stu-id="e864d-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="e864d-125">请记住，资源脚本（或类）中的每行都会设置为断点。</span><span class="sxs-lookup"><span data-stu-id="e864d-125">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="e864d-126">禁用 DSC 调试</span><span class="sxs-lookup"><span data-stu-id="e864d-126">Disabling DSC debugging</span></span>

<span data-ttu-id="e864d-127">在调用 [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) 后，对 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) 的所有调用都会导致配置中断调试器。</span><span class="sxs-lookup"><span data-stu-id="e864d-127">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="e864d-128">若要让配置正常运行，必须通过调用 [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet 来禁用调试。</span><span class="sxs-lookup"><span data-stu-id="e864d-128">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

><span data-ttu-id="e864d-129">**注意：** 重启不会更改 LCM 的调试状态。</span><span class="sxs-lookup"><span data-stu-id="e864d-129">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="e864d-130">如果调试已启用，那么启动配置仍会在重启后中断调试器。</span><span class="sxs-lookup"><span data-stu-id="e864d-130">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="e864d-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e864d-131">See Also</span></span>

- [<span data-ttu-id="e864d-132">使用 MOF 编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="e864d-132">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="e864d-133">使用 PowerShell 类编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="e864d-133">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
