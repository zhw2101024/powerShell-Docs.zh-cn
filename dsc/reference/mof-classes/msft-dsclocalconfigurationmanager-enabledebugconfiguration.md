---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078752"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="268db-103">MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="268db-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="268db-104">启用 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="268db-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="268db-105">语法</span><span class="sxs-lookup"><span data-stu-id="268db-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="268db-106">参数</span><span class="sxs-lookup"><span data-stu-id="268db-106">Parameters</span></span>

<span data-ttu-id="268db-107">BreakAll \[in\]：在资源脚本中的每一行设置断点。</span><span class="sxs-lookup"><span data-stu-id="268db-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="268db-108">返回值</span><span class="sxs-lookup"><span data-stu-id="268db-108">Return value</span></span>

<span data-ttu-id="268db-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="268db-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="268db-110">备注</span><span class="sxs-lookup"><span data-stu-id="268db-110">Remarks</span></span>

<span data-ttu-id="268db-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="268db-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="268db-112">要求</span><span class="sxs-lookup"><span data-stu-id="268db-112">Requirements</span></span>

<span data-ttu-id="268db-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="268db-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="268db-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="268db-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="268db-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="268db-115">See also</span></span>

[<span data-ttu-id="268db-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="268db-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)