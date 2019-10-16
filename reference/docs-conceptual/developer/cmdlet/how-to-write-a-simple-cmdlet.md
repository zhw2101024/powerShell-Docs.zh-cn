---
title: 如何编写简单的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365466"
---
# <a name="how-to-write-a-cmdlet"></a>如何编写 cmdlet

本文介绍如何编写 cmdlet。 @No__t cmdlet 使用单个用户名作为输入，然后将问候语写入该用户。 尽管此 cmdlet 不会执行许多工作，但本示例演示了 cmdlet 的主要部分。

## <a name="steps-to-write-a-cmdlet"></a>编写 cmdlet 的步骤

1. 若要将类声明为 cmdlet，请使用**cmdlet**特性。 **Cmdlet**属性指定该 cmdlet 名称的动词和名词。

   有关**Cmdlet**特性的详细信息，请参阅[CmdletAttribute 声明](cmdlet-attribute-declaration.md)。

2. 指定类的名称。

3. 指定该 cmdlet 派生自以下任一类：

   * [System.object。](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.web. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. 若要定义 cmdlet 的参数，请使用**Parameter**特性。 在这种情况下，只指定了一个必需的参数。

   有关**参数**属性的详细信息，请参阅[ParameterAttribute 声明](parameter-attribute-declaration.md)。

5. 重写处理输入的输入处理方法。 在这种情况下，将重写[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。

6. 若要编写问候语，请使用方法[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)。
   该问候语按以下格式显示：

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>示例

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>另请参阅

[System.object。](/dotnet/api/System.Management.Automation.Cmdlet)

[System.web. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

["ProcessRecord"。](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

["WriteObject"。](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute 声明](cmdlet-attribute-declaration.md)

[ParameterAttribute 声明](parameter-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)