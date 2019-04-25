---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.topic: conceptual
contributor: vaibch
title: 网络交换机管理器 cmdlet 失败
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084974"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="b2e21-103">网络交换机管理器 Cmdlet 失败</span><span class="sxs-lookup"><span data-stu-id="b2e21-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="b2e21-104">网络交换机管理器 cmdlet 可用于通过 WSMAN 管理网络交换机。</span><span class="sxs-lookup"><span data-stu-id="b2e21-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="b2e21-105">此模块的几个 cmdlet 可接受管道中的值。</span><span class="sxs-lookup"><span data-stu-id="b2e21-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="b2e21-106">在 WMF 5.1 预览版中，当值不通过管道传递时，无法执行可接受管道中的值的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b2e21-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="b2e21-107">如果未使用“InputObject”参数，则 cmdlet 会继续执行且不会出现故障。</span><span class="sxs-lookup"><span data-stu-id="b2e21-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="b2e21-108">下面是受影响的 cmdlet 的列表，即这些 cmdlet 可接受管道的“InputObject”参数的值。</span><span class="sxs-lookup"><span data-stu-id="b2e21-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="b2e21-109">如果此值不从管道传递，cmdlet 执行将失败。</span><span class="sxs-lookup"><span data-stu-id="b2e21-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="b2e21-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="b2e21-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="b2e21-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="b2e21-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="b2e21-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="b2e21-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="b2e21-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="b2e21-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="b2e21-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="b2e21-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="b2e21-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="b2e21-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="b2e21-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="b2e21-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="b2e21-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="b2e21-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="b2e21-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="b2e21-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="b2e21-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="b2e21-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="b2e21-120">解决方法</span><span class="sxs-lookup"><span data-stu-id="b2e21-120">Resolution</span></span>

<span data-ttu-id="b2e21-121">如果 InputObject 参数的值通过管道传递到 cmdlet，则 cmdlet 工作正常。</span><span class="sxs-lookup"><span data-stu-id="b2e21-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="b2e21-122">适用于以上 cmdlet 的一些示例包括：</span><span class="sxs-lookup"><span data-stu-id="b2e21-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```