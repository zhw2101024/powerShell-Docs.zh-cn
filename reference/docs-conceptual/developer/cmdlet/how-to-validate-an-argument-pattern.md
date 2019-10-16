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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365556"
---
# <a name="how-to-validate-an-argument-pattern"></a>如何验证参数模式

此示例演示如何指定一个验证规则，Windows PowerShell 运行时可使用该规则在运行 cmdlet 之前检查参数参数的字符模式。 可以通过声明 ValidatePattern 属性设置此验证规则。

> [!NOTE]
> 有关用于定义此属性的类的详细信息，请参阅[Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。

## <a name="to-validate-an-argument-pattern"></a>验证参数模式

- 添加 Validate 特性，如下面的代码所示。 此示例指定四位数的模式，其中每个数字的值都为0到9。

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

有关如何声明此特性的详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
