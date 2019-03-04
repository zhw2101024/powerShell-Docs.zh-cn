---
title: 如何请求确认 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863403"
---
# <a name="how-to-request-confirmations"></a>如何请求确认

此示例演示如何调用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法来请求从确认执行操作前的用户。

> [!IMPORTANT]
> 有关 Windows PowerShell 如何处理这些请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。

## <a name="to-request-confirmation"></a>请求确认

1. 絋粄`SupportsShouldProcess`参数的 Cmdlet 属性设置为`true`。 （对于函数这是 CmdletBinding 属性的参数。）

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. 添加`Force`到 cmdlet 的参数，以便用户可以重写确认请求。

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. 添加`if`使用的返回值的语句[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，以确定如果[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)调用方法。

4. 添加另一个`if`使用的返回值的语句[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法和的值`Force`参数，以确定是否应将该操作执行。

## <a name="example"></a>示例

在下面的代码示例中， [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)中调用方法重写[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 但是，您可以从其他输入处理方法调用这些方法。

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
