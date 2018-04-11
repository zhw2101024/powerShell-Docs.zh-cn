---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApplyAsync 方法
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="09fee-103">MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="09fee-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="09fee-104">将配置文档异步发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="09fee-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="09fee-105">语法</span><span class="sxs-lookup"><span data-stu-id="09fee-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="09fee-106">参数</span><span class="sxs-lookup"><span data-stu-id="09fee-106">Parameters</span></span>
----------

<span data-ttu-id="09fee-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="09fee-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="09fee-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="09fee-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="09fee-109">jobId \[in\]：为其发送配置的作业的 ID。</span><span class="sxs-lookup"><span data-stu-id="09fee-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="09fee-110">返回值</span><span class="sxs-lookup"><span data-stu-id="09fee-110">Return value</span></span>
------------

<span data-ttu-id="09fee-111">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="09fee-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="09fee-112">备注</span><span class="sxs-lookup"><span data-stu-id="09fee-112">Remarks</span></span>

<span data-ttu-id="09fee-113">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="09fee-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="09fee-114">要求</span><span class="sxs-lookup"><span data-stu-id="09fee-114">Requirements</span></span>
------------
><span data-ttu-id="09fee-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="09fee-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="09fee-116">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="09fee-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="09fee-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09fee-117">See also</span></span>


[<span data-ttu-id="09fee-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="09fee-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)