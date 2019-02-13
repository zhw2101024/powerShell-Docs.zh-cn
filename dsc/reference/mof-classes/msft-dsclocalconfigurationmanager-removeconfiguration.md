---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676042"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9c25c-103">MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="9c25c-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9c25c-104">删除配置文件。</span><span class="sxs-lookup"><span data-stu-id="9c25c-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c25c-105">语法</span><span class="sxs-lookup"><span data-stu-id="9c25c-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="9c25c-106">参数</span><span class="sxs-lookup"><span data-stu-id="9c25c-106">Parameters</span></span>

<span data-ttu-id="9c25c-107">Stage \[in\]：指定要删除的配置文档。</span><span class="sxs-lookup"><span data-stu-id="9c25c-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="9c25c-108">下面的值是有效的：</span><span class="sxs-lookup"><span data-stu-id="9c25c-108">The following values are valid:</span></span>

|<span data-ttu-id="9c25c-109">值</span><span class="sxs-lookup"><span data-stu-id="9c25c-109">Value</span></span> |<span data-ttu-id="9c25c-110">说明</span><span class="sxs-lookup"><span data-stu-id="9c25c-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="9c25c-111">**1**</span><span class="sxs-lookup"><span data-stu-id="9c25c-111">**1**</span></span> | <span data-ttu-id="9c25c-112">**当前**配置文档 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="9c25c-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="9c25c-113">**2**</span><span class="sxs-lookup"><span data-stu-id="9c25c-113">**2**</span></span> | <span data-ttu-id="9c25c-114">**挂起的**配置文档 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="9c25c-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="9c25c-115">**4**</span><span class="sxs-lookup"><span data-stu-id="9c25c-115">**4**</span></span> | <span data-ttu-id="9c25c-116">**以前的**配置文档 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="9c25c-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="9c25c-117">Force \[in\]：若为 true，强制删除配置。</span><span class="sxs-lookup"><span data-stu-id="9c25c-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="9c25c-118">返回值</span><span class="sxs-lookup"><span data-stu-id="9c25c-118">Return value</span></span>

<span data-ttu-id="9c25c-119">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="9c25c-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c25c-120">备注</span><span class="sxs-lookup"><span data-stu-id="9c25c-120">Remarks</span></span>

<span data-ttu-id="9c25c-121">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="9c25c-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9c25c-122">要求</span><span class="sxs-lookup"><span data-stu-id="9c25c-122">Requirements</span></span>

<span data-ttu-id="9c25c-123">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9c25c-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9c25c-124">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9c25c-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9c25c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c25c-125">See also</span></span>

[<span data-ttu-id="9c25c-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9c25c-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)