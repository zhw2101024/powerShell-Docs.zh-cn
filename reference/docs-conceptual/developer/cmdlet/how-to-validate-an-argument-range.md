---
title: 如何验证参数范围 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365516"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="371e8-102">如何验证参数范围</span><span class="sxs-lookup"><span data-stu-id="371e8-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="371e8-103">此示例演示如何指定一个验证规则，Windows PowerShell 运行时可使用该规则在运行 cmdlet 之前检查参数参数的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="371e8-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="371e8-104">可以通过声明 ValidateRange 属性设置此验证规则。</span><span class="sxs-lookup"><span data-stu-id="371e8-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="371e8-105">有关用于定义此属性的类的详细信息，请参阅[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。</span><span class="sxs-lookup"><span data-stu-id="371e8-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="371e8-106">验证参数范围</span><span class="sxs-lookup"><span data-stu-id="371e8-106">To validate an argument range</span></span>

- <span data-ttu-id="371e8-107">添加 ValidateRange 特性，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="371e8-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="371e8-108">此示例为 `InputData` 参数指定范围0到5。</span><span class="sxs-lookup"><span data-stu-id="371e8-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="371e8-109">有关如何声明此特性的详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="371e8-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="371e8-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="371e8-110">See Also</span></span>

[<span data-ttu-id="371e8-111">ValidateRange 特性声明</span><span class="sxs-lookup"><span data-stu-id="371e8-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="371e8-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="371e8-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
