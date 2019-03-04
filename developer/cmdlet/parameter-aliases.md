---
title: 参数别名 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853313"
---
# <a name="parameter-aliases"></a><span data-ttu-id="e7dc4-102">参数别名</span><span class="sxs-lookup"><span data-stu-id="e7dc4-102">Parameter Aliases</span></span>

<span data-ttu-id="e7dc4-103">Cmdlet 参数也可以有别名。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="e7dc4-104">键入或在命令中指定参数时，可以使用别名而不是参数名称。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="e7dc4-105">使用别名的好处</span><span class="sxs-lookup"><span data-stu-id="e7dc4-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="e7dc4-106">将别名添加到参数提供以下优势。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="e7dc4-107">可以提供一种快捷方式，以便用户无需调用 cmdlet 时，使用完整的参数名称。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="e7dc4-108">例如，您可以使用"CN"别名而不是参数名称"ComputerName"。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="e7dc4-109">如果您想要提供不同的名称相同的参数，可以定义多个别名。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="e7dc4-110">您可能想要定义多个别名，如果您需要使用不同的方式引用的相同数据的多个用户组。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="e7dc4-111">您可以向后兼容性为提供现有脚本的参数的名称更改。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="e7dc4-112">通过使用别名属性以及 ValueFromPipelineByName 属性，可以定义一个参数，它允许您 cmdlet 将绑定到不同的对象类型。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="e7dc4-113">例如，假设您有两个不同类型的对象的第一个对象具有编写器属性和第二个对象具有一个编辑器属性。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="e7dc4-114">如果你的 cmdlet 有一个参数，必须接受管道输入属性名称中基于编写器和编辑器别名和 cmdlet，cmdlet 可以将绑定到这两个对象使用两个参数的别名。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="e7dc4-115">有关可以用于特定参数的别名的详细信息，请参阅[通用参数名称](./common-parameter-names.md)。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="e7dc4-116">定义参数的别名</span><span class="sxs-lookup"><span data-stu-id="e7dc4-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="e7dc4-117">若要定义参数的别名，声明别名属性，如下面的参数声明中所示。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="e7dc4-118">在此示例中，相同的参数定义多个别名。</span><span class="sxs-lookup"><span data-stu-id="e7dc4-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="e7dc4-119">(有关详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。)</span><span class="sxs-lookup"><span data-stu-id="e7dc4-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="e7dc4-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7dc4-120">See Also</span></span>

[<span data-ttu-id="e7dc4-121">常见的参数名称</span><span class="sxs-lookup"><span data-stu-id="e7dc4-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="e7dc4-122">如何声明 Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="e7dc4-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="e7dc4-123">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e7dc4-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
