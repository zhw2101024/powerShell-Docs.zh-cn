---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: SendConfigurationApplyAsync 方法
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953374"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="913c0-103">SendConfigurationApplyAsync 方法</span><span class="sxs-lookup"><span data-stu-id="913c0-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="913c0-104">将配置文档异步发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="913c0-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="913c0-105">语法</span><span class="sxs-lookup"><span data-stu-id="913c0-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="913c0-106">参数</span><span class="sxs-lookup"><span data-stu-id="913c0-106">Parameters</span></span>

<span data-ttu-id="913c0-107">ConfigurationData  \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="913c0-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="913c0-108">force  \[in\]：若为 true  ，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="913c0-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="913c0-109">jobId  \[in\]：为其发送配置的作业的 ID。</span><span class="sxs-lookup"><span data-stu-id="913c0-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="913c0-110">返回值</span><span class="sxs-lookup"><span data-stu-id="913c0-110">Return value</span></span>

<span data-ttu-id="913c0-111">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="913c0-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="913c0-112">备注</span><span class="sxs-lookup"><span data-stu-id="913c0-112">Remarks</span></span>

<span data-ttu-id="913c0-113">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="913c0-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="913c0-114">要求</span><span class="sxs-lookup"><span data-stu-id="913c0-114">Requirements</span></span>

<span data-ttu-id="913c0-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="913c0-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="913c0-116">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="913c0-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="913c0-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="913c0-117">See also</span></span>

[<span data-ttu-id="913c0-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="913c0-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
