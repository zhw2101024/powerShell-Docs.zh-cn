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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369586"
---
# <a name="parameter-aliases"></a><span data-ttu-id="78343-102">参数别名</span><span class="sxs-lookup"><span data-stu-id="78343-102">Parameter Aliases</span></span>

<span data-ttu-id="78343-103">Cmdlet 参数还可以有别名。</span><span class="sxs-lookup"><span data-stu-id="78343-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="78343-104">在命令中键入或指定参数时，可以使用别名，而不是参数名称。</span><span class="sxs-lookup"><span data-stu-id="78343-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="78343-105">使用别名的好处</span><span class="sxs-lookup"><span data-stu-id="78343-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="78343-106">将别名添加到参数提供以下优点。</span><span class="sxs-lookup"><span data-stu-id="78343-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="78343-107">您可以提供一个快捷方式，以便用户在调用 cmdlet 时不必使用完整的参数名称。</span><span class="sxs-lookup"><span data-stu-id="78343-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="78343-108">例如，可以使用 "CN" 别名，而不是参数名称 "ComputerName"。</span><span class="sxs-lookup"><span data-stu-id="78343-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="78343-109">如果要为同一参数提供不同的名称，可以定义多个别名。</span><span class="sxs-lookup"><span data-stu-id="78343-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="78343-110">如果必须使用以不同方式引用相同数据的多个用户组，则可能需要定义多个别名。</span><span class="sxs-lookup"><span data-stu-id="78343-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="78343-111">如果参数名称发生更改，则可以为现有脚本提供向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="78343-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="78343-112">通过使用 Alias 属性和 ValueFromPipelineByName 属性，可以定义一个参数，该参数允许 cmdlet 绑定到不同的对象类型。</span><span class="sxs-lookup"><span data-stu-id="78343-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="78343-113">例如，假设您有两个不同类型的对象，第一个对象有一个写入器属性，并且第二个对象有一个编辑器属性。</span><span class="sxs-lookup"><span data-stu-id="78343-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="78343-114">如果 cmdlet 有一个参数，该参数具有编写器和编辑器别名，并且 cmdlet 已根据属性名称接受管道输入，则 cmdlet 可以使用两个参数别名绑定到这两个对象。</span><span class="sxs-lookup"><span data-stu-id="78343-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="78343-115">有关可用于特定参数的别名的详细信息，请参阅[通用参数名称](./common-parameter-names.md)。</span><span class="sxs-lookup"><span data-stu-id="78343-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="78343-116">定义参数别名</span><span class="sxs-lookup"><span data-stu-id="78343-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="78343-117">若要为参数定义别名，请声明 Alias 特性，如下面的参数声明中所示。</span><span class="sxs-lookup"><span data-stu-id="78343-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="78343-118">在此示例中，为同一参数定义了多个别名。</span><span class="sxs-lookup"><span data-stu-id="78343-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="78343-119">（有关详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。）</span><span class="sxs-lookup"><span data-stu-id="78343-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="78343-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78343-120">See Also</span></span>

[<span data-ttu-id="78343-121">常见参数名称</span><span class="sxs-lookup"><span data-stu-id="78343-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="78343-122">如何声明 Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="78343-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="78343-123">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="78343-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
