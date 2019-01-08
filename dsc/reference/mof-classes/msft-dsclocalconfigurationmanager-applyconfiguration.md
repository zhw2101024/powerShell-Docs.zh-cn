---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 ApplyConfiguration 方法
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047052"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8f0a6-103">MSFT_DSCLocalConfigurationManager 类的 ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="8f0a6-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8f0a6-104">使用配置代理应用处于挂起状态的配置。</span><span class="sxs-lookup"><span data-stu-id="8f0a6-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="8f0a6-105">如果没有挂起的配置，此方法将重新应用当前配置。</span><span class="sxs-lookup"><span data-stu-id="8f0a6-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f0a6-106">语法</span><span class="sxs-lookup"><span data-stu-id="8f0a6-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8f0a6-107">参数</span><span class="sxs-lookup"><span data-stu-id="8f0a6-107">Parameters</span></span>

<span data-ttu-id="8f0a6-108">force \[in\]：若为 true，将会重新应用当前配置，即使有挂起的配置，也不例外。</span><span class="sxs-lookup"><span data-stu-id="8f0a6-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="8f0a6-109">返回值</span><span class="sxs-lookup"><span data-stu-id="8f0a6-109">Return value</span></span>

<span data-ttu-id="8f0a6-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="8f0a6-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f0a6-111">备注</span><span class="sxs-lookup"><span data-stu-id="8f0a6-111">Remarks</span></span>

<span data-ttu-id="8f0a6-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="8f0a6-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f0a6-113">要求</span><span class="sxs-lookup"><span data-stu-id="8f0a6-113">Requirements</span></span>

<span data-ttu-id="8f0a6-114">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8f0a6-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8f0a6-115">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8f0a6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8f0a6-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f0a6-116">See also</span></span>

[<span data-ttu-id="8f0a6-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8f0a6-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)