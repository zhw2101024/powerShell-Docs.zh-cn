---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e3abf-103">MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法</span><span class="sxs-lookup"><span data-stu-id="e3abf-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e3abf-104">使用任务计划程序启动一致性检查。</span><span class="sxs-lookup"><span data-stu-id="e3abf-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="e3abf-105">语法</span><span class="sxs-lookup"><span data-stu-id="e3abf-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="e3abf-106">参数</span><span class="sxs-lookup"><span data-stu-id="e3abf-106">Parameters</span></span>
----------

<span data-ttu-id="e3abf-107">Flags \[in\]</span><span class="sxs-lookup"><span data-stu-id="e3abf-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="e3abf-108">指定要运行的一致性检查类型的位掩码。</span><span class="sxs-lookup"><span data-stu-id="e3abf-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="e3abf-109">以下值有效，并可以通过 **OR** 位运算组合：</span><span class="sxs-lookup"><span data-stu-id="e3abf-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="e3abf-110">值</span><span class="sxs-lookup"><span data-stu-id="e3abf-110">Value</span></span> |<span data-ttu-id="e3abf-111">说明</span><span class="sxs-lookup"><span data-stu-id="e3abf-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="e3abf-112">**1**</span><span class="sxs-lookup"><span data-stu-id="e3abf-112">**1**</span></span> | <span data-ttu-id="e3abf-113">常规的一致性检查。</span><span class="sxs-lookup"><span data-stu-id="e3abf-113">A normal consistency check.</span></span> |
|<span data-ttu-id="e3abf-114">**2**</span><span class="sxs-lookup"><span data-stu-id="e3abf-114">**2**</span></span> | <span data-ttu-id="e3abf-115">重启后一致性检查的延续。</span><span class="sxs-lookup"><span data-stu-id="e3abf-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="e3abf-116">此值不应与其他值组合。</span><span class="sxs-lookup"><span data-stu-id="e3abf-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="e3abf-117">**4**</span><span class="sxs-lookup"><span data-stu-id="e3abf-117">**4**</span></span> | <span data-ttu-id="e3abf-118">应从节点的元配置中指定的请求服务器请求配置。</span><span class="sxs-lookup"><span data-stu-id="e3abf-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="e3abf-119">此值应始终与 **1** 组合，以获得为 **5** 的值。</span><span class="sxs-lookup"><span data-stu-id="e3abf-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="e3abf-120">**8**</span><span class="sxs-lookup"><span data-stu-id="e3abf-120">**8**</span></span> | <span data-ttu-id="e3abf-121">将状态发送到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="e3abf-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e3abf-122">返回值</span><span class="sxs-lookup"><span data-stu-id="e3abf-122">Return value</span></span>
------------

<span data-ttu-id="e3abf-123">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="e3abf-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3abf-124">备注</span><span class="sxs-lookup"><span data-stu-id="e3abf-124">Remarks</span></span>

<span data-ttu-id="e3abf-125">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="e3abf-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3abf-126">要求</span><span class="sxs-lookup"><span data-stu-id="e3abf-126">Requirements</span></span>
------------
><span data-ttu-id="e3abf-127">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e3abf-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e3abf-128">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e3abf-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e3abf-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3abf-129">See also</span></span>


[<span data-ttu-id="e3abf-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e3abf-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



