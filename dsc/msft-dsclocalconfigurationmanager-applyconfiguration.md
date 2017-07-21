---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 ApplyConfiguration 方法"
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7944f-103">MSFT_DSCLocalConfigurationManager 类的 ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="7944f-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7944f-104">使用配置代理应用处于挂起状态的配置。</span><span class="sxs-lookup"><span data-stu-id="7944f-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="7944f-105">如果没有挂起的配置，此方法将重新应用当前配置。</span><span class="sxs-lookup"><span data-stu-id="7944f-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="7944f-106">语法</span><span class="sxs-lookup"><span data-stu-id="7944f-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="7944f-107">参数</span><span class="sxs-lookup"><span data-stu-id="7944f-107">Parameters</span></span>
----------

<span data-ttu-id="7944f-108">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="7944f-108">*force* \[in\]</span></span>  
<span data-ttu-id="7944f-109">如果为 **true**，将会重新应用当前配置，即使存在挂起的配置。</span><span class="sxs-lookup"><span data-stu-id="7944f-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="7944f-110">返回值</span><span class="sxs-lookup"><span data-stu-id="7944f-110">Return value</span></span>
------------

<span data-ttu-id="7944f-111">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="7944f-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7944f-112">备注</span><span class="sxs-lookup"><span data-stu-id="7944f-112">Remarks</span></span>

<span data-ttu-id="7944f-113">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="7944f-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7944f-114">要求</span><span class="sxs-lookup"><span data-stu-id="7944f-114">Requirements</span></span>
------------
><span data-ttu-id="7944f-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7944f-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7944f-116">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7944f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7944f-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7944f-117">See also</span></span>


[<span data-ttu-id="7944f-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7944f-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



