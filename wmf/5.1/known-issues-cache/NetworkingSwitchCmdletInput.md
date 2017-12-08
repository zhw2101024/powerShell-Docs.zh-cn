---
title: "网络交换机管理器 cmdlet 失败"
contributor: vaibch
ms.openlocfilehash: 8495d79aec54d93f94e745e2efccb5116ad5d944
ms.sourcegitcommit: a3966253a165d193a42b43b9430a4dc76988f82f
ms.translationtype: HT
ms.contentlocale: zh-CN
---
<span data-ttu-id="a76d0-102">网络交换机管理器 cmdlet 可用于通过 WSMAN 管理网络交换机。</span><span class="sxs-lookup"><span data-stu-id="a76d0-102">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="a76d0-103">此模块的几个 cmdlet 可接受管道中的值。</span><span class="sxs-lookup"><span data-stu-id="a76d0-103">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="a76d0-104">在 WMF 5.1 预览版中，当值不通过管道传递时，无法执行可接受管道中的值的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a76d0-104">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="a76d0-105">如果未使用“InputObject”参数，则 cmdlet 会继续执行且不会出现故障。</span><span class="sxs-lookup"><span data-stu-id="a76d0-105">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="a76d0-106">下面是受影响的 cmdlet 的列表，即这些 cmdlet 可接受管道的“InputObject”参数的值。</span><span class="sxs-lookup"><span data-stu-id="a76d0-106">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="a76d0-107">如果此值不从管道传递，cmdlet 执行将失败。</span><span class="sxs-lookup"><span data-stu-id="a76d0-107">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="a76d0-108">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="a76d0-108">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="a76d0-109">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="a76d0-109">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="a76d0-110">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="a76d0-110">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="a76d0-111">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="a76d0-111">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="a76d0-112">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="a76d0-112">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="a76d0-113">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="a76d0-113">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="a76d0-114">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="a76d0-114">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="a76d0-115">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="a76d0-115">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="a76d0-116">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="a76d0-116">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="a76d0-117">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="a76d0-117">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="a76d0-118">解决方法</span><span class="sxs-lookup"><span data-stu-id="a76d0-118">Resolution</span></span>
<span data-ttu-id="a76d0-119">如果 InputObject 参数的值通过管道传递到 cmdlet，则 cmdlet 工作正常。</span><span class="sxs-lookup"><span data-stu-id="a76d0-119">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="a76d0-120">适用于以上 cmdlet 的一些示例包括：</span><span class="sxs-lookup"><span data-stu-id="a76d0-120">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="a76d0-121">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="a76d0-121">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="a76d0-122">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="a76d0-122">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="a76d0-123">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="a76d0-123">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="a76d0-124">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="a76d0-124">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="a76d0-125">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="a76d0-125">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="a76d0-126">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="a76d0-126">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="a76d0-127">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="a76d0-127">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="a76d0-128">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="a76d0-128">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
