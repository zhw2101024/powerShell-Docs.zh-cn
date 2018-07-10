---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApplyAsync 方法
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893886"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="338b1-103">MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="338b1-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="338b1-104">将配置文档异步发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="338b1-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="338b1-105">语法</span><span class="sxs-lookup"><span data-stu-id="338b1-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="338b1-106">参数</span><span class="sxs-lookup"><span data-stu-id="338b1-106">Parameters</span></span>

<span data-ttu-id="338b1-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="338b1-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="338b1-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="338b1-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="338b1-109">jobId \[in\]：为其发送配置的作业的 ID。</span><span class="sxs-lookup"><span data-stu-id="338b1-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="338b1-110">返回值</span><span class="sxs-lookup"><span data-stu-id="338b1-110">Return value</span></span>

<span data-ttu-id="338b1-111">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="338b1-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="338b1-112">备注</span><span class="sxs-lookup"><span data-stu-id="338b1-112">Remarks</span></span>

<span data-ttu-id="338b1-113">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="338b1-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="338b1-114">要求</span><span class="sxs-lookup"><span data-stu-id="338b1-114">Requirements</span></span>

<span data-ttu-id="338b1-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="338b1-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="338b1-116">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="338b1-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="338b1-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="338b1-117">See also</span></span>

[<span data-ttu-id="338b1-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="338b1-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)