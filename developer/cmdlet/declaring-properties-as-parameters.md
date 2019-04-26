---
title: 声明属性作为参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068260"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="71773-102">将属性声明为参数</span><span class="sxs-lookup"><span data-stu-id="71773-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="71773-103">本主题提供了声明的参数的 cmdlet 之前，您必须了解的基本信息。</span><span class="sxs-lookup"><span data-stu-id="71773-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="71773-104">若要声明 cmdlet 类中的 cmdlet 的参数，请定义公共属性表示每个参数，并将一个或多个参数属性添加到每个属性。</span><span class="sxs-lookup"><span data-stu-id="71773-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="71773-105">Windows PowerShell 运行时使用的参数属性来标识作为 cmdlet 参数的属性。</span><span class="sxs-lookup"><span data-stu-id="71773-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="71773-106">声明参数属性的基本语法是`[Parameter()]`。</span><span class="sxs-lookup"><span data-stu-id="71773-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="71773-107">下面是属性的定义为必需的参数的示例。</span><span class="sxs-lookup"><span data-stu-id="71773-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="71773-108">以下是要记住有关参数的一些事项。</span><span class="sxs-lookup"><span data-stu-id="71773-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="71773-109">参数必须显式标记为公共。</span><span class="sxs-lookup"><span data-stu-id="71773-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="71773-110">未标记为公共的默认为内部和 Windows PowerShell 运行时将不会找到的参数。</span><span class="sxs-lookup"><span data-stu-id="71773-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="71773-111">参数应定义为 Microsoft.NET Framework 类型，以提供更好的参数验证。</span><span class="sxs-lookup"><span data-stu-id="71773-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="71773-112">例如，限制为一个值超出的一组值的参数应定义为枚举类型。</span><span class="sxs-lookup"><span data-stu-id="71773-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="71773-113">获取统一资源标识符 (URI) 值的参数应为类型[System.Uri](/dotnet/api/System.Uri)。</span><span class="sxs-lookup"><span data-stu-id="71773-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="71773-114">避免以外的所有的自由格式文本属性的基本字符串参数。</span><span class="sxs-lookup"><span data-stu-id="71773-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="71773-115">可以将参数添加到任意数量的参数集。</span><span class="sxs-lookup"><span data-stu-id="71773-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="71773-116">有关参数集的详细信息，请参阅[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="71773-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="71773-117">Windows PowerShell 还提供了一组会自动提供给每个 cmdlet 的常见参数。</span><span class="sxs-lookup"><span data-stu-id="71773-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="71773-118">有关这些参数及其各自的别名的详细信息，请参阅[Cmdlet 流通用参数](./common-parameter-names.md)。</span><span class="sxs-lookup"><span data-stu-id="71773-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71773-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71773-119">See Also</span></span>

[<span data-ttu-id="71773-120">Cmdlet 常见参数</span><span class="sxs-lookup"><span data-stu-id="71773-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="71773-121">类型的 Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="71773-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="71773-122">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="71773-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
