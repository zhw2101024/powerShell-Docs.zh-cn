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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983892"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="b5388-102">ValidateCount 属性声明</span><span class="sxs-lookup"><span data-stu-id="b5388-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="b5388-103">ValidateCount 属性指定参数允许 cmdlet 参数的最小值和最大数目。</span><span class="sxs-lookup"><span data-stu-id="b5388-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5388-104">语法</span><span class="sxs-lookup"><span data-stu-id="b5388-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="b5388-105">参数</span><span class="sxs-lookup"><span data-stu-id="b5388-105">Parameters</span></span>

<span data-ttu-id="b5388-106">`MinLength` ([System.Int32][]) 所需。</span><span class="sxs-lookup"><span data-stu-id="b5388-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="b5388-107">指定参数的最小的数目。</span><span class="sxs-lookup"><span data-stu-id="b5388-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="b5388-108">`MaxLength`([System.Int32][]) 所需。</span><span class="sxs-lookup"><span data-stu-id="b5388-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="b5388-109">指定参数的最大的数目。</span><span class="sxs-lookup"><span data-stu-id="b5388-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5388-110">备注</span><span class="sxs-lookup"><span data-stu-id="b5388-110">Remarks</span></span>

- <span data-ttu-id="b5388-111">有关如何声明此属性的详细信息，请参阅[如何进行验证的参数计数][]。</span><span class="sxs-lookup"><span data-stu-id="b5388-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="b5388-112">不调用此属性时，相应的 cmdlet 参数可以具有任意数量的参数。</span><span class="sxs-lookup"><span data-stu-id="b5388-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="b5388-113">Windows PowerShell 运行时将引发错误在以下情况下：</span><span class="sxs-lookup"><span data-stu-id="b5388-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="b5388-114">`MinLength`并`MaxLength`特性参数的类型不是[System.Int32][]。</span><span class="sxs-lookup"><span data-stu-id="b5388-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="b5388-115">值`MaxLength`特性参数是否小于的值`MinLength`特性参数。</span><span class="sxs-lookup"><span data-stu-id="b5388-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="b5388-116">通过定义 ValidateCount 特性[System.Management.Automation.ValidateCountAttribute][]类。</span><span class="sxs-lookup"><span data-stu-id="b5388-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5388-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5388-117">See Also</span></span>

<span data-ttu-id="b5388-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="b5388-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="b5388-119">[如何进行验证的参数计数][]</span><span class="sxs-lookup"><span data-stu-id="b5388-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="b5388-120">[编写 Windows PowerShell Cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="b5388-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[如何进行验证的参数计数]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[编写 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
