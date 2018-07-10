---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 RollBack 方法
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893012"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0557b-103">MSFT_DSCLocalConfigurationManager 类的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="0557b-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0557b-104">将配置回滚到以前的版本。</span><span class="sxs-lookup"><span data-stu-id="0557b-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="0557b-105">语法</span><span class="sxs-lookup"><span data-stu-id="0557b-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="0557b-106">参数</span><span class="sxs-lookup"><span data-stu-id="0557b-106">Parameters</span></span>

<span data-ttu-id="0557b-107">configurationNumber \[in\]：指定请求获取的配置。</span><span class="sxs-lookup"><span data-stu-id="0557b-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0557b-108">返回值</span><span class="sxs-lookup"><span data-stu-id="0557b-108">Return value</span></span>

<span data-ttu-id="0557b-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="0557b-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0557b-110">备注</span><span class="sxs-lookup"><span data-stu-id="0557b-110">Remarks</span></span>

<span data-ttu-id="0557b-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="0557b-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0557b-112">要求</span><span class="sxs-lookup"><span data-stu-id="0557b-112">Requirements</span></span>

<span data-ttu-id="0557b-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0557b-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0557b-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0557b-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0557b-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0557b-115">See also</span></span>

[<span data-ttu-id="0557b-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0557b-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)