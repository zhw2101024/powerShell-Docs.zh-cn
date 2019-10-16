---
title: 正在验证参数输入 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363506"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="198e7-102">验证参数输入</span><span class="sxs-lookup"><span data-stu-id="198e7-102">Validating Parameter Input</span></span>

<span data-ttu-id="198e7-103">PowerShell 可以通过多种方式验证传递到 cmdlet 参数的参数。</span><span class="sxs-lookup"><span data-stu-id="198e7-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="198e7-104">PowerShell 可以验证参数的字符的长度、范围和模式。</span><span class="sxs-lookup"><span data-stu-id="198e7-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="198e7-105">它可以验证可用参数的数目（计数）。</span><span class="sxs-lookup"><span data-stu-id="198e7-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="198e7-106">这些验证规则由使用 cmdlet 类的公共属性上的 Parameter 特性声明的验证特性定义。</span><span class="sxs-lookup"><span data-stu-id="198e7-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="198e7-107">若要验证参数参数，PowerShell 运行时使用验证特性提供的信息来确认在运行 cmdlet 之前参数的值。</span><span class="sxs-lookup"><span data-stu-id="198e7-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="198e7-108">如果参数输入无效，则用户将收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="198e7-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="198e7-109">每个验证参数都定义一个由 PowerShell 强制执行的验证规则。</span><span class="sxs-lookup"><span data-stu-id="198e7-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="198e7-110">PowerShell 根据以下属性强制执行验证规则。</span><span class="sxs-lookup"><span data-stu-id="198e7-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="198e7-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="198e7-111">ValidateCount</span></span>

<span data-ttu-id="198e7-112">指定参数可以接受的最小和最大参数数目。</span><span class="sxs-lookup"><span data-stu-id="198e7-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="198e7-113">有关详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="198e7-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="198e7-114">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="198e7-114">ValidateLength</span></span>

<span data-ttu-id="198e7-115">指定参数参数中的最小和最大字符数。</span><span class="sxs-lookup"><span data-stu-id="198e7-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="198e7-116">有关详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="198e7-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="198e7-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="198e7-117">ValidatePattern</span></span>

<span data-ttu-id="198e7-118">指定用于验证参数参数的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="198e7-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="198e7-119">有关详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="198e7-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="198e7-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="198e7-120">ValidateRange</span></span>

<span data-ttu-id="198e7-121">指定参数参数的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="198e7-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="198e7-122">有关详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="198e7-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="198e7-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="198e7-123">ValidateSet</span></span>

<span data-ttu-id="198e7-124">指定参数参数的有效值。</span><span class="sxs-lookup"><span data-stu-id="198e7-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="198e7-125">有关详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="198e7-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="198e7-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="198e7-126">See Also</span></span>

[<span data-ttu-id="198e7-127">如何验证参数输入</span><span class="sxs-lookup"><span data-stu-id="198e7-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="198e7-128">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="198e7-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
