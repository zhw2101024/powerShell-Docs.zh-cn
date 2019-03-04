---
title: Cmdlet 动态参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853803"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet 动态参数

Cmdlet 可以定义可供用户使用特殊情况下，例如，当另一个参数的参数为特定值的参数。 这些参数在运行时添加和嘿*动态参数*因为仅在需要时添加它们。 例如，您可以设计添加几个参数，仅当指定一个特定的开关参数的 cmdlet。

> [!NOTE]
> 提供程序和 Windows PowerShell 函数还可以定义动态参数。

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>在 Windows PowerShell Cmdlet 的动态参数

Windows PowerShell 在多个提供程序 cmdlet 中使用动态参数。 例如，`Get-Item`并`Get-ChildItem`cmdlet 添加`CodeSigningCert`在运行时参数时`Path`cmdlet 参数指定的证书提供程序路径。 如果`Path`cmdlet 参数指定的路径不同的提供程序，`CodeSigningCert`参数不可用。

下面的示例演示如何`CodeSigningCert`在运行时添加参数时`Get-Item`运行 cmdlet。

在第一个示例中，Windows PowerShell 运行时已添加了参数，并且该 cmdlet 成功。

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

在第二个示例中，指定文件系统驱动器，并返回错误。 错误消息指示`CodeSigningCert`找不到参数。

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>对动态参数的支持

若要支持动态参数，cmdlet 代码必须包含以下元素。

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)此接口提供用于检索动态参数的方法。

例如：

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)此方法检索包含的动态参数定义的对象。

例如：

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

动态参数类此类定义要添加的参数。 此类必须包含每个参数和所需 cmdlet 的任何可选别名和验证属性的参数属性。

例如：

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

支持动态参数的 cmdlet 的完整示例，请参阅[如何声明动态参数](./how-to-declare-dynamic-parameters.md)。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[如何声明动态参数](./how-to-declare-dynamic-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
