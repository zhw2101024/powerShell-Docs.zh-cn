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
# <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="08d50-103">获取 WMI 对象 (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="08d50-103">Getting WMI Objects (Get-CimInstance)</span></span>

## <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="08d50-104">获取 WMI 对象 (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="08d50-104">Getting WMI Objects (Get-CimInstance)</span></span>

<span data-ttu-id="08d50-105">Windows Management Instrumentation (WMI) 是 Windows 系统管理的核心技术，因为它以统一的方式公开大量信息。</span><span class="sxs-lookup"><span data-stu-id="08d50-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="08d50-106">由于 WMI 可实现的效果，用于访问 WMI 对象的 PowerShell cmdlet `Get-CimInstance` 是进行实际工作最有用的对象之一。</span><span class="sxs-lookup"><span data-stu-id="08d50-106">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="08d50-107">我们将讨论如何使用 CimCmdlets 访问 WMI 对象以及如何使用 WMI 对象执行特定操作。</span><span class="sxs-lookup"><span data-stu-id="08d50-107">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="08d50-108">列出 WMI 类</span><span class="sxs-lookup"><span data-stu-id="08d50-108">Listing WMI Classes</span></span>

<span data-ttu-id="08d50-109">大多数 WMI 用户遇到的第一个问题就是尝试了解 WMI 可执行的操作。</span><span class="sxs-lookup"><span data-stu-id="08d50-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="08d50-110">WMI 类描述了可管理的资源。</span><span class="sxs-lookup"><span data-stu-id="08d50-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="08d50-111">有成百上千的 WMI 类，其中一些包含数十个属性。</span><span class="sxs-lookup"><span data-stu-id="08d50-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="08d50-112">`Get-CimClass` 通过使 WMI 可发现来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="08d50-112">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="08d50-113">通过键入以下内容，可以获取在本地计算机上可用的 WMI 类的列表：</span><span class="sxs-lookup"><span data-stu-id="08d50-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

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

<span data-ttu-id="08d50-114">可以通过使用 ComputerName 参数指定计算机名称或 IP 地址，而从远程计算机中检索相同信息： </span><span class="sxs-lookup"><span data-stu-id="08d50-114">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="08d50-115">由于计算机正在运行的特定操作系统和已安装应用程序添加的特定 WMI 扩展，远程计算机返回的类列表可能不同。</span><span class="sxs-lookup"><span data-stu-id="08d50-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="08d50-116">使用 CIM cmdlet 连接到远程计算机时，远程计算机必须正在运行 WMI，并且所用帐户在远程计算机上必须位于本地管理员组中。</span><span class="sxs-lookup"><span data-stu-id="08d50-116">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="08d50-117">远程系统不需要安装 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="08d50-117">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="08d50-118">这让你能够管理未运行 PowerShell 的操作系统，但是你务必使 WMI 可用。</span><span class="sxs-lookup"><span data-stu-id="08d50-118">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="08d50-119">显示 WMI 类详细信息</span><span class="sxs-lookup"><span data-stu-id="08d50-119">Displaying WMI Class Details</span></span>

<span data-ttu-id="08d50-120">如果已知 WMI 类的名称，即可使用它获取信息。</span><span class="sxs-lookup"><span data-stu-id="08d50-120">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="08d50-121">例如，常用于检索有关计算机信息的 WMI 类之一 **Win32_OperatingSystem**。</span><span class="sxs-lookup"><span data-stu-id="08d50-121">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="08d50-122">尽管我们显示了所有参数，但可以用更简洁的方式表达该命令。</span><span class="sxs-lookup"><span data-stu-id="08d50-122">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="08d50-123">连接到本地系统时不需要使用 **ComputerName** 参数。</span><span class="sxs-lookup"><span data-stu-id="08d50-123">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="08d50-124">我们显示它是为了演示最常见的情况以及提醒与参数有关的事项。</span><span class="sxs-lookup"><span data-stu-id="08d50-124">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="08d50-125">Namespace  默认为 `root/CIMV2`，也可以省略。</span><span class="sxs-lookup"><span data-stu-id="08d50-125">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="08d50-126">最后，大多数 cmdlet 都允许省略通用参数的名称。</span><span class="sxs-lookup"><span data-stu-id="08d50-126">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="08d50-127">使用 `Get-CimInstance` 时，如果未指定第一个参数的名称，则 PowerShell 会将其视为 Class  参数。</span><span class="sxs-lookup"><span data-stu-id="08d50-127">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="08d50-128">这意味着最后一个命令可能是通过键入以下内容发出的：</span><span class="sxs-lookup"><span data-stu-id="08d50-128">This means the last command could have been issued by typing:</span></span>

```powershell
Get-CimInstance Win32_OperatingSystem
```

<span data-ttu-id="08d50-129">**Win32_OperatingSystem** 类拥有的属性远多于此处显示的属性。</span><span class="sxs-lookup"><span data-stu-id="08d50-129">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="08d50-130">你可以使用 Get-Member 查看所有属性。</span><span class="sxs-lookup"><span data-stu-id="08d50-130">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="08d50-131">WMI 类的属性与其他对象属性一样自动可用：</span><span class="sxs-lookup"><span data-stu-id="08d50-131">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="08d50-132">通过 Format Cmdlet 显示非默认属性</span><span class="sxs-lookup"><span data-stu-id="08d50-132">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="08d50-133">如果需要 **Win32_OperatingSystem** 类中所包含的默不显示的信息，可以通过用 **Format** cmdlet 显示它们。</span><span class="sxs-lookup"><span data-stu-id="08d50-133">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="08d50-134">例如，如果你想显示可用内存数据，请键入：</span><span class="sxs-lookup"><span data-stu-id="08d50-134">For example, if you want to display available memory data, type:</span></span>

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
> <span data-ttu-id="08d50-135">由于通配符支持 `Format-Table` 中的属性名，因此最终管道元素可缩减为 `Format-Table -Property Total*Memory*, Free*`</span><span class="sxs-lookup"><span data-stu-id="08d50-135">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="08d50-136">通过键入以下内容将内存数据的格式设置为列表可提高其可读性：</span><span class="sxs-lookup"><span data-stu-id="08d50-136">The memory data might be more readable if you format it as a list by typing:</span></span>

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
