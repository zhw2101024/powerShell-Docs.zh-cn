---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 ApplyConfiguration 方法"
ms.openlocfilehash: 72fbedf30e5058d8003ed620400d6b443d50dff6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d74f7-103">MSFT_DSCLocalConfigurationManager 类的 ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="d74f7-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d74f7-104">使用配置代理应用处于挂起状态的配置。</span><span class="sxs-lookup"><span data-stu-id="d74f7-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="d74f7-105">如果没有挂起的配置，此方法将重新应用当前配置。</span><span class="sxs-lookup"><span data-stu-id="d74f7-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="d74f7-106">语法</span><span class="sxs-lookup"><span data-stu-id="d74f7-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d74f7-107">参数</span><span class="sxs-lookup"><span data-stu-id="d74f7-107">Parameters</span></span>
----------

<span data-ttu-id="d74f7-108">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="d74f7-108">*force* \[in\]</span></span>  
<span data-ttu-id="d74f7-109">如果为 **true**，将会重新应用当前配置，即使存在挂起的配置。</span><span class="sxs-lookup"><span data-stu-id="d74f7-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="d74f7-110">返回值</span><span class="sxs-lookup"><span data-stu-id="d74f7-110">Return value</span></span>
------------

<span data-ttu-id="d74f7-111">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="d74f7-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d74f7-112">备注</span><span class="sxs-lookup"><span data-stu-id="d74f7-112">Remarks</span></span>

<span data-ttu-id="d74f7-113">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="d74f7-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d74f7-114">要求</span><span class="sxs-lookup"><span data-stu-id="d74f7-114">Requirements</span></span>
------------
><span data-ttu-id="d74f7-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d74f7-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d74f7-116">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d74f7-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d74f7-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d74f7-117">See also</span></span>


[<span data-ttu-id="d74f7-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d74f7-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



