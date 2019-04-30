---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 ResourceSet 方法
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078395"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="51c21-103">MSFT_DSCLocalConfigurationManager 类的 ResourceSet 方法</span><span class="sxs-lookup"><span data-stu-id="51c21-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="51c21-104">直接调用 DSC 资源的 **Set** 方法。</span><span class="sxs-lookup"><span data-stu-id="51c21-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="51c21-105">语法</span><span class="sxs-lookup"><span data-stu-id="51c21-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="51c21-106">参数</span><span class="sxs-lookup"><span data-stu-id="51c21-106">Parameters</span></span>

<span data-ttu-id="51c21-107">ResourceType \[in\]：要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="51c21-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="51c21-108">ModuleName \[in\]：包含要调用资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="51c21-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="51c21-109">resourceProperty \[in\]：在哈希表中分别将资源属性名及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="51c21-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="51c21-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="51c21-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="51c21-111">RebootRequired \[out\]：返回响应时，如果目标节点需要重启，便会将此属性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="51c21-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="51c21-112">返回值</span><span class="sxs-lookup"><span data-stu-id="51c21-112">Return value</span></span>

<span data-ttu-id="51c21-113">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="51c21-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="51c21-114">备注</span><span class="sxs-lookup"><span data-stu-id="51c21-114">Remarks</span></span>

<span data-ttu-id="51c21-115">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="51c21-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="51c21-116">要求</span><span class="sxs-lookup"><span data-stu-id="51c21-116">Requirements</span></span>

<span data-ttu-id="51c21-117">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="51c21-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="51c21-118">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="51c21-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="51c21-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51c21-119">See also</span></span>

[<span data-ttu-id="51c21-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="51c21-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)