---
title: ValidateLength 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067155"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="e2cb5-102">ValidateLength 属性声明</span><span class="sxs-lookup"><span data-stu-id="e2cb5-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="e2cb5-103">ValidateLength 属性指定的最小值和最大字符数为 cmdlet 参数自变量。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="e2cb5-104">Windows PowerShell 函数还可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2cb5-105">语法</span><span class="sxs-lookup"><span data-stu-id="e2cb5-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="e2cb5-106">参数</span><span class="sxs-lookup"><span data-stu-id="e2cb5-106">Parameters</span></span>

<span data-ttu-id="e2cb5-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) 所需。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="e2cb5-108">指定的最小允许的字符数。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="e2cb5-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) 所需。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="e2cb5-110">指定最大允许的字符。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2cb5-111">备注</span><span class="sxs-lookup"><span data-stu-id="e2cb5-111">Remarks</span></span>

- <span data-ttu-id="e2cb5-112">有关如何声明此属性的详细信息，请参阅[如何声明输入验证规则](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="e2cb5-113">如果不使用此特性，相应参数自变量可以是任意长度。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="e2cb5-114">Windows PowerShell 运行时将引发错误在以下情况下：</span><span class="sxs-lookup"><span data-stu-id="e2cb5-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="e2cb5-115">时的值`MaxLength`特性参数是否小于的值`MinLength`特性参数。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="e2cb5-116">当`MaxLength`属性参数设置为 0。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="e2cb5-117">当参数不是字符串。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-117">When the argument is not a string.</span></span>

- <span data-ttu-id="e2cb5-118">通过定义 ValidateLength 特性[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="e2cb5-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2cb5-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2cb5-119">See Also</span></span>

[<span data-ttu-id="e2cb5-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="e2cb5-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="e2cb5-121">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e2cb5-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
