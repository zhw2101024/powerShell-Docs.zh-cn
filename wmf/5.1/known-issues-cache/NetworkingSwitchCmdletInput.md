---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.topic: conceptual
contributor: vaibch
title: 网络交换机管理器 cmdlet 失败
ms.openlocfilehash: 197a25411a82e5d256a9420706535d5411991f1b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
<span data-ttu-id="3ccd9-103">网络交换机管理器 cmdlet 可用于通过 WSMAN 管理网络交换机。</span><span class="sxs-lookup"><span data-stu-id="3ccd9-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="3ccd9-104">此模块的几个 cmdlet 可接受管道中的值。</span><span class="sxs-lookup"><span data-stu-id="3ccd9-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="3ccd9-105">在 WMF 5.1 预览版中，当值不通过管道传递时，无法执行可接受管道中的值的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ccd9-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="3ccd9-106">如果未使用“InputObject”参数，则 cmdlet 会继续执行且不会出现故障。</span><span class="sxs-lookup"><span data-stu-id="3ccd9-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="3ccd9-107">下面是受影响的 cmdlet 的列表，即这些 cmdlet 可接受管道的“InputObject”参数的值。</span><span class="sxs-lookup"><span data-stu-id="3ccd9-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="3ccd9-108">如果此值不从管道传递，cmdlet 执行将失败。</span><span class="sxs-lookup"><span data-stu-id="3ccd9-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="3ccd9-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3ccd9-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="3ccd9-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3ccd9-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="3ccd9-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3ccd9-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="3ccd9-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3ccd9-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="3ccd9-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="3ccd9-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="3ccd9-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="3ccd9-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="3ccd9-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3ccd9-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="3ccd9-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3ccd9-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="3ccd9-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="3ccd9-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="3ccd9-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="3ccd9-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="3ccd9-119">解决方法</span><span class="sxs-lookup"><span data-stu-id="3ccd9-119">Resolution</span></span>
<span data-ttu-id="3ccd9-120">如果 InputObject 参数的值通过管道传递到 cmdlet，则 cmdlet 工作正常。</span><span class="sxs-lookup"><span data-stu-id="3ccd9-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="3ccd9-121">适用于以上 cmdlet 的一些示例包括：</span><span class="sxs-lookup"><span data-stu-id="3ccd9-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="3ccd9-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3ccd9-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="3ccd9-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3ccd9-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="3ccd9-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3ccd9-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="3ccd9-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3ccd9-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="3ccd9-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="3ccd9-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="3ccd9-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3ccd9-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="3ccd9-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3ccd9-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="3ccd9-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="3ccd9-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
