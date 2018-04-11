---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ac1b0-103">MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="ac1b0-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ac1b0-104">设置用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="ac1b0-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="ac1b0-105">语法</span><span class="sxs-lookup"><span data-stu-id="ac1b0-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ac1b0-106">参数</span><span class="sxs-lookup"><span data-stu-id="ac1b0-106">Parameters</span></span>
----------

<span data-ttu-id="ac1b0-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="ac1b0-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ac1b0-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="ac1b0-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ac1b0-109">返回值</span><span class="sxs-lookup"><span data-stu-id="ac1b0-109">Return value</span></span>
------------

<span data-ttu-id="ac1b0-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="ac1b0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac1b0-111">备注</span><span class="sxs-lookup"><span data-stu-id="ac1b0-111">Remarks</span></span>

<span data-ttu-id="ac1b0-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="ac1b0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac1b0-113">要求</span><span class="sxs-lookup"><span data-stu-id="ac1b0-113">Requirements</span></span>
------------
><span data-ttu-id="ac1b0-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ac1b0-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ac1b0-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac1b0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ac1b0-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac1b0-116">See also</span></span>


[<span data-ttu-id="ac1b0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ac1b0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)