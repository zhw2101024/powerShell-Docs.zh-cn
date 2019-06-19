---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 执行网络任务
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030854"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="20e9f-103">执行网络任务</span><span class="sxs-lookup"><span data-stu-id="20e9f-103">Performing Networking Tasks</span></span>

<span data-ttu-id="20e9f-104">由于 TCP/IP 是最常用的网络协议，因此大多数低级别网络协议管理任务都涉及 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="20e9f-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="20e9f-105">在本部分中，我们使用 Windows PowerShell 和 WMI 来执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="20e9f-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="20e9f-106">列出计算机的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="20e9f-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="20e9f-107">若要获取本地计算机上使用的所有 IP 地址，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="20e9f-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="20e9f-108">此命令的输出与大多数属性列表不同，因为值括在大括号中：</span><span class="sxs-lookup"><span data-stu-id="20e9f-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="20e9f-109">若要了解大括号出现的原因，请使用 Get-Member cmdlet 检查 **IPAddress** 属性：</span><span class="sxs-lookup"><span data-stu-id="20e9f-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="20e9f-110">每个网络适配器的 IPAddress 属性实际上是一个数组。</span><span class="sxs-lookup"><span data-stu-id="20e9f-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="20e9f-111">定义中的大括号指示 **IPAddress** 不是 **System.String** 值，而是由 **System.String** 值组成的数组。</span><span class="sxs-lookup"><span data-stu-id="20e9f-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="20e9f-112">列出 IP 配置数据</span><span class="sxs-lookup"><span data-stu-id="20e9f-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="20e9f-113">若要显示每个网络适配器的详细 IP 配置数据，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="20e9f-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="20e9f-114">网络适配器配置对象的默认显示为一组非常精简的可用信息。</span><span class="sxs-lookup"><span data-stu-id="20e9f-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="20e9f-115">对于深入检查和疑难解答，请使用 Select-Object 或格式设置 cmdlet（例如 Format-List）来指定要显示的属性。</span><span class="sxs-lookup"><span data-stu-id="20e9f-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="20e9f-116">如果你对 IPX 或 WINS 属性不感兴趣（可能是在使用现代 TCP/IP 网络的情况下），则可以使用 Select-Object 的 ExcludeProperty 参数来隐藏其名称以“WINS”或“IPX:”开头的属性</span><span class="sxs-lookup"><span data-stu-id="20e9f-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="20e9f-117">此命令返回有关 DHCP、DNS、路由以及其他次要 IP 配置属性的详细信息。</span><span class="sxs-lookup"><span data-stu-id="20e9f-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="20e9f-118">Ping 计算机</span><span class="sxs-lookup"><span data-stu-id="20e9f-118">Pinging Computers</span></span>

