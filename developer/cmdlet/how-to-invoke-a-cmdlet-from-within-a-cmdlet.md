---
title: 如何调用在 Cmdlet 中的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: d4564b51b74422cdaec3878b227ffc6be7c97949
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855883"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="bb1dd-102">如何从 Cmdlet 内部调用 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bb1dd-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="bb1dd-103">此示例演示如何调用在另一个 cmdlet，后者允许您将调用 cmdlet 的功能添加到该 cmdlet 正在开发中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="bb1dd-104">在此示例中， `Get-Process` cmdlet 调用来获取本地计算机运行的进程。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="bb1dd-105">对调用`Get-Process`cmdlet 等效于以下命令。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="bb1dd-106">此命令检索其名称以字符"a"到"t"开头的所有进程。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="bb1dd-107">可以调用仅直接派生这些 cmdlet [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="bb1dd-108">不能调用派生的 cmdlet [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="bb1dd-109">若要调用在 cmdlet 中的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="bb1dd-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="bb1dd-110">确保已引用程序集，用于定义要调用的 cmdlet 和的相应`using`添加语句。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="bb1dd-111">在此示例中，添加以下命名空间。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="bb1dd-112">在处理方法，该 cmdlet 的输入，将创建要调用该 cmdlet 的新实例。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="bb1dd-113">在此示例中，类型的对象[Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand)创建和包含调用 cmdlet 时使用的参数的字符串。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-113">In this example, an object of type [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="bb1dd-114">调用[System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法来调用`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="bb1dd-115">示例</span><span class="sxs-lookup"><span data-stu-id="bb1dd-115">Example</span></span>

<span data-ttu-id="bb1dd-116">在此示例中， `Get-Process` cmdlet 调用内[System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cmdlet 的方法。</span><span class="sxs-lookup"><span data-stu-id="bb1dd-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

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

## <a name="see-also"></a><span data-ttu-id="bb1dd-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb1dd-117">See Also</span></span>

[<span data-ttu-id="bb1dd-118">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bb1dd-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
