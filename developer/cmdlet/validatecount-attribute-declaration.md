---
title: ValidateCount 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794428"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="2719b-102">ValidateCount 属性声明</span><span class="sxs-lookup"><span data-stu-id="2719b-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="2719b-103">ValidateCount 属性指定参数允许 cmdlet 参数的最小值和最大数目。</span><span class="sxs-lookup"><span data-stu-id="2719b-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="2719b-104">语法</span><span class="sxs-lookup"><span data-stu-id="2719b-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="2719b-105">参数</span><span class="sxs-lookup"><span data-stu-id="2719b-105">Parameters</span></span>

<span data-ttu-id="2719b-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) 所需。</span><span class="sxs-lookup"><span data-stu-id="2719b-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="2719b-107">指定参数的最小的数目。</span><span class="sxs-lookup"><span data-stu-id="2719b-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="2719b-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) 所需。</span><span class="sxs-lookup"><span data-stu-id="2719b-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="2719b-109">指定参数的最大的数目。</span><span class="sxs-lookup"><span data-stu-id="2719b-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="2719b-110">备注</span><span class="sxs-lookup"><span data-stu-id="2719b-110">Remarks</span></span>

- <span data-ttu-id="2719b-111">有关如何声明此属性的详细信息，请参阅[如何声明输入验证规则](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。</span><span class="sxs-lookup"><span data-stu-id="2719b-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="2719b-112">不调用此属性时，相应的 cmdlet 参数可以具有任意数量的参数。</span><span class="sxs-lookup"><span data-stu-id="2719b-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="2719b-113">Windows PowerShell 运行时将引发错误在以下情况下：</span><span class="sxs-lookup"><span data-stu-id="2719b-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="2719b-114">`MinLength`并`MaxLength`特性参数的类型不是[System.Int32](/dotnet/api/System.Int32)。</span><span class="sxs-lookup"><span data-stu-id="2719b-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="2719b-115">值`MaxLength`特性参数是否小于的值`MinLength`特性参数。</span><span class="sxs-lookup"><span data-stu-id="2719b-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="2719b-116">通过定义 ValidateCount 特性[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)类。</span><span class="sxs-lookup"><span data-stu-id="2719b-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2719b-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2719b-117">See Also</span></span>

[<span data-ttu-id="2719b-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="2719b-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="2719b-119">如何声明输入的验证规则</span><span class="sxs-lookup"><span data-stu-id="2719b-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="2719b-120">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2719b-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
