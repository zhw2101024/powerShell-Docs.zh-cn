---
title: 收集有关计算机的信息
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
---
# 收集有关计算机的信息
**Get-WmiObject** 是常规系统管理任务最重要的 cmdlet。 所有关键子系统设置都通过 WMI 公开。 此外，WMI 将数据视为一个或多个项的集合中的对象。 由于 Windows PowerShell 也可以使用对象，且具有允许你以相同方式处理单个和多个对象的管道，因此通过泛型 WMI 访问可以非常轻易地执行某些高级任务。

下面的示例演示如何针对任意计算机使用 **Get-WmiObject** 收集特定信息。 我们为 **ComputerName** 参数指定点值 (**.**)，它表示本地计算机。 你可以指定与可以通过 WMI 访问的任意计算机相关联的名称或 IP 地址。 若要检索有关本地计算机的信息，可以省略 **-ComputerName。**

### 列出桌面设置
我们将首先处理用于收集有关本地计算机上桌面信息的命令。

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

这将返回所有桌面的信息，无论它们是否正在使用中。

> [!NOTE]
> WMI 类返回的某些信息可能非常详细，且通常包括有关 WMI 类的元数据。 因为这些元数据属性大多具有以双下划线开头的名称，因此可以使用 Select-Object 筛选属性。 将 **[a-z]&#42;** 用作 Property 值以仅指定以字母开头的属性。 例如：

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

若要筛选出元数据，请使用管道运算符 (|) 将 Get-WmiObject 命令的结果发送到 **Select-Object -Property [a-z]&#42;**。

### 列出 BIOS 信息
WMI Win32_BIOS 类返回有关本地计算机上系统 BIOS 的高度压缩的完整信息：

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### 列出处理器信息
可以通过使用 WMI 的 **Win32_Processor** 类检索常规处理器信息 ，尽管很可能需要筛选信息：

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

对于该处理器系列的常规描述字符串，可能返回 **Win32_ComputerSystemSystemType** 属性︰

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### 列出计算机制造商和型号
**Win32_ComputerSystem** 中也提供了计算机型号信息。 标准显示输出不需要任何筛选便可提供 OEM 数据：

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

像这种来自命令的输出（它直接从某个硬件返回信息）仅相当于你拥有的数据。 某些信息未由硬件制造商正确配置，因此可能不可用。

### 列出已安装的修补程序
可以通过使用 **Win32_QuickFixEngineering** 列出所有已安装的修补程序：

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

此类将返回如下所示的修补程序列表：

```
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

为了使输出更简洁，可能需要排除某些属性。 尽管可以使用 **Get-WmiObject Property** 参数以仅选择 **HotFixID**，但这样做实际上将返回更多信息，因为默认显示所有元数据：

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId
HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

返回额外数据是因为 **Get-WmiObject** 中的 Property 参数限制从 WMI 类实例返回的属性，而不限制返回到 Windows PowerShell 的对象。 若要减少输出，请使用 **Select-Object**：

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### 列出操作系统版本信息
**Win32_OperatingSystem** 类属性包括版本和服务包信息。 你可以明确仅选择这些属性，以从 **Win32_OperatingSystem** 获取版本信息摘要：

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

也可以将通配符用于 **Select-Object Property** 参数。 因为在此处使用以 **Build** 或 **ServicePack** 开头的所有属性很重要，所以我们可以将此缩短为下列形式：

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### 列出本地用户和所有者
本地常规用户信息（许可的用户数、当前用户数和所有者名称）可通过选择 **Win32_OperatingSystem** 属性找到。 你可以明确选择使属性显示如下：

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

使用通配符的更简洁版本是：

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### 获取可用磁盘空间
若要查看本地驱动器的磁盘空间和可用空间，你可以使用 WMI Win32_LogicalDisk 类。 仅需要查看具有 DriveType 3 的实例—WMI 将此值用作固定硬盘。

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### 获取登录会话信息
可以通过 WMI Win32_LogonSession 类获取有关与用户相关联的登录会话的常规信息：

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### 获取登录到计算机的用户
可以使用 Win32_ComputerSystem 显示已登录到特定计算机系统的用户。 此命令将仅返回登录到系统桌面的用户：

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### 获取计算机的本地时间
可以通过使用 WMI Win32_LocalTime 类检索指定计算机上的当前本地时间。 由于此类默认显示所有元数据，因此可能需要使用 **Select-Object** 对其进行筛选：

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### 显示服务状态
若要查看指定计算机上所有服务的状态，可以本地使用 **Get-Service** cmdlet，如前文所述。 对于远程系统，可以使用 WMI Win32_Service 类。 如果你还使用 **Select-Object** 来筛选**Status**、**Name** 和 **DisplayName** 的结果，则输出格式将与 **Get-Service** 的输出格式几乎完全相同：

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

若要完整显示具有极长名称的临时服务的名称，可能需要使用具有 **AutoSize** 和 **Wrap** 参数的 **Format-Table**，以优化列宽并允许较长名称换行而不被截断：

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```



<!--HONumber=Apr16_HO1-->


