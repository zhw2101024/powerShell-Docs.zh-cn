---
title: ValidateRange 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857033"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="0a19b-102">ValidateRange 属性声明</span><span class="sxs-lookup"><span data-stu-id="0a19b-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="0a19b-103">ValidateRange 属性指定的最小值和最大值 （范围） 的 cmdlet 参数自变量。</span><span class="sxs-lookup"><span data-stu-id="0a19b-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="0a19b-104">Windows PowerShell 函数还可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="0a19b-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a19b-105">语法</span><span class="sxs-lookup"><span data-stu-id="0a19b-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="0a19b-106">参数</span><span class="sxs-lookup"><span data-stu-id="0a19b-106">Parameters</span></span>

<span data-ttu-id="0a19b-107">`MinRange` ([System.Object](/dotnet/api/system.object)) 所需。</span><span class="sxs-lookup"><span data-stu-id="0a19b-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="0a19b-108">指定允许的最小值。</span><span class="sxs-lookup"><span data-stu-id="0a19b-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="0a19b-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) 所需。</span><span class="sxs-lookup"><span data-stu-id="0a19b-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="0a19b-110">指定允许的最大值。</span><span class="sxs-lookup"><span data-stu-id="0a19b-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a19b-111">备注</span><span class="sxs-lookup"><span data-stu-id="0a19b-111">Remarks</span></span>

- <span data-ttu-id="0a19b-112">Windows PowerShell 运行时将引发构造错误时的值`MinRange`参数是否大于的值`MaxRange`参数。</span><span class="sxs-lookup"><span data-stu-id="0a19b-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="0a19b-113">Windows PowerShell 运行时将引发验证错误在以下情况下：</span><span class="sxs-lookup"><span data-stu-id="0a19b-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="0a19b-114">当自变量的值是小于`MinRange`限制或大于`MaxRange`限制。</span><span class="sxs-lookup"><span data-stu-id="0a19b-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="0a19b-115">当参数不是相同的类型`MinRange`和`MaxRange`参数。</span><span class="sxs-lookup"><span data-stu-id="0a19b-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="0a19b-116">通过定义 ValidateRange 特性[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="0a19b-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a19b-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a19b-117">See Also</span></span>

[<span data-ttu-id="0a19b-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="0a19b-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="0a19b-119">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0a19b-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
