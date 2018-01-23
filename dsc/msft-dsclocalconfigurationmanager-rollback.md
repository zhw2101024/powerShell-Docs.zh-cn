---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 RollBack 方法"
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="38021-103">MSFT_DSCLocalConfigurationManager 类的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="38021-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="38021-104">将配置回滚到以前的版本。</span><span class="sxs-lookup"><span data-stu-id="38021-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="38021-105">语法</span><span class="sxs-lookup"><span data-stu-id="38021-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="38021-106">参数</span><span class="sxs-lookup"><span data-stu-id="38021-106">Parameters</span></span>
----------

<span data-ttu-id="38021-107">configurationNumber \[in\]</span><span class="sxs-lookup"><span data-stu-id="38021-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="38021-108">指定请求的配置。</span><span class="sxs-lookup"><span data-stu-id="38021-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="38021-109">返回值</span><span class="sxs-lookup"><span data-stu-id="38021-109">Return value</span></span>
------------

<span data-ttu-id="38021-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="38021-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="38021-111">备注</span><span class="sxs-lookup"><span data-stu-id="38021-111">Remarks</span></span>

<span data-ttu-id="38021-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="38021-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="38021-113">要求</span><span class="sxs-lookup"><span data-stu-id="38021-113">Requirements</span></span>
------------
><span data-ttu-id="38021-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="38021-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="38021-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="38021-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="38021-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38021-116">See also</span></span>


[<span data-ttu-id="38021-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="38021-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



