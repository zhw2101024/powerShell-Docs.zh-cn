---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法"
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="80603-103">MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="80603-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="80603-104">获取与特定作业相关的配置代理输出。</span><span class="sxs-lookup"><span data-stu-id="80603-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="80603-105">语法</span><span class="sxs-lookup"><span data-stu-id="80603-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="80603-106">参数</span><span class="sxs-lookup"><span data-stu-id="80603-106">Parameters</span></span>
----------

<span data-ttu-id="80603-107">jobId \[in\]</span><span class="sxs-lookup"><span data-stu-id="80603-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="80603-108">要为其获取输出数据的作业 ID。</span><span class="sxs-lookup"><span data-stu-id="80603-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="80603-109">resumeOutputBookmark \[in\]</span><span class="sxs-lookup"><span data-stu-id="80603-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="80603-110">指定输出应从上一个书签中延续。</span><span class="sxs-lookup"><span data-stu-id="80603-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="80603-111">output \[out\]</span><span class="sxs-lookup"><span data-stu-id="80603-111">*output* \[out\]</span></span>  
<span data-ttu-id="80603-112">指定作业的输出。</span><span class="sxs-lookup"><span data-stu-id="80603-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="80603-113">返回值</span><span class="sxs-lookup"><span data-stu-id="80603-113">Return value</span></span>
------------

<span data-ttu-id="80603-114">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="80603-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="80603-115">备注</span><span class="sxs-lookup"><span data-stu-id="80603-115">Remarks</span></span>

<span data-ttu-id="80603-116">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="80603-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="80603-117">要求</span><span class="sxs-lookup"><span data-stu-id="80603-117">Requirements</span></span>
------------
><span data-ttu-id="80603-118">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="80603-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="80603-119">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="80603-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="80603-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80603-120">See also</span></span>


[<span data-ttu-id="80603-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="80603-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



