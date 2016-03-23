# 调试 DSC 资源

> 适用于：Windows PowerShell 5.0

在 PowerShell 5.0 中，Desired State Configuraiton (DSC) 引入了一项新功能，允许你在应用配置时调试 DSC 资源。

## 启用 DSC 调试
必须通过调用 [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx) cmdlet 启用调试后，才能调试资源。 此 cmdlet 采用强制参数，**BreakAll**。 你可通过查看调用 [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) 的结果以验证是否已启用调试。 以下 PowerShell 输出显式了启用调试的结果：


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


## 启用调试时启动配置
若要调试 DSC 资源，首先需启动调用该资源的配置。 针对此示例，我们将查看调用 [WindowsFeature](windowsfeatureResource.md) 资源的简单配置以确保安装了“WindowsPowerShellWebAccess”功能：

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
编译配置后，通过调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) 启用该配置。 当本地配置管理器 (LCM) 调用
配置中的第一个资源时，配置将停止。 如果使用 `-Verbose` 和 `-Wait` 参数，该输出会显示需要输入
以启动调试的行。

```powershell
PS C:\DebugTest> Start-DscConfiguration .\PSWebAccess -Wait -Verbose
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
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.  Use the follow
ing commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
此时，LCM 已调用该资源，并到达第一个断点。 输出中的最后三行表明了如何附加到进程并启动调试资源脚本。

## 调试资源脚本

启动 PowerShell ISE 的新实例。 在控制台窗格中，输入 `Start-DscConifiguration` 输出中的最后三行作为命令，将 `<credentials>` 替换为
有效用户凭据。 下面是生成的输出。



<!--HONumber=Feb16_HO4-->
