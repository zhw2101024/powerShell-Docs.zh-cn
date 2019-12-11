---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: ResourceTest 方法
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954944"
---
# <a name="resourcetest-method"></a><span data-ttu-id="e5c2f-103">ResourceTest 方法</span><span class="sxs-lookup"><span data-stu-id="e5c2f-103">ResourceTest method</span></span>

<span data-ttu-id="e5c2f-104">直接调用 DSC 资源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="e5c2f-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5c2f-105">语法</span><span class="sxs-lookup"><span data-stu-id="e5c2f-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="e5c2f-106">参数</span><span class="sxs-lookup"><span data-stu-id="e5c2f-106">Parameters</span></span>

<span data-ttu-id="e5c2f-107">ResourceType  \[in\]：要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="e5c2f-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="e5c2f-108">ModuleName  \[in\]：包含要调用资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="e5c2f-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="e5c2f-109">resourceProperty  \[in\]：在哈希表中分别将资源属性名及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="e5c2f-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="e5c2f-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="e5c2f-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="e5c2f-111">InDesiredState  \[out\]：返回响应时，如果目标节点处于所需状态，便会将此属性设置为 true  。</span><span class="sxs-lookup"><span data-stu-id="e5c2f-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="e5c2f-112">返回值</span><span class="sxs-lookup"><span data-stu-id="e5c2f-112">Return value</span></span>

<span data-ttu-id="e5c2f-113">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="e5c2f-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5c2f-114">备注</span><span class="sxs-lookup"><span data-stu-id="e5c2f-114">Remarks</span></span>

<span data-ttu-id="e5c2f-115">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="e5c2f-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5c2f-116">要求</span><span class="sxs-lookup"><span data-stu-id="e5c2f-116">Requirements</span></span>

<span data-ttu-id="e5c2f-117">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e5c2f-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e5c2f-118">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5c2f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e5c2f-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5c2f-119">See also</span></span>

[<span data-ttu-id="e5c2f-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e5c2f-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
