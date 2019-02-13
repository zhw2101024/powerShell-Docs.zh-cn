---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 RollBack 方法
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677476"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a2df2-103">MSFT_DSCLocalConfigurationManager 类的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="a2df2-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a2df2-104">将配置回滚到以前的版本。</span><span class="sxs-lookup"><span data-stu-id="a2df2-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2df2-105">语法</span><span class="sxs-lookup"><span data-stu-id="a2df2-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="a2df2-106">参数</span><span class="sxs-lookup"><span data-stu-id="a2df2-106">Parameters</span></span>

<span data-ttu-id="a2df2-107">configurationNumber \[in\]：指定请求获取的配置。</span><span class="sxs-lookup"><span data-stu-id="a2df2-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a2df2-108">返回值</span><span class="sxs-lookup"><span data-stu-id="a2df2-108">Return value</span></span>

<span data-ttu-id="a2df2-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="a2df2-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2df2-110">备注</span><span class="sxs-lookup"><span data-stu-id="a2df2-110">Remarks</span></span>

<span data-ttu-id="a2df2-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="a2df2-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2df2-112">要求</span><span class="sxs-lookup"><span data-stu-id="a2df2-112">Requirements</span></span>

<span data-ttu-id="a2df2-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a2df2-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a2df2-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a2df2-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a2df2-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2df2-115">See also</span></span>

[<span data-ttu-id="a2df2-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a2df2-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)