---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 ResourceSet 方法"
ms.openlocfilehash: 7291641098578226449f8cbd360da0a3f9842598
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ca1e2-103">MSFT_DSCLocalConfigurationManager 类的 ResourceSet 方法</span><span class="sxs-lookup"><span data-stu-id="ca1e2-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ca1e2-104">直接调用 DSC 资源的 **Set** 方法。</span><span class="sxs-lookup"><span data-stu-id="ca1e2-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="ca1e2-105">语法</span><span class="sxs-lookup"><span data-stu-id="ca1e2-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="ca1e2-106">参数</span><span class="sxs-lookup"><span data-stu-id="ca1e2-106">Parameters</span></span>
----------

<span data-ttu-id="ca1e2-107">ResourceType \[in\]</span><span class="sxs-lookup"><span data-stu-id="ca1e2-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="ca1e2-108">要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="ca1e2-108">The name of the resource to call.</span></span>

<span data-ttu-id="ca1e2-109">ModuleName \[in\]</span><span class="sxs-lookup"><span data-stu-id="ca1e2-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="ca1e2-110">包含要调用的资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="ca1e2-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="ca1e2-111">resourceProperty \[in\]</span><span class="sxs-lookup"><span data-stu-id="ca1e2-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="ca1e2-112">分别在哈希表中将资源属性名称及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="ca1e2-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="ca1e2-113">使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="ca1e2-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="ca1e2-114">RebootRequired \[out\]</span><span class="sxs-lookup"><span data-stu-id="ca1e2-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="ca1e2-115">返回时，如果目标节点需要重启，会将此属性设置为 **true**。</span><span class="sxs-lookup"><span data-stu-id="ca1e2-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="ca1e2-116">返回值</span><span class="sxs-lookup"><span data-stu-id="ca1e2-116">Return value</span></span>
------------

<span data-ttu-id="ca1e2-117">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="ca1e2-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca1e2-118">备注</span><span class="sxs-lookup"><span data-stu-id="ca1e2-118">Remarks</span></span>

<span data-ttu-id="ca1e2-119">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="ca1e2-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ca1e2-120">要求</span><span class="sxs-lookup"><span data-stu-id="ca1e2-120">Requirements</span></span>
------------
><span data-ttu-id="ca1e2-121">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ca1e2-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ca1e2-122">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca1e2-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ca1e2-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca1e2-123">See also</span></span>


[<span data-ttu-id="ca1e2-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ca1e2-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



