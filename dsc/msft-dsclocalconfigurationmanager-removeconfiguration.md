---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法"
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7c5c4-103">MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="7c5c4-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7c5c4-104">删除配置文件。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="7c5c4-105">语法</span><span class="sxs-lookup"><span data-stu-id="7c5c4-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="7c5c4-106">参数</span><span class="sxs-lookup"><span data-stu-id="7c5c4-106">Parameters</span></span>
----------

<span data-ttu-id="7c5c4-107">Stage \[in\]</span><span class="sxs-lookup"><span data-stu-id="7c5c4-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="7c5c4-108">指定要删除的配置文档。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="7c5c4-109">下面的值是有效的：</span><span class="sxs-lookup"><span data-stu-id="7c5c4-109">The following values are valid:</span></span>

|<span data-ttu-id="7c5c4-110">值</span><span class="sxs-lookup"><span data-stu-id="7c5c4-110">Value</span></span> |<span data-ttu-id="7c5c4-111">说明</span><span class="sxs-lookup"><span data-stu-id="7c5c4-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="7c5c4-112">**1**</span><span class="sxs-lookup"><span data-stu-id="7c5c4-112">**1**</span></span> | <span data-ttu-id="7c5c4-113">**当前**配置文档 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="7c5c4-114">**2**</span><span class="sxs-lookup"><span data-stu-id="7c5c4-114">**2**</span></span> | <span data-ttu-id="7c5c4-115">**挂起的**配置文档 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="7c5c4-116">**4**</span><span class="sxs-lookup"><span data-stu-id="7c5c4-116">**4**</span></span> | <span data-ttu-id="7c5c4-117">**以前的**配置文档 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="7c5c4-118">Force \[in\]</span><span class="sxs-lookup"><span data-stu-id="7c5c4-118">*Force* \[in\]</span></span>  
<span data-ttu-id="7c5c4-119">为 **true**，则强制删除配置。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="7c5c4-120">返回值</span><span class="sxs-lookup"><span data-stu-id="7c5c4-120">Return value</span></span>
------------

<span data-ttu-id="7c5c4-121">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c5c4-122">备注</span><span class="sxs-lookup"><span data-stu-id="7c5c4-122">Remarks</span></span>

<span data-ttu-id="7c5c4-123">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="7c5c4-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c5c4-124">要求</span><span class="sxs-lookup"><span data-stu-id="7c5c4-124">Requirements</span></span>
------------
><span data-ttu-id="7c5c4-125">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7c5c4-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7c5c4-126">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c5c4-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7c5c4-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c5c4-127">See also</span></span>


[<span data-ttu-id="7c5c4-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7c5c4-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



