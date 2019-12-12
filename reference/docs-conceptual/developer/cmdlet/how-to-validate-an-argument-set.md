---
title: 如何验证参数集 |Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365506"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="121a0-102">如何验证参数集</span><span class="sxs-lookup"><span data-stu-id="121a0-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="121a0-103">此示例演示如何在运行 cmdlet 之前指定 Windows PowerShell 运行时可用于检查参数参数的验证规则。</span><span class="sxs-lookup"><span data-stu-id="121a0-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="121a0-104">此验证规则为参数参数提供了一组有效值。</span><span class="sxs-lookup"><span data-stu-id="121a0-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="121a0-105">有关用于定义此属性的类的详细信息，请参阅[Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。</span><span class="sxs-lookup"><span data-stu-id="121a0-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="121a0-106">验证参数集</span><span class="sxs-lookup"><span data-stu-id="121a0-106">To validate an argument set</span></span>

- <span data-ttu-id="121a0-107">添加 ValidateSet 特性，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="121a0-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="121a0-108">此示例为 `UserName` 参数指定了一组三个可能的值。</span><span class="sxs-lookup"><span data-stu-id="121a0-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="121a0-109">有关如何声明此特性的详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="121a0-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="121a0-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="121a0-110">See Also</span></span>

[<span data-ttu-id="121a0-111">System.web. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="121a0-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="121a0-112">ValidateSet 特性声明</span><span class="sxs-lookup"><span data-stu-id="121a0-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="121a0-113">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="121a0-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
