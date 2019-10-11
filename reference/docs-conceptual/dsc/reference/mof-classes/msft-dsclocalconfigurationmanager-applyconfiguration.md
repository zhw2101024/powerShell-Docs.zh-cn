---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: ApplyConfiguration 方法
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953454"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="d2245-103">ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="d2245-103">ApplyConfiguration method</span></span>

<span data-ttu-id="d2245-104">使用配置代理应用处于挂起状态的配置。</span><span class="sxs-lookup"><span data-stu-id="d2245-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="d2245-105">如果没有挂起的配置，此方法将重新应用当前配置。</span><span class="sxs-lookup"><span data-stu-id="d2245-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2245-106">语法</span><span class="sxs-lookup"><span data-stu-id="d2245-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d2245-107">参数</span><span class="sxs-lookup"><span data-stu-id="d2245-107">Parameters</span></span>

<span data-ttu-id="d2245-108">force  \[in\]：若为 true  ，将会重新应用当前配置，即使有挂起的配置，也不例外。</span><span class="sxs-lookup"><span data-stu-id="d2245-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2245-109">返回值</span><span class="sxs-lookup"><span data-stu-id="d2245-109">Return value</span></span>

<span data-ttu-id="d2245-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="d2245-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2245-111">备注</span><span class="sxs-lookup"><span data-stu-id="d2245-111">Remarks</span></span>

<span data-ttu-id="d2245-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="d2245-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2245-113">要求</span><span class="sxs-lookup"><span data-stu-id="d2245-113">Requirements</span></span>

<span data-ttu-id="d2245-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d2245-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d2245-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2245-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d2245-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2245-116">See also</span></span>

[<span data-ttu-id="d2245-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d2245-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
