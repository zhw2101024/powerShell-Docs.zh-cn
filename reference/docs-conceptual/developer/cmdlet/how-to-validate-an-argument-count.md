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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365526"
---
# <a name="how-to-validate-an-argument-count"></a>如何验证参数计数

此示例演示如何指定一个验证规则，Windows PowerShell 运行时可使用该规则检查参数在运行 cmdlet 之前接受的参数数量（计数）。 可以通过声明 ValidateCount 属性设置此验证规则。

> [!NOTE]
> 有关用于定义此属性的类的详细信息，请参阅[Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。

## <a name="to-validate-an-argument-count"></a>验证参数计数

- 添加 Validate 特性，如下面的代码所示。 此示例指定参数将接受一个参数或多达三个参数。

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

有关如何声明此特性的详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[ValidateCount 特性声明](./validatecount-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
