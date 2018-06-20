---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218189"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ecad7-103">MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="ecad7-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ecad7-104">启用 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="ecad7-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="ecad7-105">语法</span><span class="sxs-lookup"><span data-stu-id="ecad7-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="ecad7-106">参数</span><span class="sxs-lookup"><span data-stu-id="ecad7-106">Parameters</span></span>
----------

<span data-ttu-id="ecad7-107">BreakAll \[in\]：在资源脚本中的每一行设置断点。</span><span class="sxs-lookup"><span data-stu-id="ecad7-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="ecad7-108">返回值</span><span class="sxs-lookup"><span data-stu-id="ecad7-108">Return value</span></span>
------------

<span data-ttu-id="ecad7-109">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="ecad7-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ecad7-110">备注</span><span class="sxs-lookup"><span data-stu-id="ecad7-110">Remarks</span></span>

<span data-ttu-id="ecad7-111">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="ecad7-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ecad7-112">要求</span><span class="sxs-lookup"><span data-stu-id="ecad7-112">Requirements</span></span>
------------
><span data-ttu-id="ecad7-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ecad7-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ecad7-114">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ecad7-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ecad7-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ecad7-115">See also</span></span>


[<span data-ttu-id="ecad7-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ecad7-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)