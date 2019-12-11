---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 管理服务
ms.openlocfilehash: d9e17b2d91ae01d7d4d6d573348289fa68dc9c56
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030158"
---
# <a name="managing-services"></a><span data-ttu-id="8fbc3-103">管理服务</span><span class="sxs-lookup"><span data-stu-id="8fbc3-103">Managing Services</span></span>

<span data-ttu-id="8fbc3-104">有八个专为各种服务任务设计的核心 Service cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="8fbc3-105">我们仅会列出和更改服务的运行状态，但你可以使用 `Get-Help \*-Service` 获取服务 cmdlet 列表并通过使用 `Get-Help <Cmdlet-Name>`（例如 `Get-Help New-Service`）找到每个服务 cmdlet 的相关信息。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="8fbc3-106">获取服务</span><span class="sxs-lookup"><span data-stu-id="8fbc3-106">Getting Services</span></span>

<span data-ttu-id="8fbc3-107">可以通过使用 `Get-Service` cmdlet 获取本地或远程计算机上的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="8fbc3-108">与使用 `Get-Process` 相同，使用不带参数的 `Get-Service` 命令将返回所有服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="8fbc3-109">你可以按名称进行筛选，甚至可以使用星号作为通配符：</span><span class="sxs-lookup"><span data-stu-id="8fbc3-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="8fbc3-110">因为服务的真实名称并不总是可见，所以你可能会发现你需要按显示名称查找服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="8fbc3-111">可以按特定名称（使用通配符或使用显示名称的列表）执行此操作：</span><span class="sxs-lookup"><span data-stu-id="8fbc3-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="8fbc3-112">可以使用 Get-Service cmdlet 的 ComputerName 参数获取远程计算机上的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="8fbc3-113">ComputerName 参数接受多个值和通配符，因此你可以使用单个命令获取多台计算机上的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="8fbc3-114">例如，下面的命令获取 Server01 远程计算机上的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="8fbc3-115">获取必需和从属服务</span><span class="sxs-lookup"><span data-stu-id="8fbc3-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="8fbc3-116">Get-Service cmdlet 具有两个在服务管理中非常有用的参数。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="8fbc3-117">DependentServices 参数获取依赖于该服务的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="8fbc3-118">RequiredServices 参数获取此服务所依赖的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="8fbc3-119">这些参数只显示 Get-Service 返回的 System.ServiceProcess.ServiceController 对象的 DependentServices 和 ServicesDependedOn (alias=RequiredServices) 属性的值，但是它们可简化命令，使获取此信息更加简单。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="8fbc3-120">下面的命令获取 LanmanWorkstation 服务需要的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="8fbc3-121">下面的命令获取需要 LanmanWorkstation 服务的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="8fbc3-122">你甚至可以获取所有具有依赖关系的服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="8fbc3-123">下面的命令所做的就是这些，然后使用 Format-Table cmdlet 来显示计算机上服务的 Status、Name、RequiredServices 和 DependentServices 属性。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="8fbc3-124">停止、启动、暂停和重启服务</span><span class="sxs-lookup"><span data-stu-id="8fbc3-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="8fbc3-125">所有 Service cmdlet 都具有相同的一般形式。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="8fbc3-126">可以按公用名或显示名称指定服务，并使用列表和通配符作为值。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="8fbc3-127">若要停止打印后台处理程序，请使用：</span><span class="sxs-lookup"><span data-stu-id="8fbc3-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="8fbc3-128">若要在停止后启动打印后台处理程序，请使用：</span><span class="sxs-lookup"><span data-stu-id="8fbc3-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="8fbc3-129">若要暂停打印后台处理程序，请使用：</span><span class="sxs-lookup"><span data-stu-id="8fbc3-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="8fbc3-130">虽然 `Restart-Service` cmdlet 的操作方式与其他 Service cmdlet 的操作方式相同，但是我们将针对它列举一些更复杂的示例。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="8fbc3-131">使用最简单的方式指定服务的名称：</span><span class="sxs-lookup"><span data-stu-id="8fbc3-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="8fbc3-132">你将注意到你收到了有关打印后台处理程序启动的重复警告消息。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="8fbc3-133">执行需要耗费一些时间的服务操作时，Windows PowerShell 将通知你它仍在尝试执行该任务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="8fbc3-134">如果想要重启多个服务，则可获取服务列表，并对其进行筛选，然后执行重启操作：</span><span class="sxs-lookup"><span data-stu-id="8fbc3-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="8fbc3-135">虽然这些 Service cmdlet 没有 ComputerName 参数，但是你可通过使用 Invoke-Command cmdlet 在远程计算机上运行它们。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="8fbc3-136">例如，下面的命令在 Server01 远程计算机上重启后台打印程序服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="8fbc3-137">设置服务属性</span><span class="sxs-lookup"><span data-stu-id="8fbc3-137">Setting Service Properties</span></span>

<span data-ttu-id="8fbc3-138">`Set-Service` cmdlet 更改本地或远程计算机上服务的属性。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="8fbc3-139">因为服务状态是一种属性，所以你可以使用此 cmdlet 来启动、停止和暂停服务。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="8fbc3-140">Set-Service cmdlet 还有一个 StartupType 参数，可让你更改服务启动类型。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="8fbc3-141">若要在 Windows Vista 和 Windows 的更高版本上使用 `Set-Service`，请使用“以管理员身份运行”选项打开 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8fbc3-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="8fbc3-142">有关详细信息，请参阅 [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="8fbc3-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="8fbc3-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fbc3-143">See Also</span></span>

- <span data-ttu-id="8fbc3-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="8fbc3-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="8fbc3-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="8fbc3-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="8fbc3-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="8fbc3-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="8fbc3-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="8fbc3-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>
