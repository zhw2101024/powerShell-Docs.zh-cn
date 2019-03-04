---
title: 验证参数输入 |Microsoft Docs
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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858843"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="2d76f-102">验证参数输入</span><span class="sxs-lookup"><span data-stu-id="2d76f-102">Validating Parameter Input</span></span>

<span data-ttu-id="2d76f-103">Windows PowerShell 可以验证传递给以下几种方式的 cmdlet 参数的参数。</span><span class="sxs-lookup"><span data-stu-id="2d76f-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="2d76f-104">Windows PowerShell 可以验证长度、 范围和自变量的字符模式。</span><span class="sxs-lookup"><span data-stu-id="2d76f-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="2d76f-105">它可以验证的参数可用 （计数） 的数目。</span><span class="sxs-lookup"><span data-stu-id="2d76f-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="2d76f-106">通过在 cmdlet 类的公共属性的参数属性与声明的验证特性定义这些验证规则。</span><span class="sxs-lookup"><span data-stu-id="2d76f-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="2d76f-107">若要验证参数自变量，Windows PowerShell 运行时使用的验证特性提供的信息确认之前运行该 cmdlet 的参数的值。</span><span class="sxs-lookup"><span data-stu-id="2d76f-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="2d76f-108">如果该参数输入不是有效的用户会收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="2d76f-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="2d76f-109">每个验证参数定义由 Windows PowerShell 强制执行的验证规则。</span><span class="sxs-lookup"><span data-stu-id="2d76f-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="2d76f-110">Windows PowerShell 强制执行基于以下属性的验证规则。</span><span class="sxs-lookup"><span data-stu-id="2d76f-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="2d76f-111">ValidateCount 指定最小值和最大数量的参数可接受的参数。</span><span class="sxs-lookup"><span data-stu-id="2d76f-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="2d76f-112">有关用于声明此属性的语法的详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2d76f-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="2d76f-113">ValidateLength 参数自变量中指定的最小值和最大字符数。</span><span class="sxs-lookup"><span data-stu-id="2d76f-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="2d76f-114">有关用于声明此属性的语法的详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2d76f-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="2d76f-115">ValidatePattern 指定正则表达式，用于验证参数自变量。</span><span class="sxs-lookup"><span data-stu-id="2d76f-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="2d76f-116">有关用于声明此属性的语法的详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2d76f-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="2d76f-117">ValidateRange 指定参数自变量的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="2d76f-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="2d76f-118">有关用于声明此属性的语法的详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2d76f-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="2d76f-119">ValidateSet 指定参数自变量的有效值。</span><span class="sxs-lookup"><span data-stu-id="2d76f-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="2d76f-120">有关用于声明此属性的语法的详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2d76f-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d76f-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d76f-121">See Also</span></span>

[<span data-ttu-id="2d76f-122">如何验证参数输入</span><span class="sxs-lookup"><span data-stu-id="2d76f-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="2d76f-123">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2d76f-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
