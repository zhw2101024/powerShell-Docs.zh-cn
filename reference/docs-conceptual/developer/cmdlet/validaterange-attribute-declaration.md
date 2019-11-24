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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369126"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="933b8-102">ValidateRange 属性声明</span><span class="sxs-lookup"><span data-stu-id="933b8-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="933b8-103">ValidateRange 属性指定 cmdlet 参数参数的最小值和最大值（范围）。</span><span class="sxs-lookup"><span data-stu-id="933b8-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="933b8-104">此属性也可由 Windows PowerShell 函数使用。</span><span class="sxs-lookup"><span data-stu-id="933b8-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="933b8-105">语法</span><span class="sxs-lookup"><span data-stu-id="933b8-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="933b8-106">参数</span><span class="sxs-lookup"><span data-stu-id="933b8-106">Parameters</span></span>

<span data-ttu-id="933b8-107">需要 `MinRange`[（system.string）。](/dotnet/api/system.object)</span><span class="sxs-lookup"><span data-stu-id="933b8-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="933b8-108">指定允许的最小值。</span><span class="sxs-lookup"><span data-stu-id="933b8-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="933b8-109">需要 `MaxRange`[（system.string）。](/dotnet/api/system.object)</span><span class="sxs-lookup"><span data-stu-id="933b8-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="933b8-110">指定允许的最大值。</span><span class="sxs-lookup"><span data-stu-id="933b8-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="933b8-111">备注</span><span class="sxs-lookup"><span data-stu-id="933b8-111">Remarks</span></span>

- <span data-ttu-id="933b8-112">当 `MinRange` 参数的值大于 `MaxRange` 参数的值时，Windows PowerShell 运行时将引发构造错误。</span><span class="sxs-lookup"><span data-stu-id="933b8-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="933b8-113">Windows PowerShell 运行时在以下条件下引发验证错误：</span><span class="sxs-lookup"><span data-stu-id="933b8-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="933b8-114">当参数的值小于 `MinRange` 限制或大于 `MaxRange` 限制时。</span><span class="sxs-lookup"><span data-stu-id="933b8-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="933b8-115">当参数与 `MinRange` 和 `MaxRange` 参数的类型不同时。</span><span class="sxs-lookup"><span data-stu-id="933b8-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="933b8-116">ValidateRange 特性是由[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)类定义的。</span><span class="sxs-lookup"><span data-stu-id="933b8-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="933b8-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="933b8-117">See Also</span></span>

[<span data-ttu-id="933b8-118">System.web. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="933b8-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="933b8-119">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="933b8-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
