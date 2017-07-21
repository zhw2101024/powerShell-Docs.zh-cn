---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 RollBack 方法"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cdb43-103">MSFT_DSCLocalConfigurationManager 类的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="cdb43-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cdb43-104">将配置回滚到以前的版本。</span><span class="sxs-lookup"><span data-stu-id="cdb43-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="cdb43-105">语法</span><span class="sxs-lookup"><span data-stu-id="cdb43-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="cdb43-106">参数</span><span class="sxs-lookup"><span data-stu-id="cdb43-106">Parameters</span></span>
----------

<span data-ttu-id="cdb43-107">configurationNumber \[in\]</span><span class="sxs-lookup"><span data-stu-id="cdb43-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="cdb43-108">指定请求的配置。</span><span class="sxs-lookup"><span data-stu-id="cdb43-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="cdb43-109">返回值</span><span class="sxs-lookup"><span data-stu-id="cdb43-109">Return value</span></span>
------------

<span data-ttu-id="cdb43-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="cdb43-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdb43-111">备注</span><span class="sxs-lookup"><span data-stu-id="cdb43-111">Remarks</span></span>

<span data-ttu-id="cdb43-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="cdb43-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdb43-113">要求</span><span class="sxs-lookup"><span data-stu-id="cdb43-113">Requirements</span></span>
------------
><span data-ttu-id="cdb43-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cdb43-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cdb43-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cdb43-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cdb43-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdb43-116">See also</span></span>


[<span data-ttu-id="cdb43-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cdb43-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



