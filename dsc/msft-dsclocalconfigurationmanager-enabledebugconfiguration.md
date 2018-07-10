---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892393"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f5b0f-103">MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="f5b0f-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f5b0f-104">启用 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="f5b0f-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5b0f-105">语法</span><span class="sxs-lookup"><span data-stu-id="f5b0f-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="f5b0f-106">参数</span><span class="sxs-lookup"><span data-stu-id="f5b0f-106">Parameters</span></span>

<span data-ttu-id="f5b0f-107">BreakAll \[in\]：在资源脚本中的每一行设置断点。</span><span class="sxs-lookup"><span data-stu-id="f5b0f-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5b0f-108">返回值</span><span class="sxs-lookup"><span data-stu-id="f5b0f-108">Return value</span></span>

<span data-ttu-id="f5b0f-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="f5b0f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5b0f-110">备注</span><span class="sxs-lookup"><span data-stu-id="f5b0f-110">Remarks</span></span>

<span data-ttu-id="f5b0f-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="f5b0f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5b0f-112">要求</span><span class="sxs-lookup"><span data-stu-id="f5b0f-112">Requirements</span></span>

<span data-ttu-id="f5b0f-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f5b0f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f5b0f-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f5b0f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f5b0f-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5b0f-115">See also</span></span>

[<span data-ttu-id="f5b0f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f5b0f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)