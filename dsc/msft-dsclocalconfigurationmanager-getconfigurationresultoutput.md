---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186800"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b3de3-103">MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="b3de3-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b3de3-104">获取与特定作业相关的配置代理输出。</span><span class="sxs-lookup"><span data-stu-id="b3de3-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="b3de3-105">语法</span><span class="sxs-lookup"><span data-stu-id="b3de3-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="b3de3-106">参数</span><span class="sxs-lookup"><span data-stu-id="b3de3-106">Parameters</span></span>
----------

<span data-ttu-id="b3de3-107">jobId \[in\]：要为其获取输出数据的作业的 ID。</span><span class="sxs-lookup"><span data-stu-id="b3de3-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="b3de3-108">resumeOutputBookmark \[in\]：指定输出应接着上一书签。</span><span class="sxs-lookup"><span data-stu-id="b3de3-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="b3de3-109">output \[out\]：指定作业的输出。</span><span class="sxs-lookup"><span data-stu-id="b3de3-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="b3de3-110">返回值</span><span class="sxs-lookup"><span data-stu-id="b3de3-110">Return value</span></span>
------------

<span data-ttu-id="b3de3-111">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="b3de3-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3de3-112">备注</span><span class="sxs-lookup"><span data-stu-id="b3de3-112">Remarks</span></span>

<span data-ttu-id="b3de3-113">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="b3de3-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3de3-114">要求</span><span class="sxs-lookup"><span data-stu-id="b3de3-114">Requirements</span></span>
------------
><span data-ttu-id="b3de3-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b3de3-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b3de3-116">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b3de3-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b3de3-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3de3-117">See also</span></span>


[<span data-ttu-id="b3de3-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b3de3-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)