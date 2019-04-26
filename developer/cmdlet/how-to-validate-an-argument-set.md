---
title: 如何验证参数设置 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067700"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="e35d4-102">如何验证参数集</span><span class="sxs-lookup"><span data-stu-id="e35d4-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="e35d4-103">此示例演示如何指定 Windows PowerShell 运行时可用于运行该 cmdlet 之前，请查看参数自变量的验证规则。</span><span class="sxs-lookup"><span data-stu-id="e35d4-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="e35d4-104">此验证规则的参数自变量提供一的组有效的值。</span><span class="sxs-lookup"><span data-stu-id="e35d4-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="e35d4-105">有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。</span><span class="sxs-lookup"><span data-stu-id="e35d4-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="e35d4-106">若要验证的参数集</span><span class="sxs-lookup"><span data-stu-id="e35d4-106">To validate an argument set</span></span>

- <span data-ttu-id="e35d4-107">在下面的代码所示添加 ValidateSet 属性。</span><span class="sxs-lookup"><span data-stu-id="e35d4-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="e35d4-108">此示例中指定的三个可能值的一组`UserName`参数。</span><span class="sxs-lookup"><span data-stu-id="e35d4-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="e35d4-109">有关如何声明此属性的详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e35d4-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e35d4-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e35d4-110">See Also</span></span>

[<span data-ttu-id="e35d4-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="e35d4-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="e35d4-112">ValidateSet 属性声明</span><span class="sxs-lookup"><span data-stu-id="e35d4-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="e35d4-113">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e35d4-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
