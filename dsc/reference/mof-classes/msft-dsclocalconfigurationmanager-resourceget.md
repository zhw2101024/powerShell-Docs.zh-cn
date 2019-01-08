---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类的 ResourceGet 方法
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047063"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0ee2f-103">MSFT_DSCLocalConfigurationManager 类的 ResourceGet 方法</span><span class="sxs-lookup"><span data-stu-id="0ee2f-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0ee2f-104">直接调用 DSC 资源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="0ee2f-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ee2f-105">语法</span><span class="sxs-lookup"><span data-stu-id="0ee2f-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="0ee2f-106">参数</span><span class="sxs-lookup"><span data-stu-id="0ee2f-106">Parameters</span></span>

<span data-ttu-id="0ee2f-107">ResourceType \[in\]：要调用的资源的名称。</span><span class="sxs-lookup"><span data-stu-id="0ee2f-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="0ee2f-108">ModuleName \[in\]：包含要调用资源的模块名称。</span><span class="sxs-lookup"><span data-stu-id="0ee2f-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="0ee2f-109">resourceProperty \[in\]：在哈希表中分别将资源属性名及其值指定为键和值。</span><span class="sxs-lookup"><span data-stu-id="0ee2f-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="0ee2f-110">使用 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 可以发现资源属性及其类型。</span><span class="sxs-lookup"><span data-stu-id="0ee2f-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="0ee2f-111">configurations \[out\]：返回响应时，包含配置的嵌入实例。</span><span class="sxs-lookup"><span data-stu-id="0ee2f-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0ee2f-112">返回值</span><span class="sxs-lookup"><span data-stu-id="0ee2f-112">Return value</span></span>

<span data-ttu-id="0ee2f-113">如果成功，则返回零；否则返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="0ee2f-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ee2f-114">备注</span><span class="sxs-lookup"><span data-stu-id="0ee2f-114">Remarks</span></span>

<span data-ttu-id="0ee2f-115">这是一种静态方法。</span><span class="sxs-lookup"><span data-stu-id="0ee2f-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0ee2f-116">要求</span><span class="sxs-lookup"><span data-stu-id="0ee2f-116">Requirements</span></span>

<span data-ttu-id="0ee2f-117">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0ee2f-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0ee2f-118">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0ee2f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0ee2f-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ee2f-119">See also</span></span>

[<span data-ttu-id="0ee2f-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0ee2f-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)