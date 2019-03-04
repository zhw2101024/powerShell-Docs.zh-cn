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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859733"
---
# <a name="how-to-validate-an-argument-range"></a>如何验证参数范围

此示例演示如何指定 Windows PowerShell 运行时可用于运行该 cmdlet 之前检查参数自变量的最小值和最大值的验证规则。 通过声明 ValidateRange 属性来设置此验证规则。

> [!NOTE]
> 有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。

### <a name="to-validate-an-argument-range"></a>若要验证自变量范围

- 在下面的代码所示添加 ValidateRange 属性。 此示例中指定的范围为 0 到 5 的`InputData`参数。

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

有关如何声明此属性的详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[ValidateRange 属性声明](./validaterange-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
