---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: Get-Test-Set
ms.openlocfilehash: e4aa7770bb5fc8b916b0c0a6488b1ccc0ef0ade9
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229518"
---
# <a name="get-test-set"></a>Get-Test-Set

>适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

![获取、测试并设置](/media/get-test-set.png)

PowerShell Desired State Configuration 是围绕 Get、Test 和 Set 进程构建的。 每个 DSC [资源](resources.md) 都包含完成这些操作的方法。 在[配置](../configurations/configurations.md)中，定义资源块来填充成为资源的 Get、Test 和 Set 方法参数的键。

这是 Service 资源块的语法。 Service 资源配置 Windows 服务。

```syntax
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

Service 资源的 Get、Test 和 Set 方法将具有接受这些值的参数块。

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> 用于定义资源的语言和方法决定了如何定义 Get、Test 和 Set 方法。

由于 Service 资源只有一个必需的键 (`Name`)，因此 Service 块资源可以非常简单，如下所示：

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

编译上述配置时，为键指定的值存储在生成的“.mof”文件中。 有关详细信息，请参阅 [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)。

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

应用时，[本地配置管理器](../managing-nodes/metaConfig.md) (LCM) 将从“.mof”文件读取值“Spooler”，并将其传递给 Service 资源“MyService”实例的 Get、Test 和 Set 方法的 `-Name` 参数。

## <a name="get"></a>Get

资源的 Get 方法，检索在目标节点上配置的资源的状态。 此状态作为[哈希表](/powershell/module/microsoft.powershell.core/about/about_hash_tables)返回。 哈希表的键是资源接受的可配置值或参数。

Get 方法直接映射到 [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet。 调用 `Get-DSCConfiguration` 时，LCM 运行当前应用配置中每个资源的 Get 方法。 LCM 使用存储在“.mof”中的键值作为每个相应资源实例的参数。

这是配置“Spooler”服务的 Service 资源的示例输出。

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

输出显示了 Service 资源可配置的当前值属性。

```syntax
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

## <a name="test"></a>测试

资源的 Test 方法确定目标节点当前是否符合资源的所需状态。 Test 方法返回 `$True` 或 `$False` 以仅指示节点是否符合。
调用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) 时，LCM 调用当前应用配置中每个资源的 Test 方法。 LCM 使用存储在“.mof”中的键值作为每个相应资源实例的参数。

如果任何单个资源的 Test 结果是 `$False`，则 `Test-DSCConfiguration` 返回 `$False`，表示该节点不符合。 如果所有资源的 Test 方法都返回 `$True`，则 `Test-DSCConfiguration` 返回 `$True`，表示该节点符合。

```powershell
Test-DSCConfiguration
```

```output
True
```

从 PowerShell 5.0 开始，添加了 `-Detailed` 参数。 指定 `-Detailed` 将导致 `Test-DSCConfiguration` 返回一个对象，该对象包含符合和不符合资源的结果集合。

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

有关详细信息，请参阅 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Set

资源的 Set 方法尝试强制节点符合资源的所需状态。 Set 方法旨在幂等，这意味着 Set 可以多次运行，并始终得到相同的结果而没有错误。  当运行 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration) 时，LCM 在当前应用的配置中循环切换每个资源。 LCM 从“.mof”文件检索当前资源实例的键值，并使用它们作为 Test 方法的参数。 如果 Test 方法返回 `$True`，则节点符合当前资源，并跳过 Set 方法。 如果 Test 返回 `$False`，则节点不符合。  LCM 将资源实例的键值作为参数传递给资源的 Set 方法，使节点恢复符合性。

通过指定 `-Verbose` 和 `-Wait` 参数，可以查看 `Start-DSCConfiguration` cmdlet的进度。 在此示例中，节点已具有符合性。 `Verbose` 输出表明跳过了 Set 方法。

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>另请参阅

- [Azure Automation DSC 概述](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [设置 SMB 请求服务器](../pull-server/pullServerSMB.md)
- [配置请求客户端](../pull-server/pullClientConfigID.md)
