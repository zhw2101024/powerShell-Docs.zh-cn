---
title: 如何验证参数模式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855063"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="e003a-102">如何验证参数模式</span><span class="sxs-lookup"><span data-stu-id="e003a-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="e003a-103">此示例演示如何指定 Windows PowerShell 运行时可用于运行该 cmdlet 之前，请查看参数自变量的字符模式的验证规则。</span><span class="sxs-lookup"><span data-stu-id="e003a-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="e003a-104">通过声明 ValidatePattern 属性来设置此验证规则。</span><span class="sxs-lookup"><span data-stu-id="e003a-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="e003a-105">有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。</span><span class="sxs-lookup"><span data-stu-id="e003a-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="e003a-106">若要验证的自变量模式</span><span class="sxs-lookup"><span data-stu-id="e003a-106">To validate an argument pattern</span></span>

- <span data-ttu-id="e003a-107">添加验证特性，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="e003a-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="e003a-108">此示例指定四位数字，其中每个数字的值为 0 到 9 的模式。</span><span class="sxs-lookup"><span data-stu-id="e003a-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="e003a-109">有关如何声明此属性的详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="e003a-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e003a-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e003a-110">See Also</span></span>

[<span data-ttu-id="e003a-111">ValidatePattern 属性声明</span><span class="sxs-lookup"><span data-stu-id="e003a-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="e003a-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e003a-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
