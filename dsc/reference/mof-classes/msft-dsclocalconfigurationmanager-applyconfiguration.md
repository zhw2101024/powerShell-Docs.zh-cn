---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: ApplyConfiguration 方法
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727180"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="2998b-103">ApplyConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="2998b-103">ApplyConfiguration method</span></span>

<span data-ttu-id="2998b-104">使用配置代理应用处于挂起状态的配置。</span><span class="sxs-lookup"><span data-stu-id="2998b-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="2998b-105">如果没有挂起的配置，此方法将重新应用当前配置。</span><span class="sxs-lookup"><span data-stu-id="2998b-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="2998b-106">语法</span><span class="sxs-lookup"><span data-stu-id="2998b-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="2998b-107">参数</span><span class="sxs-lookup"><span data-stu-id="2998b-107">Parameters</span></span>

<span data-ttu-id="2998b-108">force  \[in\]：若为 true  ，将会重新应用当前配置，即使有挂起的配置，也不例外。</span><span class="sxs-lookup"><span data-stu-id="2998b-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="2998b-109">返回值</span><span class="sxs-lookup"><span data-stu-id="2998b-109">Return value</span></span>

<span data-ttu-id="2998b-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="2998b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2998b-111">备注</span><span class="sxs-lookup"><span data-stu-id="2998b-111">Remarks</span></span>

<span data-ttu-id="2998b-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="2998b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2998b-113">要求</span><span class="sxs-lookup"><span data-stu-id="2998b-113">Requirements</span></span>

<span data-ttu-id="2998b-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2998b-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2998b-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2998b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2998b-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2998b-116">See also</span></span>

[<span data-ttu-id="2998b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2998b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
