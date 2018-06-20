---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 收集有关计算机的信息
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ca92474eaf6fa546c3d6450f5a282e45157018a8
ms.sourcegitcommit: 4a841ebda3339ae2477e0f5f5be8c01740221232
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33677308"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="76102-103">收集有关计算机的信息</span><span class="sxs-lookup"><span data-stu-id="76102-103">Collecting Information About Computers</span></span>

<span data-ttu-id="76102-104">CimCmdlets 模块中的 cmdlet 是对常规系统管理任务最重要的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76102-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="76102-105">所有关键子系统设置都通过 WMI 公开。</span><span class="sxs-lookup"><span data-stu-id="76102-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="76102-106">此外，WMI 将数据视为一个或多个项的集合中的对象。</span><span class="sxs-lookup"><span data-stu-id="76102-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="76102-107">由于 Windows PowerShell 也可以使用对象，且具有允许你以相同方式处理单个和多个对象的管道，因此通过泛型 WMI 访问可以非常轻易地执行某些高级任务。</span><span class="sxs-lookup"><span data-stu-id="76102-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="76102-108">以下示例演示如何针对任意计算机使用 `Get-CimInstance` 收集特定信息。</span><span class="sxs-lookup"><span data-stu-id="76102-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="76102-109">我们为 **ComputerName** 参数指定点值 (**.**)，它表示本地计算机。</span><span class="sxs-lookup"><span data-stu-id="76102-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="76102-110">你可以指定与可以通过 WMI 访问的任意计算机相关联的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="76102-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="76102-111">若要检索有关本地计算机的信息，可以省略 ComputerName 参数。</span><span class="sxs-lookup"><span data-stu-id="76102-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="76102-112">列出桌面设置</span><span class="sxs-lookup"><span data-stu-id="76102-112">Listing Desktop Settings</span></span>

<span data-ttu-id="76102-113">我们将首先处理用于收集有关本地计算机上桌面信息的命令。</span><span class="sxs-lookup"><span data-stu-id="76102-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="76102-114">这将返回所有桌面的信息，无论它们是否正在使用中。</span><span class="sxs-lookup"><span data-stu-id="76102-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="76102-115">WMI 类返回的某些信息可能非常详细，且通常包括有关 WMI 类的元数据。</span><span class="sxs-lookup"><span data-stu-id="76102-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="76102-116">因为这些元数据属性大多具有以 Cim 开头的名称，因此可以使用 `Select-Object` 筛选属性。</span><span class="sxs-lookup"><span data-stu-id="76102-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="76102-117">指定值为“Cim\*”的 -ExcludeProperty 参数。</span><span class="sxs-lookup"><span data-stu-id="76102-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="76102-118">例如：</span><span class="sxs-lookup"><span data-stu-id="76102-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="76102-119">若要筛选掉元数据，请使用管道运算符 (|)，将 `Get-CimInstance` 命令的结果发送到 `Select-Object -ExcludeProperty "CIM*"`。</span><span class="sxs-lookup"><span data-stu-id="76102-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="76102-120">列出 BIOS 信息</span><span class="sxs-lookup"><span data-stu-id="76102-120">Listing BIOS Information</span></span>

<span data-ttu-id="76102-121">WMI Win32_BIOS 类返回有关本地计算机上系统 BIOS 的高度压缩的完整信息：</span><span class="sxs-lookup"><span data-stu-id="76102-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="76102-122">列出处理器信息</span><span class="sxs-lookup"><span data-stu-id="76102-122">Listing Processor Information</span></span>

