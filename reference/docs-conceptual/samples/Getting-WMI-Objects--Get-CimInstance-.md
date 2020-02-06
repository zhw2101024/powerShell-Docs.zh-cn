---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 获取 WMI 对象 - Get-CimInstance
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "77002647"
---
# <a name="getting-wmi-objects-get-ciminstance"></a>获取 WMI 对象 (Get-CimInstance)

## <a name="getting-wmi-objects-get-ciminstance"></a>获取 WMI 对象 (Get-CimInstance)

Windows Management Instrumentation (WMI) 是 Windows 系统管理的核心技术，因为它以统一的方式公开大量信息。 由于 WMI 可实现的效果，用于访问 WMI 对象的 PowerShell cmdlet `Get-CimInstance` 是进行实际工作最有用的对象之一。 我们将讨论如何使用 CimCmdlets 访问 WMI 对象以及如何使用 WMI 对象执行特定操作。

### <a name="listing-wmi-classes"></a>列出 WMI 类

大多数 WMI 用户遇到的第一个问题就是尝试了解 WMI 可执行的操作。 WMI 类描述了可管理的资源。 有成百上千的 WMI 类，其中一些包含数十个属性。

`Get-CimClass` 通过使 WMI 可发现来解决此问题。 通过键入以下内容，可以获取在本地计算机上可用的 WMI 类的列表：

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

可以通过使用 ComputerName 参数指定计算机名称或 IP 地址，而从远程计算机中检索相同信息： 

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

由于计算机正在运行的特定操作系统和已安装应用程序添加的特定 WMI 扩展，远程计算机返回的类列表可能不同。

> [!NOTE]
> 使用 CIM cmdlet 连接到远程计算机时，远程计算机必须正在运行 WMI，并且所用帐户在远程计算机上必须位于本地管理员组中。
> 远程系统不需要安装 PowerShell。 这让你能够管理未运行 PowerShell 的操作系统，但是你务必使 WMI 可用。

### <a name="displaying-wmi-class-details"></a>显示 WMI 类详细信息

如果已知 WMI 类的名称，即可使用它获取信息。 例如，常用于检索有关计算机信息的 WMI 类之一 **Win32_OperatingSystem**。

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

尽管我们显示了所有参数，但可以用更简洁的方式表达该命令。
连接到本地系统时不需要使用 **ComputerName** 参数。 我们显示它是为了演示最常见的情况以及提醒与参数有关的事项。 Namespace  默认为 `root/CIMV2`，也可以省略。 最后，大多数 cmdlet 都允许省略通用参数的名称。 使用 `Get-CimInstance` 时，如果未指定第一个参数的名称，则 PowerShell 会将其视为 Class  参数。 这意味着最后一个命令可能是通过键入以下内容发出的：

```powershell
Get-CimInstance Win32_OperatingSystem
```

**Win32_OperatingSystem** 类拥有的属性远多于此处显示的属性。 你可以使用 Get-Member 查看所有属性。 WMI 类的属性与其他对象属性一样自动可用：

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>通过 Format Cmdlet 显示非默认属性

如果需要 **Win32_OperatingSystem** 类中所包含的默不显示的信息，可以通过用 **Format** cmdlet 显示它们。 例如，如果你想显示可用内存数据，请键入：

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> 由于通配符支持 `Format-Table` 中的属性名，因此最终管道元素可缩减为 `Format-Table -Property Total*Memory*, Free*`

通过键入以下内容将内存数据的格式设置为列表可提高其可读性：

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
