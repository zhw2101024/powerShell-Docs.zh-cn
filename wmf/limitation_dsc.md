# Desired State Configuration (DSC) 已知问题和限制

重大更改：DSC 配置中用于对密码进行加密/解密的证书在安装 WMF 5.0 RTM 后可能失效
--------------------------------------------------------------------------------------------------------------------------------

在 WMF 4.0 和 WMF 5.0 预览版本中，DSC 不允许配置中的密码长度超过 121 个字符。 尽管使用较长的强密码更好，但 DSC 强制使用短密码。 此项重大更改使 DSC 配置中的密码可为任意长度。

**解决方法：**使用数据加密或密钥加密密钥用法和文档加密增强型密钥用法 (1.3.6.1.4.1.311.80.1) 重新创建证书。 Technet 文章 <https://technet.microsoft.com/en-us/library/dn807171.aspx> 中提供了详细信息。


安装 WMF 5.0 RTM 后 DSC cmdlet 可能失败
------------------------------------------------------------------------------------
安装 WMF 5.0 RTM 后，Start-DscConfiguration 和其他 DSC cmdlet 可能失败并出现以下错误：
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**解决方法：**通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行）来删除 DSCEngineCache.mof：
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


如果在 WMF 5.0 生产预览版的基础上安装 WMF 5.0 RTM，DSC cmdlet 可能失效
------------------------------------------------------
**解决方法：**在提升的 PowerShell 会话中运行以下命令（以管理员身份运行）：
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


在 DebugMode 中使用 Get-DscConfiguration 时，LCM 可能进入不稳定状态
-------------------------------------------------------------------------------

如果 LCM 处于 DebugMode，按 Ctrl+C 来停止 Get-DscConfiguration 处理可能导致 LCM 进入不稳定状态，从而导致大部分 DSC cmdlet 失效。

**解决方法：**不要在调试 Get-DscConfiguration cmdlet 时按 Ctrl+C。


在 DebugMode 中，Stop-DscConfiguration 可能挂起
------------------------------------------------------------------------------------------------------------------------
如果 LCM 处于 DebugMode，则当试图停止由 Get-DscConfiguration 启动的操作时，Stop-DscConfiguration 可能挂起

**解决方法：**按“[DSC 资源脚本调试](#dsc-resource-script-debugging)”部分中所述完成由 Get-DscConfiguration 所启动操作的调试。


DebugMode 中不显示详细错误消息
-----------------------------------------------------------------------------------
如果 LCM 处于 DebugMode，DSC 资源中将不显示详细错误消息。

**解决方法：**禁用 *DebugMode* 以从资源中查看详细消息


Get-DscConfigurationStatus cmdlet 无法检索 Invoke-DscResource 操作
--------------------------------------------------------------------------------------
使用 Invoke-DscResource cmdlet 直接调用资源的方法后，将无法再通过 Get-DscConfigurationStatus 检索此类操作的记录。

**解决方法：**无。


Get-DscConfigurationStatus 将请求周期操作返回为 *Consistency* 类型
---------------------------------------------------------------------------------
将节点设置为 PULL 刷新模式时，对于所执行的每个请求操作，Get-DscConfigurationStatus cmdlet 会将操作类型报告为 *Consistency* 而不是 *Initial*

**解决方法：**无。

Invoke-DscResource cmdlet 不按生成消息的顺序返回消息
---------------------------------------------------------------------------------
Invoke-DscResource cmdlet 不按 LCM 或 DSC 资源生成详细、警告和错误消息的顺序返回这些消息。

**解决方法：**无。


与 Invoke-DscResource 一起使用时，无法轻松调试 DSC 资源
-----------------------------------------------------------------------
LCM 在调试模式下的运行时（请参阅 [DSC 资源脚本调试](#dsc-resource-script-debugging)以了解详细信息），Invoke-DscResource cmdlet 不会给出有关连接以便调试的运行空间的信息。
**解决方法：**使用 cmdlet **Get-PSHostProcessInfo**、**Enter-PSHostProcess**、**Get-Runspace** 和 **Debug-Runspace** 来发现并连接到运行空间，以便调试 DSC 资源。

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


同一节点的各部分配置文档不能具有相同的资源名称
------------------------------------------------------------------------------------------

对于部署到单个节点上的多个部分配置，相同的资源名称可能导致运行时错误。

**解决方法：**即使对不同部分配置中的相同资源也使用不同的名称。


Start-DscConfiguration –UseExisting 不可与 -Credential 一起使用
------------------------------------------------------------------

使用具有 –UseExisting 参数的 Start-DscConfiguration 时，将忽略 –Credential 参数。 DSC 使用默认进程标识继续执行操作。 当需要其他凭据才可在远程节点上继续执行时，这将导致错误。

**解决方法：**使用 CIM 会话进行远程 DSC 操作：
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


将 IPv6 地址作为 DSC 配置中的节点名称
--------------------------------------------------
此版本中不支持将 IPv6 地址作为 DSC 配置脚本中的节点名称。

**解决方法：**无。


调试基于类的 DSC 资源
--------------------------------------
此版本中不支持调试基于类的 DSC 资源。

**解决方法：**无。


在多次调用 DSC 资源之间，将不保留在 DSC 基于类的资源中 $script 作用域内定义的变量和函数 
-------------------------------------------------------------------------------------------------------------------------------------

如果配置使用任何基于类的资源，而该资源包含在 $script 作用域内定义的变量或函数，则对 Start-DSCConfiguration 的多个连续调用将失败。

**解决方法：**在 DSC 资源类本身中定义所有变量和函数。 没有 $script 作用域的变量/函数。


在资源使用 PSDscRunAsCredential 时进行 DSC 资源调试
----------------------------------------------------------------------
在此版本中，当资源使用配置中的 *PSDscRunAsCredential* 属性时，不支持进行 DSC 资源调试。

**解决方法：**无。


不支持将 PsDscRunAsCredential 用于 DSC 复合资源
----------------------------------------------------------------

**解决方法：**尽可能使用 Credential 属性。 示例 ServiceSet 和 WindowsFeatureSet


*Get-DscResource -Syntax* 不能正确地反映 PsDscRunAsCredential
-------------------------------------------------------------------------
当资源将 Get-DscResource -Syntax 标记为强制使用或不支持它时，它将不能正确地反映 PsDscRunAsCredential。

**解决方法：**无。 但是，使用 IntelliSense 时，在 ISE 中创作配置可以反映关于 PsDscRunAsCredential 属性的正确元数据。


WindowsOptionalFeature 在 Windows 7 中不可用
-----------------------------------------------------

WindowsOptionalFeature DSC 资源在 Windows 7 中不可用。 此资源需要 DISM 模块以及在 Windows 8 和更新版 Windows 操作系统中开始提供的 DISM cmdlet。

对于基于类的 DSC 资源，Import-DscResource -ModuleVersion 可能未按预期运行   
------------------------------------------------------------------------------------------
如果编译节点具有多个版本的基于类的 DSC 资源模块，`Import-DscResource -ModuleVersion` 不会获取指定版本，并导致产生以下编译错误。

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**解决方法：**通过定义 *ModuleSpecification* 对象将所需版本导入到 `-ModuleName`，`RequiredVersion` 密钥按如下所示指定：
``` PowerShell  
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}  
```  



<!--HONumber=May16_HO1-->


