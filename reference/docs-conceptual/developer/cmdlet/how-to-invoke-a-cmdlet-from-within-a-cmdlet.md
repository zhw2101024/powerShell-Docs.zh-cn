---
title: 如何从 Cmdlet 内调用 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365546"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="ca97a-102">如何从 Cmdlet 内部调用 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca97a-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="ca97a-103">此示例演示如何从另一个 cmdlet 中调用 cmdlet，这允许你将调用的 cmdlet 的功能添加到正在开发的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ca97a-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="ca97a-104">在此示例中，调用 `Get-Process` cmdlet 来获取本地计算机上运行的进程。</span><span class="sxs-lookup"><span data-stu-id="ca97a-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="ca97a-105">调用 `Get-Process` cmdlet 等效于以下命令。</span><span class="sxs-lookup"><span data-stu-id="ca97a-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="ca97a-106">此命令检索其名称以字符 "a" 到 "t" 开头的所有进程。</span><span class="sxs-lookup"><span data-stu-id="ca97a-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="ca97a-107">你可以仅调用直接从[system.web](/dotnet/api/System.Management.Automation.Cmdlet)类派生的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ca97a-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="ca97a-108">不能调用派生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ca97a-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="ca97a-109">从 cmdlet 内调用 cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca97a-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="ca97a-110">确保引用定义要调用的 cmdlet 的程序集，并且添加适当的 @no__t 0 语句。</span><span class="sxs-lookup"><span data-stu-id="ca97a-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="ca97a-111">在此示例中，添加了以下命名空间。</span><span class="sxs-lookup"><span data-stu-id="ca97a-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="ca97a-112">在 cmdlet 的输入处理方法中，创建要调用的 cmdlet 的新实例。</span><span class="sxs-lookup"><span data-stu-id="ca97a-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="ca97a-113">在此示例中，将创建一个类型为[Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand)的对象，并在其中包含调用 cmdlet 时使用的参数的字符串。</span><span class="sxs-lookup"><span data-stu-id="ca97a-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="ca97a-114">调用 " [system.object](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) " 方法以调用 `Get-Process` Cmdlet 的。</span><span class="sxs-lookup"><span data-stu-id="ca97a-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="ca97a-115">示例</span><span class="sxs-lookup"><span data-stu-id="ca97a-115">Example</span></span>

<span data-ttu-id="ca97a-116">在此示例中，将从 cmdlet 的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中调用 `Get-Process` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ca97a-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ca97a-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca97a-117">See Also</span></span>

[<span data-ttu-id="ca97a-118">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca97a-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
