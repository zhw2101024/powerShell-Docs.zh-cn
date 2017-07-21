---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSCAutomationHostEnabled 注册表项"
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="5057c-103">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5057c-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="5057c-104">DSCAutomationHostEnabled 注册表项</span><span class="sxs-lookup"><span data-stu-id="5057c-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="5057c-105">DSC 使用 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** 下的 **DSCAutomationHostEnabled** 注册表项，启用在初始启动时配置计算机。</span><span class="sxs-lookup"><span data-stu-id="5057c-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="5057c-106">DSCAutomationHostEnabled 支持三种模式：</span><span class="sxs-lookup"><span data-stu-id="5057c-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="5057c-107">DSCAutomationHostEnabled 值</span><span class="sxs-lookup"><span data-stu-id="5057c-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="5057c-108">说明</span><span class="sxs-lookup"><span data-stu-id="5057c-108">Description</span></span>   | 
|---|---| 
<span data-ttu-id="5057c-109">0</span><span class="sxs-lookup"><span data-stu-id="5057c-109">0</span></span> | <span data-ttu-id="5057c-110">禁用对启动状态计算机的配置。</span><span class="sxs-lookup"><span data-stu-id="5057c-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="5057c-111">1</span><span class="sxs-lookup"><span data-stu-id="5057c-111">1</span></span> | <span data-ttu-id="5057c-112">启用对启动状态计算机的配置。</span><span class="sxs-lookup"><span data-stu-id="5057c-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="5057c-113">2</span><span class="sxs-lookup"><span data-stu-id="5057c-113">2</span></span> | <span data-ttu-id="5057c-114">仅在 DSC 处于挂起或当前状态时，启用对计算机的配置。</span><span class="sxs-lookup"><span data-stu-id="5057c-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="5057c-115">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="5057c-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="5057c-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5057c-116">See Also</span></span>

<span data-ttu-id="5057c-117">有关如何使用此功能在初始启动时运行配置的示例，请参阅[初始启动时使用 DSC 配置虚拟机](bootstrapDsc.md)。</span><span class="sxs-lookup"><span data-stu-id="5057c-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>


