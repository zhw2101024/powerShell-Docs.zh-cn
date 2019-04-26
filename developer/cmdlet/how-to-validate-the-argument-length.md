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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067701"
---
# <a name="how-to-validate-the-argument-length"></a>如何验证参数长度

此示例演示如何指定 Windows PowerShell 运行时可用于运行该 cmdlet 之前检查的参数自变量的字符 （长度） 数的验证规则。 通过声明 ValidateLength 属性来设置此验证规则。

> [!NOTE]
> 有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。

## <a name="to-validate-the-argument-length"></a>若要验证的参数长度

- 添加验证特性，如下面的代码中所示。 此示例指定参数的长度应具有长度为 0 到 10 个字符。

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

有关如何声明此属性的详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[ValidateLength 属性声明](./validatelength-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
