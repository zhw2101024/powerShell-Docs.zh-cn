---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApplyAsync 方法"
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0d681-103">MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="0d681-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0d681-104">将配置文档异步发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="0d681-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="0d681-105">语法</span><span class="sxs-lookup"><span data-stu-id="0d681-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="0d681-106">参数</span><span class="sxs-lookup"><span data-stu-id="0d681-106">Parameters</span></span>
----------

<span data-ttu-id="0d681-107">ConfigurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="0d681-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="0d681-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="0d681-108">The environment data for the configuration.</span></span>

<span data-ttu-id="0d681-109">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="0d681-109">*force* \[in\]</span></span>  
<span data-ttu-id="0d681-110">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="0d681-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="0d681-111">jobId \[in\]</span><span class="sxs-lookup"><span data-stu-id="0d681-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="0d681-112">为其发送配置的作业 ID。</span><span class="sxs-lookup"><span data-stu-id="0d681-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d681-113">返回值</span><span class="sxs-lookup"><span data-stu-id="0d681-113">Return value</span></span>
------------

<span data-ttu-id="0d681-114">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="0d681-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d681-115">备注</span><span class="sxs-lookup"><span data-stu-id="0d681-115">Remarks</span></span>

<span data-ttu-id="0d681-116">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="0d681-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d681-117">要求</span><span class="sxs-lookup"><span data-stu-id="0d681-117">Requirements</span></span>
------------
><span data-ttu-id="0d681-118">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0d681-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0d681-119">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d681-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0d681-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d681-120">See also</span></span>


[<span data-ttu-id="0d681-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0d681-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



