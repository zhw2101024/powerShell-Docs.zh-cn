---
title: 如何验证参数长度 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857123"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="638f4-102">如何验证参数长度</span><span class="sxs-lookup"><span data-stu-id="638f4-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="638f4-103">此示例演示如何指定 Windows PowerShell 运行时可用于运行该 cmdlet 之前检查的参数自变量的字符 （长度） 数的验证规则。</span><span class="sxs-lookup"><span data-stu-id="638f4-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="638f4-104">通过声明 ValidateLength 属性来设置此验证规则。</span><span class="sxs-lookup"><span data-stu-id="638f4-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="638f4-105">有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。</span><span class="sxs-lookup"><span data-stu-id="638f4-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="638f4-106">若要验证的参数长度</span><span class="sxs-lookup"><span data-stu-id="638f4-106">To validate the argument length</span></span>

- <span data-ttu-id="638f4-107">添加验证特性，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="638f4-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="638f4-108">此示例指定参数的长度应具有长度为 0 到 10 个字符。</span><span class="sxs-lookup"><span data-stu-id="638f4-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="638f4-109">有关如何声明此属性的详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="638f4-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="638f4-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="638f4-110">See Also</span></span>

[<span data-ttu-id="638f4-111">ValidateLength 属性声明</span><span class="sxs-lookup"><span data-stu-id="638f4-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="638f4-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="638f4-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
