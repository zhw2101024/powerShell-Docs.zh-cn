---
title: 如何声明 Cmdlet 参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861393"
---
# <a name="how-to-declare-cmdlet-parameters"></a>如何声明 Cmdlet 参数

这些示例显示如何声明命名、 位置、 必需、 可选的和开关参数。 这些示例还演示如何定义参数别名。

## <a name="how-to-declare-a-named-parameter"></a>如何声明一个命名的参数

- 定义公共属性，如下面的代码中所示。 当您添加的参数属性时，请省略`Position`从属性中的关键字。

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

有关参数属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-positional-parameter"></a>如何声明位置参数

- 定义公共属性，如下面的代码中所示。 当您添加的参数属性时，请设置`Position`关键字的参数位置。 值为 0 指示第一个位置。

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

有关参数属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-mandatory-parameter"></a>如何以声明的必需参数

- 定义公共属性，如下面的代码中所示。 当您添加的参数属性时，请设置`Mandatory`关键字`true`。

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

有关参数属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-an-optional-parameter"></a>如何声明一个可选参数

- 定义公共属性，如下面的代码中所示。 当您添加的参数属性时，请省略`Mandatory`关键字。

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>如何声明一个开关参数

- 公共属性定义为类型[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)，然后声明参数属性。

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

有关参数属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。

## <a name="how-to-declare-a-parameter-with-aliases"></a>如何声明具有别名的参数

- 定义公共属性，如下面的代码中所示。 添加别名属性，其中列出了该参数的别名。 在此示例中，相同的参数定义三个别名。 第一个别名提供了一种快捷方式。 第二个和第三个别名，提供可用于不同方案的名称。

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

有关别名属性的详细信息，请参阅[别名属性声明](./alias-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[参数特性声明](./parameter-attribute-declaration.md)

[别名属性声明](./alias-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
