---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法"
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="35d82-103">MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="35d82-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="35d82-104">停止正在进行的配置更改。</span><span class="sxs-lookup"><span data-stu-id="35d82-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="35d82-105">语法</span><span class="sxs-lookup"><span data-stu-id="35d82-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="35d82-106">参数</span><span class="sxs-lookup"><span data-stu-id="35d82-106">Parameters</span></span>
----------

<span data-ttu-id="35d82-107">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="35d82-107">*force* \[in\]</span></span>  
<span data-ttu-id="35d82-108">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="35d82-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="35d82-109">返回值</span><span class="sxs-lookup"><span data-stu-id="35d82-109">Return value</span></span>
------------

<span data-ttu-id="35d82-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="35d82-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="35d82-111">备注</span><span class="sxs-lookup"><span data-stu-id="35d82-111">Remarks</span></span>

<span data-ttu-id="35d82-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="35d82-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="35d82-113">要求</span><span class="sxs-lookup"><span data-stu-id="35d82-113">Requirements</span></span>
------------
><span data-ttu-id="35d82-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="35d82-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="35d82-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="35d82-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="35d82-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35d82-116">See also</span></span>


[<span data-ttu-id="35d82-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="35d82-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



