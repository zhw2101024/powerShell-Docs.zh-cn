---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: StopConfiguration 方法
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953354"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="533b1-103">StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="533b1-103">StopConfiguration method</span></span>

<span data-ttu-id="533b1-104">停止正在进行的配置更改。</span><span class="sxs-lookup"><span data-stu-id="533b1-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="533b1-105">语法</span><span class="sxs-lookup"><span data-stu-id="533b1-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="533b1-106">参数</span><span class="sxs-lookup"><span data-stu-id="533b1-106">Parameters</span></span>

<span data-ttu-id="533b1-107">force  \[in\]：若为 true  ，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="533b1-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="533b1-108">返回值</span><span class="sxs-lookup"><span data-stu-id="533b1-108">Return value</span></span>

<span data-ttu-id="533b1-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="533b1-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="533b1-110">备注</span><span class="sxs-lookup"><span data-stu-id="533b1-110">Remarks</span></span>

<span data-ttu-id="533b1-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="533b1-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="533b1-112">要求</span><span class="sxs-lookup"><span data-stu-id="533b1-112">Requirements</span></span>

<span data-ttu-id="533b1-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="533b1-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="533b1-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="533b1-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="533b1-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="533b1-115">See also</span></span>

[<span data-ttu-id="533b1-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="533b1-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
