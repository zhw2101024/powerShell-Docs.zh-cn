---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 ResourceGet 方法
ms.openlocfilehash: 3fd7ae54eb3ae782156dc4619ee0b6905dfb1212
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7a640-103">MSFT_DSCLocalConfigurationManager 类的 ResourceGet 方法</span><span class="sxs-lookup"><span data-stu-id="7a640-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7a640-104">直接调用 DSC 资源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="7a640-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="7a640-105">语法</span><span class="sxs-lookup"><span data-stu-id="7a640-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="7a640-106">参数</span><span class="sxs-lookup"><span data-stu-id="7a640-106">Parameters</span></span>
----------

<span data-ttu-id="7a640-107">ResourceType \[in\]：要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="7a640-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="7a640-108">ModuleName \[in\]：包含要调用资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="7a640-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="7a640-109">resourceProperty \[in\]：在哈希表中分别将资源属性名及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="7a640-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="7a640-110">使用 [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="7a640-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="7a640-111">configurations \[out\]：在返回时包含配置的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="7a640-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a640-112">返回值</span><span class="sxs-lookup"><span data-stu-id="7a640-112">Return value</span></span>
------------

<span data-ttu-id="7a640-113">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="7a640-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a640-114">备注</span><span class="sxs-lookup"><span data-stu-id="7a640-114">Remarks</span></span>

<span data-ttu-id="7a640-115">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="7a640-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a640-116">要求</span><span class="sxs-lookup"><span data-stu-id="7a640-116">Requirements</span></span>
------------
><span data-ttu-id="7a640-117">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7a640-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7a640-118">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7a640-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7a640-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a640-119">See also</span></span>


[<span data-ttu-id="7a640-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7a640-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)