---
title: ValidatePattern 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067121"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="475fe-102">ValidatePattern 属性声明</span><span class="sxs-lookup"><span data-stu-id="475fe-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="475fe-103">ValidatePattern 属性指定的正则表达式模式，用于验证的 cmdlet 参数的参数。</span><span class="sxs-lookup"><span data-stu-id="475fe-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="475fe-104">Windows PowerShell 函数还可以使用此属性。</span><span class="sxs-lookup"><span data-stu-id="475fe-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="475fe-105">在 cmdlet 内调用 ValidatePattern 时，Windows PowerShell 运行时将 cmdlet 参数的参数转换为字符串，然后将该字符串 ValidatePattern 特性提供的模式进行比较。</span><span class="sxs-lookup"><span data-stu-id="475fe-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="475fe-106">转换后的字符串表示形式的参数而提供的模式与匹配时才运行该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="475fe-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="475fe-107">如果不匹配，是由 Windows PowerShell 运行时引发错误。</span><span class="sxs-lookup"><span data-stu-id="475fe-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="475fe-108">语法</span><span class="sxs-lookup"><span data-stu-id="475fe-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="475fe-109">参数</span><span class="sxs-lookup"><span data-stu-id="475fe-109">Parameters</span></span>

<span data-ttu-id="475fe-110">`RegexString` ([System.String](/dotnet/api/System.String)) 所需。</span><span class="sxs-lookup"><span data-stu-id="475fe-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="475fe-111">指定正则表达式，用于验证参数自变量。</span><span class="sxs-lookup"><span data-stu-id="475fe-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="475fe-112">选项 ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="475fe-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="475fe-113">指定的按位组合[System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)标志，用于指定正则表达式选项。</span><span class="sxs-lookup"><span data-stu-id="475fe-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="475fe-114">备注</span><span class="sxs-lookup"><span data-stu-id="475fe-114">Remarks</span></span>

- <span data-ttu-id="475fe-115">此属性可以使用仅一次，每个参数。</span><span class="sxs-lookup"><span data-stu-id="475fe-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="475fe-116">可以使用`Option`的属性来进一步定义模式参数。</span><span class="sxs-lookup"><span data-stu-id="475fe-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="475fe-117">例如，可以使该模式区分大小写。</span><span class="sxs-lookup"><span data-stu-id="475fe-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="475fe-118">如果此特性应用于一个集合，集合中的每个元素必须匹配的模式。</span><span class="sxs-lookup"><span data-stu-id="475fe-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="475fe-119">通过定义 ValidatePattern 特性[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="475fe-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="475fe-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="475fe-120">See Also</span></span>

[<span data-ttu-id="475fe-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="475fe-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="475fe-122">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="475fe-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