<span data-ttu-id="20e9f-119">你可以使用 **Win32_PingStatus** 对计算机执行简单的 Ping 操作。</span><span class="sxs-lookup"><span data-stu-id="20e9f-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="20e9f-120">下面的命令执行 Ping 操作，但返回冗长的输出：</span><span class="sxs-lookup"><span data-stu-id="20e9f-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="20e9f-121">摘要信息是更为有用的形式，它显示下面的命令生成的 Address、ResponseTime 以及 StatusCode 属性。</span><span class="sxs-lookup"><span data-stu-id="20e9f-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="20e9f-122">Format-Table 的 Autosize 参数调整表列的大小，以使其正确显示在 Windows PowerShell 中。</span><span class="sxs-lookup"><span data-stu-id="20e9f-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="20e9f-123">如果 StatusCode 为 0，指明 ping 操作成功。</span><span class="sxs-lookup"><span data-stu-id="20e9f-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="20e9f-124">你可以使用数组借助单个命令对计算机执行 Ping 操作。</span><span class="sxs-lookup"><span data-stu-id="20e9f-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="20e9f-125">由于存在多个地址，因此请使用 **ForEach-Object** 单独对每个地址执行 Ping 操作：</span><span class="sxs-lookup"><span data-stu-id="20e9f-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="20e9f-126">可以使用相同的命令格式对一个子网（例如使用网络号码 (192.168.1.0) 和标准 C 类子网掩码 (255.255.255.0) 的专用网）上的所有计算机执行 Ping 操作。仅在 192.168.1.1 到 192.168.1.254 范围内的地址为合法本地地址（0 始终为网络号码保留，255 是子网广播地址）。</span><span class="sxs-lookup"><span data-stu-id="20e9f-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="20e9f-127">若要在 Windows PowerShell 中表示从 1 到 254 范围内的数字数组，请使用语句 **1..254**。</span><span class="sxs-lookup"><span data-stu-id="20e9f-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="20e9f-128">可以通过生成数组，然后将值添加到 ping 语句中的部分地址上，执行完整的子网 Ping 操作：</span><span class="sxs-lookup"><span data-stu-id="20e9f-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="20e9f-129">请注意，这一用于生成一系列地址的方法也可用于其他地方。</span><span class="sxs-lookup"><span data-stu-id="20e9f-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="20e9f-130">你可以使用以下方式生成完整的地址集：</span><span class="sxs-lookup"><span data-stu-id="20e9f-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="20e9f-131">检索网络适配器属性</span><span class="sxs-lookup"><span data-stu-id="20e9f-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="20e9f-132">在本用户指南的前面部分中，我们提到过你可以使用 **Win32_NetworkAdapterConfiguration** 来检索常规配置属性。</span><span class="sxs-lookup"><span data-stu-id="20e9f-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="20e9f-133">尽管不是严格的 TCP/IP 信息，但网络适配器信息（例如 MAC 地址和适配器类型）也可用于了解计算机的运行情况。</span><span class="sxs-lookup"><span data-stu-id="20e9f-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="20e9f-134">若要获取此信息的摘要，请使用下面的命令：</span><span class="sxs-lookup"><span data-stu-id="20e9f-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="20e9f-135">为网络适配器分配 DNS 域</span><span class="sxs-lookup"><span data-stu-id="20e9f-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="20e9f-136">若要分配 DNS 域以便进行自动名称解析，请使用 **Win32_NetworkAdapterConfiguration SetDNSDomain** 方法。</span><span class="sxs-lookup"><span data-stu-id="20e9f-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="20e9f-137">由于你单独为每个网络适配器配置分配 DNS 域，因此需要使用 **ForEach-Object** 语句将域分配给每个适配器：</span><span class="sxs-lookup"><span data-stu-id="20e9f-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="20e9f-138">筛选语句“IPEnabled=$true”是必需的，因为即使是在仅使用 TCP/IP 的网络上，计算机上的多个网络适配器配置也不是真正的 TCP/IP 适配器；它们是支持 RAS、PPTP、QoS 和其他适用于所有适配器的服务的常规软件元素，因此没有自己的地址。</span><span class="sxs-lookup"><span data-stu-id="20e9f-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="20e9f-139">可以使用 **Where-Object** cmdlet，而不是使用 **Get-WmiObject** 筛选器筛选命令。</span><span class="sxs-lookup"><span data-stu-id="20e9f-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="20e9f-140">执行 DHCP 配置任务</span><span class="sxs-lookup"><span data-stu-id="20e9f-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="20e9f-141">修改 DHCP 详细信息需处理一组网络适配器，与 DNS 配置的操作相同。</span><span class="sxs-lookup"><span data-stu-id="20e9f-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="20e9f-142">你可通过使用 WMI 执行多种不同的操作，我们将逐步介绍一些常见操作。</span><span class="sxs-lookup"><span data-stu-id="20e9f-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="20e9f-143">确定启用 DHCP 的适配器</span><span class="sxs-lookup"><span data-stu-id="20e9f-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="20e9f-144">若要查找计算机上启用了 DHCP 的适配器，请使用下面的命令：</span><span class="sxs-lookup"><span data-stu-id="20e9f-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="20e9f-145">若要排除有IP 配置问题的适配器，可以仅检索已启用 IP 的适配器：</span><span class="sxs-lookup"><span data-stu-id="20e9f-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="20e9f-146">检索 DHCP 属性</span><span class="sxs-lookup"><span data-stu-id="20e9f-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="20e9f-147">因为适配器的 DHCP 相关属性通常以“DHCP”开头，所以你可使用 Format-Table 的 Property 参数来仅显示那些属性：</span><span class="sxs-lookup"><span data-stu-id="20e9f-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="20e9f-148">在每个适配器上启用 DHCP</span><span class="sxs-lookup"><span data-stu-id="20e9f-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="20e9f-149">若要在所有适配器上启用 DHCP，请使用下面的命令：</span><span class="sxs-lookup"><span data-stu-id="20e9f-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="20e9f-150">可以使用 Filter 语句“IPEnabled=$true and DHCPEnabled=$false”，以免在已启用 DHCP 的适配器上再次启用它，但忽略这一步也不会导致错误出现。</span><span class="sxs-lookup"><span data-stu-id="20e9f-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="20e9f-151">释放和续订特定适配器上的 DHCP 租约</span><span class="sxs-lookup"><span data-stu-id="20e9f-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="20e9f-152">**Win32_NetworkAdapterConfiguration** 类具有 **ReleaseDHCPLease** 和 **RenewDHCPLease** 方法。</span><span class="sxs-lookup"><span data-stu-id="20e9f-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="20e9f-153">这两种方法的使用方式相同。</span><span class="sxs-lookup"><span data-stu-id="20e9f-153">Both are used in the same way.</span></span> <span data-ttu-id="20e9f-154">一般情况下，在仅需释放或续订特定子网上的适配器地址时使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="20e9f-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="20e9f-155">在子网上筛选器适配器的最简单方法是仅选择使用该子网的网关的适配器配置。</span><span class="sxs-lookup"><span data-stu-id="20e9f-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="20e9f-156">例如，下面的命令释放本地计算机上适配器上的所有 DHCP 租约，这些适配器正在从 192.168.1.254 获得 DHCP 租约：</span><span class="sxs-lookup"><span data-stu-id="20e9f-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="20e9f-157">续订 DHCP 租约的唯一更改是使用 **RenewDHCPLease** 方法，而不是 **ReleaseDHCPLease** 方法：</span><span class="sxs-lookup"><span data-stu-id="20e9f-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="20e9f-158">在远程计算机上使用这些方法时，请注意，如果你通过已释放或已续订租约的适配器连接到远程系统，则可能会失去对该系统的访问权限。</span><span class="sxs-lookup"><span data-stu-id="20e9f-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="20e9f-159">释放和续订所有适配器上的 DHCP 租约</span><span class="sxs-lookup"><span data-stu-id="20e9f-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="20e9f-160">可以通过使用 **Win32_NetworkAdapterConfiguration** 方法、**ReleaseDHCPLeaseAll** 和 **RenewDHCPLeaseAll** 对所有适配器指定全局 DHCP 地址释放或续订。</span><span class="sxs-lookup"><span data-stu-id="20e9f-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="20e9f-161">但是，该命令必须适用于 WMI 类，而不是特定的适配器，因为全局释放和续订租约是对该类执行的，而不是对特定适配器执行的。</span><span class="sxs-lookup"><span data-stu-id="20e9f-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="20e9f-162">可以通过列出所有 WMI 类，然后按名称仅选择所需类来获取对 WMI 类而不是类实例的引用。</span><span class="sxs-lookup"><span data-stu-id="20e9f-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="20e9f-163">例如，下面的命令将返回 Win32_NetworkAdapterConfiguration 类：</span><span class="sxs-lookup"><span data-stu-id="20e9f-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="20e9f-164">可以将整个命令视为类，并在其上调用**ReleaseDHCPAdapterLease** 方法。</span><span class="sxs-lookup"><span data-stu-id="20e9f-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="20e9f-165">在下面的命令中，**Get-WmiObject** 和 **Where-Object** 管道元素两边的括号指示 Windows PowerShell 先对其进行评估：</span><span class="sxs-lookup"><span data-stu-id="20e9f-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="20e9f-166">可以使用相同的命令格式来调用 **RenewDHCPLeaseAll** 方法：</span><span class="sxs-lookup"><span data-stu-id="20e9f-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="20e9f-167">创建网络共享</span><span class="sxs-lookup"><span data-stu-id="20e9f-167">Creating a Network Share</span></span>

