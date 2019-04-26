---
title: 如何验证自变量范围 |Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067784"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="156f2-102">如何验证参数范围</span><span class="sxs-lookup"><span data-stu-id="156f2-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="156f2-103">此示例演示如何指定 Windows PowerShell 运行时可用于运行该 cmdlet 之前检查参数自变量的最小值和最大值的验证规则。</span><span class="sxs-lookup"><span data-stu-id="156f2-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="156f2-104">通过声明 ValidateRange 属性来设置此验证规则。</span><span class="sxs-lookup"><span data-stu-id="156f2-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="156f2-105">有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。</span><span class="sxs-lookup"><span data-stu-id="156f2-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="156f2-106">若要验证自变量范围</span><span class="sxs-lookup"><span data-stu-id="156f2-106">To validate an argument range</span></span>

- <span data-ttu-id="156f2-107">在下面的代码所示添加 ValidateRange 属性。</span><span class="sxs-lookup"><span data-stu-id="156f2-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="156f2-108">此示例中指定的范围为 0 到 5 的`InputData`参数。</span><span class="sxs-lookup"><span data-stu-id="156f2-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="156f2-109">有关如何声明此属性的详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="156f2-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="156f2-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="156f2-110">See Also</span></span>

[<span data-ttu-id="156f2-111">ValidateRange 属性声明</span><span class="sxs-lookup"><span data-stu-id="156f2-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="156f2-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="156f2-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
