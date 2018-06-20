---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 11b5e36f703c242e0bc820ab19d11d39305fa90c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187905"
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="3885b-102">PowerShell 网络交换机管理</span><span class="sxs-lookup"><span data-stu-id="3885b-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="3885b-103">**Get NetworkSwitchEthernetPort** cmdlet 现在返回以下包含实例的附加信息：</span><span class="sxs-lookup"><span data-stu-id="3885b-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="3885b-104">IPAddress – 与端口相关联的 IP 地址</span><span class="sxs-lookup"><span data-stu-id="3885b-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="3885b-105">PortMode – 端口模式：Access、Route 或 Trunk</span><span class="sxs-lookup"><span data-stu-id="3885b-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="3885b-106">AccessVLAN – Access 模式中与此端口相关联的 VLAN 的 ID</span><span class="sxs-lookup"><span data-stu-id="3885b-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="3885b-107">TrunkedVLANList – Trunk 模式中与此端口相关联的 VLAN 的 ID 列表</span><span class="sxs-lookup"><span data-stu-id="3885b-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="3885b-108">Windows PowerShell 基本网络交换机管理</span><span class="sxs-lookup"><span data-stu-id="3885b-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="3885b-109">在 WMF 5.0 中引入的网络交换机 cmdlet 让你能够将交换机、虚拟 LAN (VLAN) 和基本第 2 层网络交换机端口配置应用到 Windows Server 2012 R2 徽标认证的网络交换机。</span><span class="sxs-lookup"><span data-stu-id="3885b-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="3885b-110">Microsoft 仍致力于支持[数据中心抽象](http://technet.microsoft.com/cloud/dal.aspx)层 (DAL) 的愿景，从而为这一领域中的客户和合作伙伴彰显价值。</span><span class="sxs-lookup"><span data-stu-id="3885b-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="3885b-111">通过使用这些 cmdlet，你可以执行：</span><span class="sxs-lookup"><span data-stu-id="3885b-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="3885b-112">全局交换机配置，如：</span><span class="sxs-lookup"><span data-stu-id="3885b-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="3885b-113">设置主机名</span><span class="sxs-lookup"><span data-stu-id="3885b-113">Set host name</span></span>
    - <span data-ttu-id="3885b-114">设置交换机横幅</span><span class="sxs-lookup"><span data-stu-id="3885b-114">Set switch banner</span></span>
    - <span data-ttu-id="3885b-115">保留配置</span><span class="sxs-lookup"><span data-stu-id="3885b-115">Persist configuration</span></span>
    - <span data-ttu-id="3885b-116">启用或禁用功能</span><span class="sxs-lookup"><span data-stu-id="3885b-116">Enable or disable feature</span></span>

- <span data-ttu-id="3885b-117">VLAN 配置：</span><span class="sxs-lookup"><span data-stu-id="3885b-117">VLAN configuration:</span></span>
    - <span data-ttu-id="3885b-118">创建或删除 VLAN</span><span class="sxs-lookup"><span data-stu-id="3885b-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="3885b-119">启用或禁用 VLAN</span><span class="sxs-lookup"><span data-stu-id="3885b-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="3885b-120">枚举 VLAN</span><span class="sxs-lookup"><span data-stu-id="3885b-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="3885b-121">为 VLAN 设置友好名称</span><span class="sxs-lookup"><span data-stu-id="3885b-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="3885b-122">第 2 层端口配置：</span><span class="sxs-lookup"><span data-stu-id="3885b-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="3885b-123">枚举端口</span><span class="sxs-lookup"><span data-stu-id="3885b-123">Enumerate ports</span></span>
    - <span data-ttu-id="3885b-124">启用或禁用端口</span><span class="sxs-lookup"><span data-stu-id="3885b-124">Enable or disable ports</span></span>
    - <span data-ttu-id="3885b-125">设置端口模式和属性</span><span class="sxs-lookup"><span data-stu-id="3885b-125">Set port modes and properties</span></span>
    - <span data-ttu-id="3885b-126">添加或将 VLAN 关联到端口上的 Trunk 或 Access</span><span class="sxs-lookup"><span data-stu-id="3885b-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="3885b-127">通过查找所有 NetworkSwitch cmdlet 开始探索吧！</span><span class="sxs-lookup"><span data-stu-id="3885b-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="3885b-128">有关详细信息，请参阅 Jeffrey Snover 的 WMF 5.0 预览版公告博客文章：<http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="3885b-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>