<span data-ttu-id="20e9f-168">若要创建网络共享，请使用 **Win32_Share Create** 方法：</span><span class="sxs-lookup"><span data-stu-id="20e9f-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="20e9f-169">还可以在 Windows PowerShell 中使用 **net share** 来创建共享：</span><span class="sxs-lookup"><span data-stu-id="20e9f-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="20e9f-170">删除网络共享</span><span class="sxs-lookup"><span data-stu-id="20e9f-170">Removing a Network Share</span></span>

<span data-ttu-id="20e9f-171">可以使用 **Win32_Share** 删除网络共享，但是该过程与创建共享略有不同，因为需要检索要删除的特定共享，而不是 **Win32_Share** 类。</span><span class="sxs-lookup"><span data-stu-id="20e9f-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="20e9f-172">下面的语句删除共享“TempShare”：</span><span class="sxs-lookup"><span data-stu-id="20e9f-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="20e9f-173">**Net share** 也可实现此操作：</span><span class="sxs-lookup"><span data-stu-id="20e9f-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="20e9f-174">连接 Windows 可访问网络驱动器</span><span class="sxs-lookup"><span data-stu-id="20e9f-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="20e9f-175">**New-PSDrive** cmdlet 可创建 Windows PowerShell 驱动器，但使用这种方法创建的驱动器仅适用于 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="20e9f-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="20e9f-176">若要创建新的联网驱动器，可以使用 **WScript.Network** COM 对象。</span><span class="sxs-lookup"><span data-stu-id="20e9f-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="20e9f-177">下面的命令将共享 \\\\FPS01\\users 映射到本地驱动器 B：</span><span class="sxs-lookup"><span data-stu-id="20e9f-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="20e9f-178">**net use** 命令也可实现此操作：</span><span class="sxs-lookup"><span data-stu-id="20e9f-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="20e9f-179">使用 **WScript.Network** 或 net use 映射的驱动器可立即用于 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="20e9f-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>
