---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 获取 WMI 对象 (Get WmiObject)
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030210"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="53d1a-103">获取 WMI 对象 (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="53d1a-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="53d1a-104">获取 WMI 对象 (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="53d1a-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="53d1a-105">Windows Management Instrumentation (WMI) 是 Windows 系统管理的核心技术，因为它以统一的方式公开大量信息。</span><span class="sxs-lookup"><span data-stu-id="53d1a-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="53d1a-106">由于 WMI 可实现的效果，用于访问 WMI 对象的 Windows PowerShell cmdlet **Get-WmiObject** 是进行实际工作最有用的对象之一。</span><span class="sxs-lookup"><span data-stu-id="53d1a-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="53d1a-107">我们将讨论如何使用 Get-WmiObject 访问 WMI 对象以及如何使用 WMI 对象执行特定操作。</span><span class="sxs-lookup"><span data-stu-id="53d1a-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="53d1a-108">列出 WMI 类</span><span class="sxs-lookup"><span data-stu-id="53d1a-108">Listing WMI Classes</span></span>

<span data-ttu-id="53d1a-109">大多数 WMI 用户遇到的第一个问题就是尝试了解 WMI 可执行的操作。</span><span class="sxs-lookup"><span data-stu-id="53d1a-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="53d1a-110">WMI 类描述了可管理的资源。</span><span class="sxs-lookup"><span data-stu-id="53d1a-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="53d1a-111">有成百上千的 WMI 类，其中一些包含数十个属性。</span><span class="sxs-lookup"><span data-stu-id="53d1a-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="53d1a-112">**Get-WmiObject** 通过使 WMI 可发现来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="53d1a-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="53d1a-113">通过键入以下内容，可以获取在本地计算机上可用的 WMI 类的列表：</span><span class="sxs-lookup"><span data-stu-id="53d1a-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="53d1a-114">可以通过使用 ComputerName 参数指定计算机名称或 IP 地址，而从远程计算机中检索相同信息：</span><span class="sxs-lookup"><span data-stu-id="53d1a-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="53d1a-115">由于计算机正在运行的特定操作系统和已安装应用程序添加的特定 WMI 扩展，远程计算机返回的类列表可能不同。</span><span class="sxs-lookup"><span data-stu-id="53d1a-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="53d1a-116">使用 Get-WmiObject 连接到远程计算机时，远程计算机必须运行 WMI，并且在默认配置下，所用帐户在远程计算机上必须位于本地管理员组中。</span><span class="sxs-lookup"><span data-stu-id="53d1a-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="53d1a-117">远程系统不需要安装 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="53d1a-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="53d1a-118">这让你能够管理未运行 Windows PowerShell 的操作系统，但爱你过务必使 WMI 可用。</span><span class="sxs-lookup"><span data-stu-id="53d1a-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="53d1a-119">连接到本地系统时，甚至可以包括 ComputerName。</span><span class="sxs-lookup"><span data-stu-id="53d1a-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="53d1a-120">可以将本地计算机的名称、其 IP 地址（或环回地址 127.0.0.1） 或 WMI 样式“.”作为计算机名。</span><span class="sxs-lookup"><span data-stu-id="53d1a-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="53d1a-121">如果在名为 Admin01 且 IP 地址为 192.168.1.90 计算机上运行 Windows PowerShell，以下所有命令将返回该计算机的 WMI 类列表：</span><span class="sxs-lookup"><span data-stu-id="53d1a-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="53d1a-122">Get-WmiObject 默认使用 root/cimv2 命名空间。</span><span class="sxs-lookup"><span data-stu-id="53d1a-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="53d1a-123">如果你想指定其他 WMI 命名空间，请使用 **Namespace** 参数并指定相应的命名空间路径：</span><span class="sxs-lookup"><span data-stu-id="53d1a-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="53d1a-124">显示 WMI 类详细信息</span><span class="sxs-lookup"><span data-stu-id="53d1a-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="53d1a-125">如果已知 WMI 类的名称，即可使用它获取信息。</span><span class="sxs-lookup"><span data-stu-id="53d1a-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="53d1a-126">例如，常用于检索有关计算机信息的 WMI 类之一 **Win32_OperatingSystem**。</span><span class="sxs-lookup"><span data-stu-id="53d1a-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="53d1a-127">尽管我们显示了所有参数，但可以用更简洁的方式表达该命令。</span><span class="sxs-lookup"><span data-stu-id="53d1a-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="53d1a-128">连接到本地系统时不需要使用 **ComputerName** 参数。</span><span class="sxs-lookup"><span data-stu-id="53d1a-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="53d1a-129">我们显示它是为了演示最常见的情况以及提醒与参数有关的事项。</span><span class="sxs-lookup"><span data-stu-id="53d1a-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="53d1a-130">**Namespace** 默认为 root/cimv2，也可以省略。</span><span class="sxs-lookup"><span data-stu-id="53d1a-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="53d1a-131">最后，大多数 cmdlet 都允许省略通用参数的名称。</span><span class="sxs-lookup"><span data-stu-id="53d1a-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="53d1a-132">使用 Get-WmiObject 时，如果未指定第一个参数的名称，则 Windows PowerShell 会将其视为 **Class** 参数。</span><span class="sxs-lookup"><span data-stu-id="53d1a-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="53d1a-133">这意味着最后一个命令可能是通过键入以下内容发出的：</span><span class="sxs-lookup"><span data-stu-id="53d1a-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="53d1a-134">**Win32_OperatingSystem** 类拥有的属性远多于此处显示的属性。</span><span class="sxs-lookup"><span data-stu-id="53d1a-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="53d1a-135">你可以使用 Get-Member 查看所有属性。</span><span class="sxs-lookup"><span data-stu-id="53d1a-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="53d1a-136">WMI 类的属性与其他对象属性一样自动可用：</span><span class="sxs-lookup"><span data-stu-id="53d1a-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="53d1a-137">通过 Format Cmdlet 显示非默认属性</span><span class="sxs-lookup"><span data-stu-id="53d1a-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="53d1a-138">如果需要 **Win32_OperatingSystem** 类中所包含的默不显示的信息，可以通过用 **Format** cmdlet 显示它们。</span><span class="sxs-lookup"><span data-stu-id="53d1a-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="53d1a-139">例如，如果你想显示可用内存数据，请键入：</span><span class="sxs-lookup"><span data-stu-id="53d1a-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="53d1a-140">由于通配符支持 Format-Table  中的属性名，因此最终管道元素可缩减为 `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="53d1a-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="53d1a-141">通过键入以下内容将内存数据的格式设置为列表可提高其可读性：</span><span class="sxs-lookup"><span data-stu-id="53d1a-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