<span data-ttu-id="76102-123">可以通过使用 WMI 的 **Win32_Processor** 类检索常规处理器信息 ，尽管很可能需要筛选信息：</span><span class="sxs-lookup"><span data-stu-id="76102-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="76102-124">对于该处理器系列的常规描述字符串，可以仅返回 **SystemType** 属性：</span><span class="sxs-lookup"><span data-stu-id="76102-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="76102-125">列出计算机制造商和型号</span><span class="sxs-lookup"><span data-stu-id="76102-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="76102-126">**Win32_ComputerSystem** 中也提供了计算机型号信息。</span><span class="sxs-lookup"><span data-stu-id="76102-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="76102-127">标准显示输出不需要任何筛选便可提供 OEM 数据：</span><span class="sxs-lookup"><span data-stu-id="76102-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="76102-128">像这种来自命令的输出（它直接从某个硬件返回信息）仅相当于你拥有的数据。</span><span class="sxs-lookup"><span data-stu-id="76102-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="76102-129">某些信息未由硬件制造商正确配置，因此可能不可用。</span><span class="sxs-lookup"><span data-stu-id="76102-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="76102-130">列出已安装的修补程序</span><span class="sxs-lookup"><span data-stu-id="76102-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="76102-131">可以通过使用 **Win32_QuickFixEngineering** 列出所有已安装的修补程序：</span><span class="sxs-lookup"><span data-stu-id="76102-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="76102-132">此类将返回如下所示的修补程序列表：</span><span class="sxs-lookup"><span data-stu-id="76102-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="76102-133">为了使输出更简洁，可能需要排除某些属性。</span><span class="sxs-lookup"><span data-stu-id="76102-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="76102-134">尽管可以使用 `Get-CimInstance` 的 Property 参数以仅选择 HotFixID，但这样做实际上将返回更多信息，因为默认显示所有元数据：</span><span class="sxs-lookup"><span data-stu-id="76102-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="76102-135">返回额外数据是因为 `Get-CimInstance` 中的 Property 参数限制从 WMI 类实例返回的属性，而不限制返回到 Windows PowerShell 的对象。</span><span class="sxs-lookup"><span data-stu-id="76102-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="76102-136">若要减少输出，请使用 `Select-Object`：</span><span class="sxs-lookup"><span data-stu-id="76102-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="76102-137">列出操作系统版本信息</span><span class="sxs-lookup"><span data-stu-id="76102-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="76102-138">**Win32_OperatingSystem** 类属性包括版本和服务包信息。</span><span class="sxs-lookup"><span data-stu-id="76102-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="76102-139">你可以明确仅选择这些属性，以从 **Win32_OperatingSystem** 获取版本信息摘要：</span><span class="sxs-lookup"><span data-stu-id="76102-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="76102-140">也可以将通配符用于 `Select-Object` 的 Property 参数。</span><span class="sxs-lookup"><span data-stu-id="76102-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="76102-141">因为在此处使用以 **Build** 或 **ServicePack** 开头的所有属性很重要，所以我们可以将此缩短为下列形式：</span><span class="sxs-lookup"><span data-stu-id="76102-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="76102-142">列出本地用户和所有者</span><span class="sxs-lookup"><span data-stu-id="76102-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="76102-143">本地常规用户信息（许可的用户数、当前用户数和所有者名称）可通过选择 Win32_OperatingSystem 类的属性找到。</span><span class="sxs-lookup"><span data-stu-id="76102-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="76102-144">你可以明确选择使属性显示如下：</span><span class="sxs-lookup"><span data-stu-id="76102-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="76102-145">使用通配符的更简洁版本是：</span><span class="sxs-lookup"><span data-stu-id="76102-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="76102-146">获取可用磁盘空间</span><span class="sxs-lookup"><span data-stu-id="76102-146">Getting Available Disk Space</span></span>

<span data-ttu-id="76102-147">若要查看本地驱动器的磁盘空间和可用空间，可以使用 Win32_LogicalDisk WMI 类。</span><span class="sxs-lookup"><span data-stu-id="76102-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="76102-148">仅需要查看具有 DriveType 3（WMI 将此值用作固定硬盘）的实例。</span><span class="sxs-lookup"><span data-stu-id="76102-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="76102-149">获取登录会话信息</span><span class="sxs-lookup"><span data-stu-id="76102-149">Getting Logon Session Information</span></span>

<span data-ttu-id="76102-150">可通过 Win32_LogonSession WMI 类获取有关与用户相关联的登录会话的常规信息：</span><span class="sxs-lookup"><span data-stu-id="76102-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="76102-151">获取登录到计算机的用户</span><span class="sxs-lookup"><span data-stu-id="76102-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="76102-152">可以使用 Win32_ComputerSystem 显示已登录到特定计算机系统的用户。</span><span class="sxs-lookup"><span data-stu-id="76102-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="76102-153">此命令将仅返回登录到系统桌面的用户：</span><span class="sxs-lookup"><span data-stu-id="76102-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="76102-154">获取计算机的本地时间</span><span class="sxs-lookup"><span data-stu-id="76102-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="76102-155">可以通过使用 Win32_LocalTime WMI 类检索指定计算机上的当前本地时间。</span><span class="sxs-lookup"><span data-stu-id="76102-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a><span data-ttu-id="76102-156">显示服务状态</span><span class="sxs-lookup"><span data-stu-id="76102-156">Displaying Service Status</span></span>

<span data-ttu-id="76102-157">若要查看指定计算机上所有服务的状态，可以本地使用 `Get-Service` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="76102-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="76102-158">对于远程系统，可以使用 Win32_Service WMI 类。</span><span class="sxs-lookup"><span data-stu-id="76102-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="76102-159">如果还使用 `Select-Object` 来筛选 Status、Name 和 DisplayName 的结果，则输出格式将与 `Get-Service` 的输出格式几乎完全相同：</span><span class="sxs-lookup"><span data-stu-id="76102-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="76102-160">若要完整显示具有极长名称的临时服务的名称，可能需要使用具有 AutoSize 和 Wrap 参数的 `Format-Table`，用于优化列宽并允许较长名称换行而不是被截断：</span><span class="sxs-lookup"><span data-stu-id="76102-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
