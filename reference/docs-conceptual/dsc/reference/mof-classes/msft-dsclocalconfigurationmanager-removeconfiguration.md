---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: RemoveConfiguration 方法
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953394"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="b6a10-103">RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="b6a10-103">RemoveConfiguration method</span></span>

<span data-ttu-id="b6a10-104">删除配置文件。</span><span class="sxs-lookup"><span data-stu-id="b6a10-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6a10-105">语法</span><span class="sxs-lookup"><span data-stu-id="b6a10-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="b6a10-106">参数</span><span class="sxs-lookup"><span data-stu-id="b6a10-106">Parameters</span></span>

<span data-ttu-id="b6a10-107">Stage  \[in\]：指定要删除的配置文档。</span><span class="sxs-lookup"><span data-stu-id="b6a10-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="b6a10-108">下面的值是有效的：</span><span class="sxs-lookup"><span data-stu-id="b6a10-108">The following values are valid:</span></span>

|<span data-ttu-id="b6a10-109">值</span><span class="sxs-lookup"><span data-stu-id="b6a10-109">Value</span></span> |<span data-ttu-id="b6a10-110">说明</span><span class="sxs-lookup"><span data-stu-id="b6a10-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="b6a10-111">**1**</span><span class="sxs-lookup"><span data-stu-id="b6a10-111">**1**</span></span> | <span data-ttu-id="b6a10-112">**当前**配置文档 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="b6a10-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="b6a10-113">**2**</span><span class="sxs-lookup"><span data-stu-id="b6a10-113">**2**</span></span> | <span data-ttu-id="b6a10-114">**挂起的**配置文档 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="b6a10-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="b6a10-115">**4**</span><span class="sxs-lookup"><span data-stu-id="b6a10-115">**4**</span></span> | <span data-ttu-id="b6a10-116">**以前的**配置文档 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="b6a10-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="b6a10-117">Force  \[in\]：若为 true  ，强制删除配置。</span><span class="sxs-lookup"><span data-stu-id="b6a10-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b6a10-118">返回值</span><span class="sxs-lookup"><span data-stu-id="b6a10-118">Return value</span></span>

<span data-ttu-id="b6a10-119">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="b6a10-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6a10-120">备注</span><span class="sxs-lookup"><span data-stu-id="b6a10-120">Remarks</span></span>

<span data-ttu-id="b6a10-121">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="b6a10-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6a10-122">要求</span><span class="sxs-lookup"><span data-stu-id="b6a10-122">Requirements</span></span>

<span data-ttu-id="b6a10-123">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b6a10-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b6a10-124">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6a10-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b6a10-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6a10-125">See also</span></span>

[<span data-ttu-id="b6a10-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b6a10-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
