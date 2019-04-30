---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 RollBack 方法
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078361"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b588f-103">MSFT_DSCLocalConfigurationManager 类的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="b588f-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b588f-104">将配置回滚到以前的版本。</span><span class="sxs-lookup"><span data-stu-id="b588f-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="b588f-105">语法</span><span class="sxs-lookup"><span data-stu-id="b588f-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="b588f-106">参数</span><span class="sxs-lookup"><span data-stu-id="b588f-106">Parameters</span></span>

<span data-ttu-id="b588f-107">configurationNumber \[in\]：指定请求获取的配置。</span><span class="sxs-lookup"><span data-stu-id="b588f-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b588f-108">返回值</span><span class="sxs-lookup"><span data-stu-id="b588f-108">Return value</span></span>

<span data-ttu-id="b588f-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="b588f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b588f-110">备注</span><span class="sxs-lookup"><span data-stu-id="b588f-110">Remarks</span></span>

<span data-ttu-id="b588f-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="b588f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b588f-112">要求</span><span class="sxs-lookup"><span data-stu-id="b588f-112">Requirements</span></span>

<span data-ttu-id="b588f-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b588f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b588f-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b588f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b588f-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b588f-115">See also</span></span>

[<span data-ttu-id="b588f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b588f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)