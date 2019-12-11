---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: GetConfigurationResultOutput 方法
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953414"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="e60a3-103">GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="e60a3-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="e60a3-104">获取与特定作业相关的配置代理输出。</span><span class="sxs-lookup"><span data-stu-id="e60a3-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="e60a3-105">语法</span><span class="sxs-lookup"><span data-stu-id="e60a3-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="e60a3-106">参数</span><span class="sxs-lookup"><span data-stu-id="e60a3-106">Parameters</span></span>

<span data-ttu-id="e60a3-107">jobId  \[in\]：要为其获取输出数据的作业的 ID。</span><span class="sxs-lookup"><span data-stu-id="e60a3-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="e60a3-108">resumeOutputBookmark  \[in\]：指定输出应接着上一书签。</span><span class="sxs-lookup"><span data-stu-id="e60a3-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="e60a3-109">output  \[out\]：指定作业的输出。</span><span class="sxs-lookup"><span data-stu-id="e60a3-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="e60a3-110">返回值</span><span class="sxs-lookup"><span data-stu-id="e60a3-110">Return value</span></span>

<span data-ttu-id="e60a3-111">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="e60a3-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e60a3-112">备注</span><span class="sxs-lookup"><span data-stu-id="e60a3-112">Remarks</span></span>

<span data-ttu-id="e60a3-113">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="e60a3-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e60a3-114">要求</span><span class="sxs-lookup"><span data-stu-id="e60a3-114">Requirements</span></span>

<span data-ttu-id="e60a3-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e60a3-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e60a3-116">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e60a3-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e60a3-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e60a3-117">See also</span></span>

[<span data-ttu-id="e60a3-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e60a3-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
