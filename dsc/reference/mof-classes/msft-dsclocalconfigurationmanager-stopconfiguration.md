---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677358"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cc862-103">MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="cc862-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cc862-104">停止正在进行的配置更改。</span><span class="sxs-lookup"><span data-stu-id="cc862-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc862-105">语法</span><span class="sxs-lookup"><span data-stu-id="cc862-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="cc862-106">参数</span><span class="sxs-lookup"><span data-stu-id="cc862-106">Parameters</span></span>

<span data-ttu-id="cc862-107">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="cc862-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="cc862-108">返回值</span><span class="sxs-lookup"><span data-stu-id="cc862-108">Return value</span></span>

<span data-ttu-id="cc862-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="cc862-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc862-110">备注</span><span class="sxs-lookup"><span data-stu-id="cc862-110">Remarks</span></span>

<span data-ttu-id="cc862-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="cc862-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc862-112">要求</span><span class="sxs-lookup"><span data-stu-id="cc862-112">Requirements</span></span>

<span data-ttu-id="cc862-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cc862-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cc862-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc862-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cc862-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cc862-115">See also</span></span>

[<span data-ttu-id="cc862-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cc862-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)