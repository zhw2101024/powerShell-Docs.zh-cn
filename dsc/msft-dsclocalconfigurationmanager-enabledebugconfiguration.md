---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法"
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="31332-103">MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="31332-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="31332-104">启用 DSC 资源调试。</span><span class="sxs-lookup"><span data-stu-id="31332-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="31332-105">语法</span><span class="sxs-lookup"><span data-stu-id="31332-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="31332-106">参数</span><span class="sxs-lookup"><span data-stu-id="31332-106">Parameters</span></span>
----------

<span data-ttu-id="31332-107">BreakAll \[in\]</span><span class="sxs-lookup"><span data-stu-id="31332-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="31332-108">在资源脚本中的每一行设置断点。</span><span class="sxs-lookup"><span data-stu-id="31332-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="31332-109">返回值</span><span class="sxs-lookup"><span data-stu-id="31332-109">Return value</span></span>
------------

<span data-ttu-id="31332-110">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="31332-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="31332-111">备注</span><span class="sxs-lookup"><span data-stu-id="31332-111">Remarks</span></span>

<span data-ttu-id="31332-112">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="31332-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="31332-113">要求</span><span class="sxs-lookup"><span data-stu-id="31332-113">Requirements</span></span>
------------
><span data-ttu-id="31332-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="31332-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="31332-115">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="31332-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="31332-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31332-116">See also</span></span>


[<span data-ttu-id="31332-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="31332-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



