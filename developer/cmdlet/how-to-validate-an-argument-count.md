---
title: 如何验证参数计数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067801"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="2bb0b-102">如何验证参数计数</span><span class="sxs-lookup"><span data-stu-id="2bb0b-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="2bb0b-103">此示例演示如何指定 Windows PowerShell 运行时可用于检查的一个参数接受的参数 （计数） 的数目的验证规则之前运行该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2bb0b-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="2bb0b-104">通过声明 ValidateCount 属性来设置此验证规则。</span><span class="sxs-lookup"><span data-stu-id="2bb0b-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="2bb0b-105">有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。</span><span class="sxs-lookup"><span data-stu-id="2bb0b-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="2bb0b-106">若要验证的参数计数</span><span class="sxs-lookup"><span data-stu-id="2bb0b-106">To validate an argument count</span></span>

- <span data-ttu-id="2bb0b-107">添加验证特性，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="2bb0b-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="2bb0b-108">此示例中指定该参数将接受一个参数或多达三个参数。</span><span class="sxs-lookup"><span data-stu-id="2bb0b-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

<span data-ttu-id="2bb0b-109">有关如何声明此属性的详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="2bb0b-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2bb0b-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2bb0b-110">See Also</span></span>

[<span data-ttu-id="2bb0b-111">ValidateCount 属性声明</span><span class="sxs-lookup"><span data-stu-id="2bb0b-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="2bb0b-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bb0b-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
