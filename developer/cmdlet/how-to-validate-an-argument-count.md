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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067801"
---
# <a name="how-to-validate-an-argument-count"></a>如何验证参数计数

此示例演示如何指定 Windows PowerShell 运行时可用于检查的一个参数接受的参数 （计数） 的数目的验证规则之前运行该 cmdlet。 通过声明 ValidateCount 属性来设置此验证规则。

> [!NOTE]
> 有关定义此特性的类的详细信息，请参阅[System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。

## <a name="to-validate-an-argument-count"></a>若要验证的参数计数

- 添加验证特性，如下面的代码中所示。 此示例中指定该参数将接受一个参数或多达三个参数。

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

有关如何声明此属性的详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[ValidateCount 属性声明](./validatecount-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
