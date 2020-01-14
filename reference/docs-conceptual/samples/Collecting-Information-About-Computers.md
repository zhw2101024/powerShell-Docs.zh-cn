---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 收集有关计算机的信息
ms.openlocfilehash: 9407ff15b3c3ca6b3adab60d4d01d957c599e79e
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737230"
---
# <a name="collecting-information-about-computers"></a>收集有关计算机的信息

CimCmdlets 模块中的 cmdlet 是对常规系统管理任务最重要的 cmdlet  。 所有关键子系统设置都通过 WMI 公开。 此外，WMI 将数据视为一个或多个项的集合中的对象。 由于 Windows PowerShell 也可以使用对象，且具有允许你以相同方式处理单个和多个对象的管道，因此通过泛型 WMI 访问可以非常轻易地执行某些高级任务。

## <a name="listing-desktop-settings"></a>列出桌面设置

我们将首先处理用于收集有关本地计算机上桌面信息的命令。

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

这将返回所有桌面的信息，无论它们是否正在使用中。

> [!NOTE]
> WMI 类返回的某些信息可能非常详细，且通常包括有关 WMI 类的元数据。

因为这些元数据属性大多具有以 Cim 开头的名称，因此可以使用 `Select-Object` 筛选属性  。 指定值为“Cim*”的 -ExcludeProperty 参数  。 例如：

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

若要筛选掉元数据，请使用管道运算符 (|)，将 `Get-CimInstance` 命令的结果发送到 `Select-Object -ExcludeProperty "CIM*"`。

## <a name="listing-bios-information"></a>列出 BIOS 信息

WMI Win32_BIOS 类返回有关本地计算机上系统 BIOS 的高度压缩的完整信息  ：

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a>列出处理器信息

可以通过使用 WMI 的 **Win32_Processor** 类检索常规处理器信息 ，尽管很可能需要筛选信息：

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

对于该处理器系列的常规描述字符串，可以仅返回 **SystemType** 属性：

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>列出计算机制造商和型号

**Win32_ComputerSystem** 中也提供了计算机型号信息。 标准显示输出不需要任何筛选便可提供 OEM 数据：

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

像这种来自命令的输出（它直接从某个硬件返回信息）仅相当于你拥有的数据。 某些信息未由硬件制造商正确配置，因此可能不可用。

## <a name="listing-installed-hotfixes"></a>列出已安装的修补程序

可以通过使用 **Win32_QuickFixEngineering** 列出所有已安装的修补程序：

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

此类将返回如下所示的修补程序列表：

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

为了使输出更简洁，可能需要排除某些属性。 尽管可以使用 `Get-CimInstance` 的 Property 参数以仅选择 HotFixID，但这样做实际上将返回更多信息，因为默认显示所有元数据   ：

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

返回额外数据是因为 `Get-CimInstance` 中的 Property 参数限制从 WMI 类实例返回的属性，而不限制返回到 PowerShell 的对象。  若要减少输出，请使用 `Select-Object`：

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>列出操作系统版本信息

**Win32_OperatingSystem** 类属性包括版本和服务包信息。 你可以明确仅选择这些属性，以从 **Win32_OperatingSystem** 获取版本信息摘要：

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

也可以将通配符用于 `Select-Object` 的 Property 参数  。 因为在此处使用以 **Build** 或 **ServicePack** 开头的所有属性很重要，所以我们可以将此缩短为下列形式：

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a>列出本地用户和所有者

本地常规用户信息（许可的用户数、当前用户数和所有者名称）可通过选择 Win32_OperatingSystem 类的属性找到  。 你可以明确选择使属性显示如下：

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

使用通配符的更简洁版本是：

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>获取可用磁盘空间

若要查看本地驱动器的磁盘空间和可用空间，可以使用 Win32_LogicalDisk WMI 类。
仅需要查看具有 DriveType 3（WMI 将此值用作固定硬盘）的实例。

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a>获取登录会话信息

可通过 Win32_LogonSession WMI 类获取有关与用户相关联的登录会话的常规信息  ：

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>获取登录到计算机的用户

可以使用 Win32_ComputerSystem 显示已登录到特定计算机系统的用户。 此命令将仅返回登录到系统桌面的用户：

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a>获取计算机的本地时间

可以通过使用 Win32_LocalTime WMI 类检索指定计算机上的当前本地时间  。

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a>显示服务状态

若要查看指定计算机上所有服务的状态，可以本地使用 `Get-Service` cmdlet。 对于远程系统，可以使用 Win32_Service WMI 类  。 如果还使用 `Select-Object` 来筛选 Status、Name 和 DisplayName 的结果，则输出格式将与 `Get-Service` 的输出格式几乎完全相同    ：

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

若要完整显示具有极长名称的临时服务的名称，可能需要使用具有 AutoSize 和 Wrap 参数的 `Format-Table`，用于优化列宽并允许较长名称换行而不是被截断   ：

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
