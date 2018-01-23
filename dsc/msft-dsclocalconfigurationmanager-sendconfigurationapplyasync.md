---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApplyAsync 方法"
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="55f9a-103">MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="55f9a-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="55f9a-104">将配置文档异步发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="55f9a-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="55f9a-105">语法</span><span class="sxs-lookup"><span data-stu-id="55f9a-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="55f9a-106">参数</span><span class="sxs-lookup"><span data-stu-id="55f9a-106">Parameters</span></span>
----------

<span data-ttu-id="55f9a-107">ConfigurationData \[in\]</span><span class="sxs-lookup"><span data-stu-id="55f9a-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="55f9a-108">配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="55f9a-108">The environment data for the configuration.</span></span>

<span data-ttu-id="55f9a-109">force \[in\]</span><span class="sxs-lookup"><span data-stu-id="55f9a-109">*force* \[in\]</span></span>  
<span data-ttu-id="55f9a-110">为 **true**，则强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="55f9a-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="55f9a-111">jobId \[in\]</span><span class="sxs-lookup"><span data-stu-id="55f9a-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="55f9a-112">为其发送配置的作业 ID。</span><span class="sxs-lookup"><span data-stu-id="55f9a-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="55f9a-113">返回值</span><span class="sxs-lookup"><span data-stu-id="55f9a-113">Return value</span></span>
------------

<span data-ttu-id="55f9a-114">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="55f9a-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="55f9a-115">备注</span><span class="sxs-lookup"><span data-stu-id="55f9a-115">Remarks</span></span>

<span data-ttu-id="55f9a-116">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="55f9a-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="55f9a-117">要求</span><span class="sxs-lookup"><span data-stu-id="55f9a-117">Requirements</span></span>
------------
><span data-ttu-id="55f9a-118">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="55f9a-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="55f9a-119">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="55f9a-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="55f9a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="55f9a-120">See also</span></span>


[<span data-ttu-id="55f9a-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="55f9a-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



