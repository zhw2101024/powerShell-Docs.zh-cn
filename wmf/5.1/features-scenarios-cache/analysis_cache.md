# 模块分析缓存 #

从版本 5.1 开始，PowerShell 针对用于缓存有关模块的数据（如它导出的命令）的文件提供以下控制。

默认情况下，此缓存存储在文件 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 中。
缓存通常在启动时进行读取（同时搜索命令），在模块导入一段时间之后在后台线程上进行写入。

若要更改缓存的默认位置，请在启动 PowerShell 之前设置环境变量 PSModuleAnalysisCachePath。 对此环境变量进行的更改只影响子进程。
值应指定 PowerShell 有权创建和写入文件的完整路径（包括文件名）。
例如，若要禁用文件缓存，此值可以设置为无效位置

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

这会将路径设置为无效设备。 PowerShell 无法写入路径并不是错误，不过你可能会看到通过跟踪器进行报告的错误：

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

从缓存写出时，PowerShell 会检查不再存在的模块以避免进行不必要的大型缓存。
有时不需要这些检查，在这种情况下可以通过设置关闭它们

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此环境变量的设置会在当前进程中立即生效。

<!--HONumber=Jul16_HO1-->


