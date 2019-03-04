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
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251449"
---
# <a name="how-to-write-a-cmdlet"></a>如何编写 cmdlet

本文介绍如何编写的 cmdlet。 `Send-Greeting` Cmdlet 采用单个用户名称作为输入，然后将一条问候信息写入到该用户。 尽管该 cmdlet 不会做大量的工作，但此示例演示一个 cmdlet 的主要部分。

## <a name="steps-to-write-a-cmdlet"></a>若要编写的 cmdlet 的步骤

1. 若要将类声明为一个 cmdlet，使用**Cmdlet**属性。 **Cmdlet**属性指定动词和名词的 cmdlet 名称。

   有关详细信息**Cmdlet**属性，请参阅[CmdletAttribute 声明](cmdlet-attribute-declaration.md)。

2. 指定的类的名称。

3. 指定该 cmdlet 派生以下类之一：

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. 若要定义 cmdlet 的参数，请使用**参数**属性。 在这种情况下，只有一个指定必需的参数。

   有关详细信息**参数**属性，请参阅[ParameterAttribute 声明](parameter-attribute-declaration.md)。

5. 重写的输入处理方法，用于处理输入。 在这种情况下， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法被重写。

6. 若要编写问候语，使用该方法[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)。
   采用以下格式显示问候语：

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

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute Declaration](cmdlet-attribute-declaration.md)

[ParameterAttribute 声明](parameter-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](writing-a-windows-powershell-cmdlet.md)