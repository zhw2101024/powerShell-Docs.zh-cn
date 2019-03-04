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
# <a name="how-to-validate-an-argument-pattern"></a>如何验证参数模式

此示例演示如何指定 Windows PowerShell 运行时可用于运行该 cmdlet 之前，请查看参数自变量的字符模式的验证规则。 通过声明 ValidatePattern 属性来设置此验证规则。

> [!NOTE]
> 有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。

## <a name="to-validate-an-argument-pattern"></a>若要验证的自变量模式

- 添加验证特性，如下面的代码中所示。 此示例指定四位数字，其中每个数字的值为 0 到 9 的模式。

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

有关如何声明此属性的详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[ValidatePattern 属性声明](./validatepattern-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
