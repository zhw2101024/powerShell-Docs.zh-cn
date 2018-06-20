---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法
ms.openlocfilehash: 714bbb286ebbe4ed0f1faa15e03ac4b51a3ee87f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218852"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d7045-103">MSFT_DSCLocalConfigurationManager 类的 ResourceTest 方法</span><span class="sxs-lookup"><span data-stu-id="d7045-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d7045-104">直接调用 DSC 资源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="d7045-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="d7045-105">语法</span><span class="sxs-lookup"><span data-stu-id="d7045-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="d7045-106">参数</span><span class="sxs-lookup"><span data-stu-id="d7045-106">Parameters</span></span>
----------

<span data-ttu-id="d7045-107">ResourceType \[in\]：要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="d7045-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="d7045-108">ModuleName \[in\]：包含要调用资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="d7045-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="d7045-109">resourceProperty \[in\]：在哈希表中分别将资源属性名及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="d7045-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="d7045-110">使用 [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="d7045-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="d7045-111">InDesiredState \[out\]：返回响应时，如果目标节点处于所需状态，便会将此属性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="d7045-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="d7045-112">返回值</span><span class="sxs-lookup"><span data-stu-id="d7045-112">Return value</span></span>
------------

<span data-ttu-id="d7045-113">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="d7045-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7045-114">备注</span><span class="sxs-lookup"><span data-stu-id="d7045-114">Remarks</span></span>

<span data-ttu-id="d7045-115">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="d7045-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7045-116">要求</span><span class="sxs-lookup"><span data-stu-id="d7045-116">Requirements</span></span>
------------
><span data-ttu-id="d7045-117">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d7045-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d7045-118">**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7045-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d7045-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7045-119">See also</span></span>


[<span data-ttu-id="d7045-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d7045-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)