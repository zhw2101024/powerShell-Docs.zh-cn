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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365486"
---
# <a name="how-to-validate-the-argument-length"></a>如何验证参数长度

此示例演示如何指定一个验证规则，Windows PowerShell 运行时可使用该规则检查在运行 cmdlet 之前参数参数的字符数（长度）。 可以通过声明 ValidateLength 属性设置此验证规则。

> [!NOTE]
> 有关用于定义此属性的类的详细信息，请参阅[Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。

## <a name="to-validate-the-argument-length"></a>验证参数长度

- 添加 Validate 特性，如下面的代码所示。 此示例指定参数的长度应为0到10个字符。

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

有关如何声明此特性的详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[ValidateLength 特性声明](./validatelength-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
