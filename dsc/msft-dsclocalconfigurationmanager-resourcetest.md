---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法"
ms.openlocfilehash: 73d7d543505a3768a0660084345d3858e055514f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0c918-103">MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法</span><span class="sxs-lookup"><span data-stu-id="0c918-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0c918-104">直接调用 DSC 资源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="0c918-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="0c918-105">语法</span><span class="sxs-lookup"><span data-stu-id="0c918-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="0c918-106">参数</span><span class="sxs-lookup"><span data-stu-id="0c918-106">Parameters</span></span>
----------

<span data-ttu-id="0c918-107">ResourceType \[in\]</span><span class="sxs-lookup"><span data-stu-id="0c918-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="0c918-108">要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="0c918-108">The name of the resource to call.</span></span>

<span data-ttu-id="0c918-109">ModuleName \[in\]</span><span class="sxs-lookup"><span data-stu-id="0c918-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="0c918-110">包含要调用的资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="0c918-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="0c918-111">resourceProperty \[in\]</span><span class="sxs-lookup"><span data-stu-id="0c918-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="0c918-112">分别在哈希表中将资源属性名称及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="0c918-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="0c918-113">使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="0c918-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="0c918-114">InDesiredState \[out\]</span><span class="sxs-lookup"><span data-stu-id="0c918-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="0c918-115">返回时，如果目标节点处于所需状态，会将此属性设置为 **true**。</span><span class="sxs-lookup"><span data-stu-id="0c918-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="0c918-116">返回值</span><span class="sxs-lookup"><span data-stu-id="0c918-116">Return value</span></span>
------------

<span data-ttu-id="0c918-117">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="0c918-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c918-118">备注</span><span class="sxs-lookup"><span data-stu-id="0c918-118">Remarks</span></span>

<span data-ttu-id="0c918-119">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="0c918-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c918-120">要求</span><span class="sxs-lookup"><span data-stu-id="0c918-120">Requirements</span></span>
------------
><span data-ttu-id="0c918-121">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0c918-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0c918-122">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0c918-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0c918-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c918-123">See also</span></span>


[<span data-ttu-id="0c918-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0c918-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



