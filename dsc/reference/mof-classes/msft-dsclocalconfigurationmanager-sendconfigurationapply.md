---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676254"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3071c-103">MSFT_DSCLocalConfigurationManager 类的 SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="3071c-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3071c-104">将配置文档发送到托管节点，并使用配置代理应用配置。</span><span class="sxs-lookup"><span data-stu-id="3071c-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="3071c-105">语法</span><span class="sxs-lookup"><span data-stu-id="3071c-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="3071c-106">参数</span><span class="sxs-lookup"><span data-stu-id="3071c-106">Parameters</span></span>

<span data-ttu-id="3071c-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="3071c-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="3071c-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="3071c-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="3071c-109">返回值</span><span class="sxs-lookup"><span data-stu-id="3071c-109">Return value</span></span>

<span data-ttu-id="3071c-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="3071c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3071c-111">备注</span><span class="sxs-lookup"><span data-stu-id="3071c-111">Remarks</span></span>

<span data-ttu-id="3071c-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="3071c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3071c-113">要求</span><span class="sxs-lookup"><span data-stu-id="3071c-113">Requirements</span></span>

<span data-ttu-id="3071c-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3071c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3071c-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3071c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3071c-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3071c-116">See also</span></span>

[<span data-ttu-id="3071c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3071c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)