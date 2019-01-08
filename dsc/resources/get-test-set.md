---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 获取测试设置
ms.openlocfilehash: e46710954679bf20f4536c6efbcbd4dafd9e629e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400464"
---
# <a name="get-test-set"></a>获取测试设置

>适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.0

![获取、测试并设置](/media/get-test-set.png)

PowerShell Desired State Configuration 构造周围**获取**，**测试**，并**设置**过程。 DSC[资源](resources.md)每个都包含用于完成这些操作的方法。 在[配置](../configurations/configurations.md)，定义资源块来填充成为资源的参数的键**获取**，**测试**，以及**设置**方法。

这是语法**服务**资源块。 **服务**资源配置 Windows 服务。

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

**获取**，**测试**，并**设置**方法**服务**资源将具有接受这些值的参数块。

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
> 语言和方法用于定义该资源确定如何**获取**，**测试**，并**设置**将定义方法。

因为**服务**资源仅有一个必需的密钥 (`Name`)、 一个**服务**块资源可能简单，如下：

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

编译上面的配置时，生成的".mof"文件中存储指定键的值。 有关详细信息，请参阅[MOF](/windows/desktop/wmisdk/managed-object-format--mof-)。

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

当应用时，[本地配置管理器](../managing-nodes/metaConfig.md)将从".mof"文件读取值"后台处理程序"并将其传递给`-Name`参数**获取**，**测试**，并**设置**"MyService"实例的方法**服务**资源。

## <a name="get"></a>Get

**获取**的资源，方法检索资源的状态，因为在目标节点上进行此配置。 此状态下返回作为[哈希表](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。 键**哈希表**可配置的值或参数，将为该资源接受。

**获取**方法直接映射到[Get-dscconfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet。 当您调用`Get-DSCConfiguration`，则 LCM 将运行**获取**当前应用的配置的每个资源的方法。 LCM 使用为每个相应的资源实例的参数".mof"文件中存储的密钥值。

这是示例输出**服务**会将"Spooler"服务配置的资源。

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

该输出显示当前值属性可由配置**服务**资源。

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

**测试**资源的方法确定目标节点是否与资源的当前兼容*所需状态*。 **测试**方法将返回`$True`或`$False`仅以指示节点是否符合。
当您调用[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)，LCM 调用**测试**当前应用的配置的每个资源的方法。 LCM 使用为每个相应的资源实例的参数".mof"文件中存储的密钥值。

如果任何单独的资源的结果**测试**是`$False`，`Test-DSCConfiguration`返回`$False`，该值指示该节点不符合。 如果所有资源**测试**方法返回`$True`，`Test-DSCConfiguration`返回`$True`以指示该节点是符合。

```powershell
Test-DSCConfiguration
```

```output
True
```

从 PowerShell 5.0 开始`-Detailed`参数已添加。 指定`-Detailed`导致`Test-DSCConfiguration`返回一个对象，包含集合的结果符合和不合规资源。

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

有关详细信息，请参阅[测试 DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Set

**设置**资源的方法尝试强制符合资源的节点*所需状态*。 **设置**方法旨在**幂等**，这意味着**设置**可能运行多次，并且始终获得相同的结果不包含错误。  在运行时[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)、 LCM 循环的当前应用配置的每个资源。 LCM".mof"文件从检索当前的资源实例的密钥值，并使用作为参数**测试**方法。 如果**测试**方法将返回`$True`，该节点是符合当前的资源，并且**设置**方法跳过。 如果**测试**返回`$False`，该节点是不符合标准。  LCM 资源实例的密钥值将作为参数传递到的资源**设置**方法中，节点恢复到符合性。

通过指定`-Verbose`并`-Wait`参数，可以查看进度`Start-DSCConfiguration`cmdlet。 在此示例中，该节点是已经符合。 `Verbose`输出指示**设置**方法已跳过。

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

- [Azure Automation DSC 概述](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [设置 SMB 请求服务器](../pull-server/pullServerSMB.md)
- [配置请求客户端](../pull-server/pullClientConfigID.md)
