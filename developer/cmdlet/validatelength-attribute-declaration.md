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
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855159"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="6a84f-102">ValidateLength 属性声明</span><span class="sxs-lookup"><span data-stu-id="6a84f-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="6a84f-103">ValidateLength 属性指定的最小值和最大字符数为 cmdlet 参数自变量。</span><span class="sxs-lookup"><span data-stu-id="6a84f-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="6a84f-104">Windows PowerShell 函数还可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="6a84f-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a84f-105">语法</span><span class="sxs-lookup"><span data-stu-id="6a84f-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="6a84f-106">参数</span><span class="sxs-lookup"><span data-stu-id="6a84f-106">Parameters</span></span>

<span data-ttu-id="6a84f-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) 所需。</span><span class="sxs-lookup"><span data-stu-id="6a84f-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="6a84f-108">指定的最小允许的字符数。</span><span class="sxs-lookup"><span data-stu-id="6a84f-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="6a84f-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) 所需。</span><span class="sxs-lookup"><span data-stu-id="6a84f-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="6a84f-110">指定最大允许的字符。</span><span class="sxs-lookup"><span data-stu-id="6a84f-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a84f-111">备注</span><span class="sxs-lookup"><span data-stu-id="6a84f-111">Remarks</span></span>

- <span data-ttu-id="6a84f-112">有关如何声明此属性的详细信息，请参阅[如何声明输入验证规则](./how-to-validate-parameter-input.md)。</span><span class="sxs-lookup"><span data-stu-id="6a84f-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="6a84f-113">如果不使用此特性，相应参数自变量可以是任意长度。</span><span class="sxs-lookup"><span data-stu-id="6a84f-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="6a84f-114">Windows PowerShell 运行时将引发错误在以下情况下：</span><span class="sxs-lookup"><span data-stu-id="6a84f-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="6a84f-115">时的值`MaxLength`特性参数是否小于的值`MinLength`特性参数。</span><span class="sxs-lookup"><span data-stu-id="6a84f-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="6a84f-116">当`MaxLength`属性参数设置为 0。</span><span class="sxs-lookup"><span data-stu-id="6a84f-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="6a84f-117">当参数不是字符串。</span><span class="sxs-lookup"><span data-stu-id="6a84f-117">When the argument is not a string.</span></span>

- <span data-ttu-id="6a84f-118">通过定义 ValidateLength 特性[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="6a84f-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a84f-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a84f-119">See Also</span></span>

[<span data-ttu-id="6a84f-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="6a84f-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="6a84f-121">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6a84f-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
