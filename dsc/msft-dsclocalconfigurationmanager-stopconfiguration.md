---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法"
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="60392-103">MSFT_DSCLocalConfigurationManager 类的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="60392-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="60392-104">停止正在进行的配置更改。</span><span class="sxs-lookup"><span data-stu-id="60392-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="60392-105">语法</span><span class="sxs-lookup"><span data-stu-id="60392-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="60392-106">参数</span><span class="sxs-lookup"><span data-stu-id="60392-106">Parameters</span></span>
----------

<span data-ttu-id="60392-107">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="60392-107">*force* \[in\]</span></span>  
<span data-ttu-id="60392-108">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="60392-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="60392-109">返回值</span><span class="sxs-lookup"><span data-stu-id="60392-109">Return value</span></span>
------------

<span data-ttu-id="60392-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="60392-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="60392-111">备注</span><span class="sxs-lookup"><span data-stu-id="60392-111">Remarks</span></span>

<span data-ttu-id="60392-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="60392-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="60392-113">要求</span><span class="sxs-lookup"><span data-stu-id="60392-113">Requirements</span></span>
------------
><span data-ttu-id="60392-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="60392-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="60392-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="60392-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="60392-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60392-116">See also</span></span>


[<span data-ttu-id="60392-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="60392-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



