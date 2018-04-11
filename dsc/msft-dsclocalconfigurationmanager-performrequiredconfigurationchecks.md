---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法
ms.openlocfilehash: 9cc4384088fcc39b09979b8ae4d023fc46307b13
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="70fb1-103">MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法</span><span class="sxs-lookup"><span data-stu-id="70fb1-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="70fb1-104">使用任务计划程序启动一致性检查。</span><span class="sxs-lookup"><span data-stu-id="70fb1-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="70fb1-105">语法</span><span class="sxs-lookup"><span data-stu-id="70fb1-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="70fb1-106">参数</span><span class="sxs-lookup"><span data-stu-id="70fb1-106">Parameters</span></span>
----------

<span data-ttu-id="70fb1-107">Flags \[in\]：指定要运行的一致性检查类型的位掩码。</span><span class="sxs-lookup"><span data-stu-id="70fb1-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="70fb1-108">以下值有效，并可以通过 **OR** 位运算组合：</span><span class="sxs-lookup"><span data-stu-id="70fb1-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="70fb1-109">值</span><span class="sxs-lookup"><span data-stu-id="70fb1-109">Value</span></span> |<span data-ttu-id="70fb1-110">说明</span><span class="sxs-lookup"><span data-stu-id="70fb1-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="70fb1-111">**1**</span><span class="sxs-lookup"><span data-stu-id="70fb1-111">**1**</span></span> | <span data-ttu-id="70fb1-112">常规的一致性检查。</span><span class="sxs-lookup"><span data-stu-id="70fb1-112">A normal consistency check.</span></span> |
|<span data-ttu-id="70fb1-113">**2**</span><span class="sxs-lookup"><span data-stu-id="70fb1-113">**2**</span></span> | <span data-ttu-id="70fb1-114">重启后一致性检查的延续。</span><span class="sxs-lookup"><span data-stu-id="70fb1-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="70fb1-115">此值不应与其他值组合。</span><span class="sxs-lookup"><span data-stu-id="70fb1-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="70fb1-116">**4**</span><span class="sxs-lookup"><span data-stu-id="70fb1-116">**4**</span></span> | <span data-ttu-id="70fb1-117">应从节点的元配置中指定的请求服务器请求配置。</span><span class="sxs-lookup"><span data-stu-id="70fb1-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="70fb1-118">此值应始终与 **1** 组合，以获得为 **5** 的值。</span><span class="sxs-lookup"><span data-stu-id="70fb1-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="70fb1-119">**8**</span><span class="sxs-lookup"><span data-stu-id="70fb1-119">**8**</span></span> | <span data-ttu-id="70fb1-120">将状态发送到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="70fb1-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="70fb1-121">返回值</span><span class="sxs-lookup"><span data-stu-id="70fb1-121">Return value</span></span>
------------

<span data-ttu-id="70fb1-122">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="70fb1-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="70fb1-123">备注</span><span class="sxs-lookup"><span data-stu-id="70fb1-123">Remarks</span></span>

<span data-ttu-id="70fb1-124">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="70fb1-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="70fb1-125">要求</span><span class="sxs-lookup"><span data-stu-id="70fb1-125">Requirements</span></span>
------------
><span data-ttu-id="70fb1-126">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="70fb1-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="70fb1-127">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="70fb1-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="70fb1-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70fb1-128">See also</span></span>


[<span data-ttu-id="70fb1-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="70fb1-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)