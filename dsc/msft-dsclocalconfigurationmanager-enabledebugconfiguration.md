---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="07570-103">MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="07570-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="07570-104">启用 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="07570-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="07570-105">语法</span><span class="sxs-lookup"><span data-stu-id="07570-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="07570-106">参数</span><span class="sxs-lookup"><span data-stu-id="07570-106">Parameters</span></span>
----------

<span data-ttu-id="07570-107">BreakAll \[in\]：在资源脚本中的每一行设置断点。</span><span class="sxs-lookup"><span data-stu-id="07570-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="07570-108">返回值</span><span class="sxs-lookup"><span data-stu-id="07570-108">Return value</span></span>
------------

<span data-ttu-id="07570-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="07570-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="07570-110">备注</span><span class="sxs-lookup"><span data-stu-id="07570-110">Remarks</span></span>

<span data-ttu-id="07570-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="07570-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="07570-112">要求</span><span class="sxs-lookup"><span data-stu-id="07570-112">Requirements</span></span>
------------
><span data-ttu-id="07570-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="07570-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="07570-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="07570-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="07570-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07570-115">See also</span></span>


[<span data-ttu-id="07570-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="07570-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)