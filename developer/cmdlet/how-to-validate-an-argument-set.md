---
title: 如何验证参数设置 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861363"
---
# <a name="how-to-validate-an-argument-set"></a>如何验证参数集

此示例演示如何指定 Windows PowerShell 运行时可用于运行该 cmdlet 之前，请查看参数自变量的验证规则。 此验证规则的参数自变量提供一的组有效的值。

> [!NOTE]
> 有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。

## <a name="to-validate-an-argument-set"></a>若要验证的参数集

- 在下面的代码所示添加 ValidateSet 属性。 此示例中指定的三个可能值的一组`UserName`参数。

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

有关如何声明此属性的详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[ValidateSet 属性声明](./validateset-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
