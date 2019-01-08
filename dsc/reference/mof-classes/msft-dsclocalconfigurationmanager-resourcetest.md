---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047173"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fb7a7-103">MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法</span><span class="sxs-lookup"><span data-stu-id="fb7a7-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fb7a7-104">直接调用 DSC 资源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="fb7a7-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb7a7-105">语法</span><span class="sxs-lookup"><span data-stu-id="fb7a7-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="fb7a7-106">参数</span><span class="sxs-lookup"><span data-stu-id="fb7a7-106">Parameters</span></span>

<span data-ttu-id="fb7a7-107">ResourceType \[in\]：要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="fb7a7-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="fb7a7-108">ModuleName \[in\]：包含要调用资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="fb7a7-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="fb7a7-109">resourceProperty \[in\]：在哈希表中分别将资源属性名及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="fb7a7-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="fb7a7-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="fb7a7-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="fb7a7-111">InDesiredState \[out\]：返回响应时，如果目标节点处于所需状态，便会将此属性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="fb7a7-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="fb7a7-112">返回值</span><span class="sxs-lookup"><span data-stu-id="fb7a7-112">Return value</span></span>

<span data-ttu-id="fb7a7-113">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="fb7a7-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb7a7-114">备注</span><span class="sxs-lookup"><span data-stu-id="fb7a7-114">Remarks</span></span>

<span data-ttu-id="fb7a7-115">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="fb7a7-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb7a7-116">要求</span><span class="sxs-lookup"><span data-stu-id="fb7a7-116">Requirements</span></span>

<span data-ttu-id="fb7a7-117">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fb7a7-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fb7a7-118">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb7a7-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fb7a7-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb7a7-119">See also</span></span>

[<span data-ttu-id="fb7a7-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fb7a7-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)