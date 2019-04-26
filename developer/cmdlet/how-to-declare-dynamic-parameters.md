---
title: 如何将动态参数声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067905"
---
# <a name="how-to-declare-dynamic-parameters"></a>如何声明动态参数

此示例演示如何定义添加到在运行时该 cmdlet 的动态参数。 在此示例中，`Department`参数添加到 cmdlet，每当用户指定`Employee`开关参数。 有关动态参数的详细信息，请参阅[Cmdlet 的动态参数](./cmdlet-dynamic-parameters.md)。

## <a name="to-define-dynamic-parameters"></a>若要定义动态参数

1. 在 cmdlet 类声明中，添加[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)接口如所示。

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. 调用[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)方法，返回的对象定义的动态参数的顺序。 在此示例中，该方法时调用`Employee`指定参数。

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

3. 声明的类，定义要添加的动态参数。 可以使用用于声明来声明的动态参数的静态 cmdlet 参数的属性。

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

## <a name="example"></a>示例

在此示例中，`Department`用户指定时，会添加参数`Employee`参数。 `Department`参数是一个可选参数，和 ValidateSet 属性用于指定允许的参数。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
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

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
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
}
```

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cmdlet 动态参数](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)