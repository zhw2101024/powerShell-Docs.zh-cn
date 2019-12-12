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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365516"
---
# <a name="how-to-validate-an-argument-range"></a>如何验证参数范围

此示例演示如何指定一个验证规则，Windows PowerShell 运行时可使用该规则在运行 cmdlet 之前检查参数参数的最小值和最大值。 可以通过声明 ValidateRange 属性设置此验证规则。

> [!NOTE]
> 有关用于定义此属性的类的详细信息，请参阅[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。

### <a name="to-validate-an-argument-range"></a>验证参数范围

- 添加 ValidateRange 特性，如下面的代码所示。 此示例为 `InputData` 参数指定范围0到5。

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

有关如何声明此特性的详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[ValidateRange 特性声明](./validaterange-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
