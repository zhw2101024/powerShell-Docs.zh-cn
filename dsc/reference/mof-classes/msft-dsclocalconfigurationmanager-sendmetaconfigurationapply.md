---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047210"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fc969-103">MSFT_DSCLocalConfigurationManager 类的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="fc969-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fc969-104">设置用于控制配置代理的本地配置管理器设置。</span><span class="sxs-lookup"><span data-stu-id="fc969-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc969-105">语法</span><span class="sxs-lookup"><span data-stu-id="fc969-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="fc969-106">参数</span><span class="sxs-lookup"><span data-stu-id="fc969-106">Parameters</span></span>

<span data-ttu-id="fc969-107">ConfigurationData \[in\]：配置的环境数据。</span><span class="sxs-lookup"><span data-stu-id="fc969-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fc969-108">force \[in\]：若为 true，强制停止配置。</span><span class="sxs-lookup"><span data-stu-id="fc969-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="fc969-109">返回值</span><span class="sxs-lookup"><span data-stu-id="fc969-109">Return value</span></span>

<span data-ttu-id="fc969-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="fc969-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc969-111">备注</span><span class="sxs-lookup"><span data-stu-id="fc969-111">Remarks</span></span>

<span data-ttu-id="fc969-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="fc969-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc969-113">要求</span><span class="sxs-lookup"><span data-stu-id="fc969-113">Requirements</span></span>

<span data-ttu-id="fc969-114">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fc969-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fc969-115">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc969-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fc969-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc969-116">See also</span></span>

[<span data-ttu-id="fc969-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fc969-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)