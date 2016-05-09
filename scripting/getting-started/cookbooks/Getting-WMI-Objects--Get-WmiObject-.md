---
title: 获取 WMI 对象 (Get-WmiObject)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
---
# 获取 WMI 对象 (Get-WmiObject)

## 获取 WMI 对象 (Get-WmiObject)
Windows Management Instrumentation (WMI) 是 Windows 系统管理的核心技术，因为它以统一的方式公开大量信息。 由于 WMI 可实现的效果，用于访问 WMI 对象的 Windows PowerShell cmdlet **Get-WmiObject** 是进行实际工作最有用的对象之一。 我们将讨论如何使用 Get-WmiObject 访问 WMI 对象以及如何使用 WMI 对象执行特定操作。

### 列出 WMI 类
大多数 WMI 用户遇到的第一个问题就是尝试了解 WMI 可执行的操作。 WMI 类描述了可管理的资源。 有成百上千的 WMI 类，其中一些包含数十个属性。

**Get-WmiObject** 通过使 WMI 可发现来解决此问题。 通过键入以下内容，可以获取在本地计算机上可用的 WMI 类的列表：

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

可以通过使用 ComputerName 参数指定计算机名称或 IP 地址，而从远程计算机中检索相同信息：

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

由于计算机正在运行的特定操作系统和已安装应用程序添加的特定 WMI 扩展，远程计算机返回的类列表可能不同。

> [!NOTE]
> 使用 Get-WmiObject 连接到远程计算机时，远程计算机必须运行 WMI，并且在默认配置下，所用帐户在远程计算机上必须位于本地管理员组中。 远程系统不需要安装 Windows PowerShell。 这让你能够管理未运行 Windows PowerShell 的操作系统，但爱你过务必使 WMI 可用。

连接到本地系统时，甚至可以包括 ComputerName。 可以将本地计算机的名称、其 IP 地址（或环回地址 127.0.0.1） 或 WMI 样式“.”作为计算机名。 如果在名为 Admin01 且 IP 地址为 192.168.1.90 计算机上运行 Windows PowerShell，以下所有命令将返回该计算机的 WMI 类列表：

```
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject 默认使用 root/cimv2 命名空间。 如果你想指定其他 WMI 命名空间，请使用 **Namespace** 参数并指定相应的命名空间路径：

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### 显示 WMI 类详细信息
如果已知 WMI 类的名称，即可使用它获取信息。 例如，常用于检索有关计算机信息的 WMI 类之一 **Win32_OperatingSystem**。

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

尽管我们显示了所有参数，但可以用更简洁的方式表达该命令。 连接到本地系统时不需要使用 **ComputerName** 参数。 我们显示它是为了演示最常见的情况以及提醒与参数有关的事项。 **Namespace** 默认为 root/cimv2，也可以省略。 最后，大多数 cmdlet 都允许省略通用参数的名称。 使用 Get-WmiObject 时，如果未指定第一个参数的名称，则 Windows PowerShell 会将其视为 **Class** 参数。 这意味着最后一个命令可能是通过键入以下内容发出的：

```
Get-WmiObject Win32_OperatingSystem
```

**Win32_OperatingSystem** 类拥有的属性远多于此处显示的属性。 你可以使用 Get-Member 查看所有属性。 WMI 类的属性与其他对象属性一样自动可用：

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### 通过 Format Cmdlet 显示非默认属性
如果需要 **Win32_OperatingSystem** 类中所包含的默不显示的信息，可以通过用 **Format** cmdlet 显示它们。 例如，如果你想显示可用内存数据，请键入：

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMem FreePhysicalMem FreeVirtualMemo FreeSpaceInPagi
                              ory              ry         ngFiles
--------------- --------------- --------------- --------------- ---------------
        2097024          785904          305808         2056724         1558232
```

> [!NOTE]
> 通配符可与 **Format-Table** 中的属性名称一起使用，因此最终管道元素可缩减为 **Format-Table -Property TotalV&#42;,Free&#42;**

通过键入以下内容将内存数据的格式设置为列表可提高其可读性：

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```



<!--HONumber=Apr16_HO1-->


