---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法"
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fc7d4-103">MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法</span><span class="sxs-lookup"><span data-stu-id="fc7d4-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fc7d4-104">直接调用 DSC 资源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="fc7d4-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="fc7d4-105">语法</span><span class="sxs-lookup"><span data-stu-id="fc7d4-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="fc7d4-106">参数</span><span class="sxs-lookup"><span data-stu-id="fc7d4-106">Parameters</span></span>
----------

<span data-ttu-id="fc7d4-107">ResourceType \[in\]</span><span class="sxs-lookup"><span data-stu-id="fc7d4-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="fc7d4-108">要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="fc7d4-108">The name of the resource to call.</span></span>

<span data-ttu-id="fc7d4-109">ModuleName \[in\]</span><span class="sxs-lookup"><span data-stu-id="fc7d4-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="fc7d4-110">包含要调用的资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="fc7d4-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="fc7d4-111">resourceProperty \[in\]</span><span class="sxs-lookup"><span data-stu-id="fc7d4-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="fc7d4-112">分别在哈希表中将资源属性名称及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="fc7d4-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="fc7d4-113">使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="fc7d4-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="fc7d4-114">InDesiredState \[out\]</span><span class="sxs-lookup"><span data-stu-id="fc7d4-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="fc7d4-115">返回时，如果目标节点处于所需状态，会将此属性设置为 **true**。</span><span class="sxs-lookup"><span data-stu-id="fc7d4-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="fc7d4-116">返回值</span><span class="sxs-lookup"><span data-stu-id="fc7d4-116">Return value</span></span>
------------

<span data-ttu-id="fc7d4-117">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="fc7d4-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc7d4-118">备注</span><span class="sxs-lookup"><span data-stu-id="fc7d4-118">Remarks</span></span>

<span data-ttu-id="fc7d4-119">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="fc7d4-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc7d4-120">要求</span><span class="sxs-lookup"><span data-stu-id="fc7d4-120">Requirements</span></span>
------------
><span data-ttu-id="fc7d4-121">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fc7d4-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fc7d4-122">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc7d4-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fc7d4-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc7d4-123">See also</span></span>


[<span data-ttu-id="fc7d4-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fc7d4-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



