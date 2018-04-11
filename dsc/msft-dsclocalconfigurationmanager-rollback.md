---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 RollBack 方法
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6373c-103">MSFT_DSCLocalConfigurationManager 类的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="6373c-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6373c-104">将配置回滚到以前的版本。</span><span class="sxs-lookup"><span data-stu-id="6373c-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="6373c-105">语法</span><span class="sxs-lookup"><span data-stu-id="6373c-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="6373c-106">参数</span><span class="sxs-lookup"><span data-stu-id="6373c-106">Parameters</span></span>
----------

<span data-ttu-id="6373c-107">configurationNumber \[in\]：指定请求获取的配置。</span><span class="sxs-lookup"><span data-stu-id="6373c-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="6373c-108">返回值</span><span class="sxs-lookup"><span data-stu-id="6373c-108">Return value</span></span>
------------

<span data-ttu-id="6373c-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="6373c-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6373c-110">备注</span><span class="sxs-lookup"><span data-stu-id="6373c-110">Remarks</span></span>

<span data-ttu-id="6373c-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="6373c-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6373c-112">要求</span><span class="sxs-lookup"><span data-stu-id="6373c-112">Requirements</span></span>
------------
><span data-ttu-id="6373c-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6373c-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6373c-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6373c-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6373c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6373c-115">See also</span></span>


[<span data-ttu-id="6373c-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6373c-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)