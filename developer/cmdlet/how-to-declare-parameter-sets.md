---
title: 如何声明参数集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067886"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="8740a-102">如何声明参数集</span><span class="sxs-lookup"><span data-stu-id="8740a-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="8740a-103">此示例演示如何声明一个 cmdlet 的参数时定义两个参数集。</span><span class="sxs-lookup"><span data-stu-id="8740a-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="8740a-104">每个参数集具有唯一的参数和两个参数集使用了共享的参数。</span><span class="sxs-lookup"><span data-stu-id="8740a-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="8740a-105">有关参数集，包括如何指定默认参数集，请参阅[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="8740a-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8740a-106">只要有可能，定义一个参数为必需的参数集的唯一参数。</span><span class="sxs-lookup"><span data-stu-id="8740a-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="8740a-107">但是，如果你想在 cmdlet 运行而无需指定任何参数，唯一的参数可以是一个可选参数。</span><span class="sxs-lookup"><span data-stu-id="8740a-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="8740a-108">例如，唯一的参数`Get-Command`cmdlet 是可选的。</span><span class="sxs-lookup"><span data-stu-id="8740a-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="8740a-109">如何定义两个参数集</span><span class="sxs-lookup"><span data-stu-id="8740a-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="8740a-110">添加`ParameterSet`到第一个参数集的唯一参数的参数属性的关键字。</span><span class="sxs-lookup"><span data-stu-id="8740a-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="8740a-111">添加`ParameterSet`到第二个参数集的唯一参数的参数属性的关键字。</span><span class="sxs-lookup"><span data-stu-id="8740a-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="8740a-112">对于属于这两个参数集参数，添加每个参数集的参数属性，然后添加`ParameterSet`到每个集的关键字。</span><span class="sxs-lookup"><span data-stu-id="8740a-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="8740a-113">在每个参数属性，可以指定该参数的定义方式。</span><span class="sxs-lookup"><span data-stu-id="8740a-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="8740a-114">参数可以是中一组可选的在另一个强制性。</span><span class="sxs-lookup"><span data-stu-id="8740a-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="8740a-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8740a-115">See Also</span></span>

[<span data-ttu-id="8740a-116">Cmdlet 参数集</span><span class="sxs-lookup"><span data-stu-id="8740a-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="8740a-117">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8740a-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
