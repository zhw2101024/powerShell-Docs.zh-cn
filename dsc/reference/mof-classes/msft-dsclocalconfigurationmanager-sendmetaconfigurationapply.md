---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677403"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9bea4-103">MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="9bea4-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9bea4-104">设置用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="9bea4-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bea4-105">语法</span><span class="sxs-lookup"><span data-stu-id="9bea4-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9bea4-106">参数</span><span class="sxs-lookup"><span data-stu-id="9bea4-106">Parameters</span></span>

<span data-ttu-id="9bea4-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="9bea4-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9bea4-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="9bea4-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9bea4-109">返回值</span><span class="sxs-lookup"><span data-stu-id="9bea4-109">Return value</span></span>

<span data-ttu-id="9bea4-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="9bea4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9bea4-111">备注</span><span class="sxs-lookup"><span data-stu-id="9bea4-111">Remarks</span></span>

<span data-ttu-id="9bea4-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="9bea4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9bea4-113">要求</span><span class="sxs-lookup"><span data-stu-id="9bea4-113">Requirements</span></span>

<span data-ttu-id="9bea4-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9bea4-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9bea4-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9bea4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9bea4-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9bea4-116">See also</span></span>

[<span data-ttu-id="9bea4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9bea4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)