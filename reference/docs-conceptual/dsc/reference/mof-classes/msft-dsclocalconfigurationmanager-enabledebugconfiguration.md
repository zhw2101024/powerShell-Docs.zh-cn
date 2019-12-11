---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: EnableDebugConfiguration 方法
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953434"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="e4ec0-103">EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="e4ec0-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="e4ec0-104">启用 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="e4ec0-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4ec0-105">语法</span><span class="sxs-lookup"><span data-stu-id="e4ec0-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="e4ec0-106">参数</span><span class="sxs-lookup"><span data-stu-id="e4ec0-106">Parameters</span></span>

<span data-ttu-id="e4ec0-107">BreakAll  \[in\]：在资源脚本中的每一行设置断点。</span><span class="sxs-lookup"><span data-stu-id="e4ec0-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="e4ec0-108">返回值</span><span class="sxs-lookup"><span data-stu-id="e4ec0-108">Return value</span></span>

<span data-ttu-id="e4ec0-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="e4ec0-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4ec0-110">备注</span><span class="sxs-lookup"><span data-stu-id="e4ec0-110">Remarks</span></span>

<span data-ttu-id="e4ec0-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="e4ec0-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e4ec0-112">要求</span><span class="sxs-lookup"><span data-stu-id="e4ec0-112">Requirements</span></span>

<span data-ttu-id="e4ec0-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e4ec0-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e4ec0-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e4ec0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e4ec0-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4ec0-115">See also</span></span>

[<span data-ttu-id="e4ec0-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e4ec0-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
