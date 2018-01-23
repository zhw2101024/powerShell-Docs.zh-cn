---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法"
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="31250-103">MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法</span><span class="sxs-lookup"><span data-stu-id="31250-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="31250-104">使用任务计划程序启动一致性检查。</span><span class="sxs-lookup"><span data-stu-id="31250-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="31250-105">语法</span><span class="sxs-lookup"><span data-stu-id="31250-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="31250-106">参数</span><span class="sxs-lookup"><span data-stu-id="31250-106">Parameters</span></span>
----------

<span data-ttu-id="31250-107">Flags \[in\]</span><span class="sxs-lookup"><span data-stu-id="31250-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="31250-108">指定要运行的一致性检查类型的位掩码。</span><span class="sxs-lookup"><span data-stu-id="31250-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="31250-109">以下值有效，并可以通过 **OR** 位运算组合：</span><span class="sxs-lookup"><span data-stu-id="31250-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="31250-110">值</span><span class="sxs-lookup"><span data-stu-id="31250-110">Value</span></span> |<span data-ttu-id="31250-111">说明</span><span class="sxs-lookup"><span data-stu-id="31250-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="31250-112">**1**</span><span class="sxs-lookup"><span data-stu-id="31250-112">**1**</span></span> | <span data-ttu-id="31250-113">常规的一致性检查。</span><span class="sxs-lookup"><span data-stu-id="31250-113">A normal consistency check.</span></span> |
|<span data-ttu-id="31250-114">**2**</span><span class="sxs-lookup"><span data-stu-id="31250-114">**2**</span></span> | <span data-ttu-id="31250-115">重启后一致性检查的延续。</span><span class="sxs-lookup"><span data-stu-id="31250-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="31250-116">此值不应与其他值组合。</span><span class="sxs-lookup"><span data-stu-id="31250-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="31250-117">**4**</span><span class="sxs-lookup"><span data-stu-id="31250-117">**4**</span></span> | <span data-ttu-id="31250-118">应从节点的元配置中指定的请求服务器请求配置。</span><span class="sxs-lookup"><span data-stu-id="31250-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="31250-119">此值应始终与 **1** 组合，以获得为 **5** 的值。</span><span class="sxs-lookup"><span data-stu-id="31250-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="31250-120">**8**</span><span class="sxs-lookup"><span data-stu-id="31250-120">**8**</span></span> | <span data-ttu-id="31250-121">将状态发送到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="31250-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="31250-122">返回值</span><span class="sxs-lookup"><span data-stu-id="31250-122">Return value</span></span>
------------

<span data-ttu-id="31250-123">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="31250-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="31250-124">备注</span><span class="sxs-lookup"><span data-stu-id="31250-124">Remarks</span></span>

<span data-ttu-id="31250-125">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="31250-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="31250-126">要求</span><span class="sxs-lookup"><span data-stu-id="31250-126">Requirements</span></span>
------------
><span data-ttu-id="31250-127">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="31250-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="31250-128">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="31250-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="31250-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31250-129">See also</span></span>


[<span data-ttu-id="31250-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="31250-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



