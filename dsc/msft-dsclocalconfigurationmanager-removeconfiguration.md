---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2072f-103">MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="2072f-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2072f-104">删除配置文件。</span><span class="sxs-lookup"><span data-stu-id="2072f-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="2072f-105">语法</span><span class="sxs-lookup"><span data-stu-id="2072f-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="2072f-106">参数</span><span class="sxs-lookup"><span data-stu-id="2072f-106">Parameters</span></span>
----------

<span data-ttu-id="2072f-107">Stage \[in\]</span><span class="sxs-lookup"><span data-stu-id="2072f-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="2072f-108">指定要删除的配置文档。</span><span class="sxs-lookup"><span data-stu-id="2072f-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="2072f-109">下面的值是有效的：</span><span class="sxs-lookup"><span data-stu-id="2072f-109">The following values are valid:</span></span>

|<span data-ttu-id="2072f-110">值</span><span class="sxs-lookup"><span data-stu-id="2072f-110">Value</span></span> |<span data-ttu-id="2072f-111">说明</span><span class="sxs-lookup"><span data-stu-id="2072f-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="2072f-112">**1**</span><span class="sxs-lookup"><span data-stu-id="2072f-112">**1**</span></span> | <span data-ttu-id="2072f-113">**当前**配置文档 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="2072f-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="2072f-114">**2**</span><span class="sxs-lookup"><span data-stu-id="2072f-114">**2**</span></span> | <span data-ttu-id="2072f-115">**挂起的**配置文档 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="2072f-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="2072f-116">**4**</span><span class="sxs-lookup"><span data-stu-id="2072f-116">**4**</span></span> | <span data-ttu-id="2072f-117">**以前的**配置文档 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="2072f-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="2072f-118">Force \[in\]</span><span class="sxs-lookup"><span data-stu-id="2072f-118">*Force* \[in\]</span></span>  
<span data-ttu-id="2072f-119">为 **true**，则强制删除配置。</span><span class="sxs-lookup"><span data-stu-id="2072f-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="2072f-120">返回值</span><span class="sxs-lookup"><span data-stu-id="2072f-120">Return value</span></span>
------------

<span data-ttu-id="2072f-121">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="2072f-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2072f-122">备注</span><span class="sxs-lookup"><span data-stu-id="2072f-122">Remarks</span></span>

<span data-ttu-id="2072f-123">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="2072f-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2072f-124">要求</span><span class="sxs-lookup"><span data-stu-id="2072f-124">Requirements</span></span>
------------
><span data-ttu-id="2072f-125">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2072f-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2072f-126">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2072f-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2072f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2072f-127">See also</span></span>


[<span data-ttu-id="2072f-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2072f-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



