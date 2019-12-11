---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: RollBack 方法
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954934"
---
# <a name="rollback-method"></a><span data-ttu-id="06e29-103">RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="06e29-103">RollBack method</span></span>

<span data-ttu-id="06e29-104">将配置回滚到以前的版本。</span><span class="sxs-lookup"><span data-stu-id="06e29-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="06e29-105">语法</span><span class="sxs-lookup"><span data-stu-id="06e29-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="06e29-106">参数</span><span class="sxs-lookup"><span data-stu-id="06e29-106">Parameters</span></span>

<span data-ttu-id="06e29-107">configurationNumber  \[in\]：指定请求获取的配置。</span><span class="sxs-lookup"><span data-stu-id="06e29-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="06e29-108">返回值</span><span class="sxs-lookup"><span data-stu-id="06e29-108">Return value</span></span>

<span data-ttu-id="06e29-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="06e29-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="06e29-110">备注</span><span class="sxs-lookup"><span data-stu-id="06e29-110">Remarks</span></span>

<span data-ttu-id="06e29-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="06e29-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="06e29-112">要求</span><span class="sxs-lookup"><span data-stu-id="06e29-112">Requirements</span></span>

<span data-ttu-id="06e29-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="06e29-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="06e29-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="06e29-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="06e29-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06e29-115">See also</span></span>

[<span data-ttu-id="06e29-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="06e29-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
