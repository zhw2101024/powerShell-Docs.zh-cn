---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047133"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a3b75-103">MSFT_DSCLocalConfigurationManager 类的 GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="a3b75-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a3b75-104">获取与特定作业相关的配置代理输出。</span><span class="sxs-lookup"><span data-stu-id="a3b75-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3b75-105">语法</span><span class="sxs-lookup"><span data-stu-id="a3b75-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="a3b75-106">参数</span><span class="sxs-lookup"><span data-stu-id="a3b75-106">Parameters</span></span>

<span data-ttu-id="a3b75-107">jobId \[in\]：要为其获取输出数据的作业的 ID。</span><span class="sxs-lookup"><span data-stu-id="a3b75-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="a3b75-108">resumeOutputBookmark \[in\]：指定输出应接着上一书签。</span><span class="sxs-lookup"><span data-stu-id="a3b75-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="a3b75-109">output \[out\]：指定作业的输出。</span><span class="sxs-lookup"><span data-stu-id="a3b75-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="a3b75-110">返回值</span><span class="sxs-lookup"><span data-stu-id="a3b75-110">Return value</span></span>

<span data-ttu-id="a3b75-111">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="a3b75-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3b75-112">备注</span><span class="sxs-lookup"><span data-stu-id="a3b75-112">Remarks</span></span>

<span data-ttu-id="a3b75-113">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="a3b75-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3b75-114">要求</span><span class="sxs-lookup"><span data-stu-id="a3b75-114">Requirements</span></span>

<span data-ttu-id="a3b75-115">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a3b75-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a3b75-116">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3b75-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a3b75-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3b75-117">See also</span></span>

[<span data-ttu-id="a3b75-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a3b75-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)