---
title: Windows PowerShell 主机快速入门 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360816"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="ff700-102">Windows PowerShell 主机快速入门</span><span class="sxs-lookup"><span data-stu-id="ff700-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="ff700-103">若要在应用程序中托管 Windows PowerShell，请使用[system.web](/dotnet/api/System.Management.Automation.PowerShell)类。</span><span class="sxs-lookup"><span data-stu-id="ff700-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="ff700-104">此类提供创建命令管道，然后在运行空间中执行这些命令的方法。</span><span class="sxs-lookup"><span data-stu-id="ff700-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="ff700-105">创建主机应用程序的最简单方法是使用默认的运行空间。</span><span class="sxs-lookup"><span data-stu-id="ff700-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="ff700-106">默认运行空间包含所有核心 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="ff700-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="ff700-107">如果希望应用程序仅公开部分 Windows PowerShell 命令，则必须创建自定义运行空间。</span><span class="sxs-lookup"><span data-stu-id="ff700-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="ff700-108">使用默认运行空间</span><span class="sxs-lookup"><span data-stu-id="ff700-108">Using the default runspace</span></span>

<span data-ttu-id="ff700-109">首先，我们将使用默认的运行空间，并使用[system.web](/dotnet/api/System.Management.Automation.PowerShell)类的方法向管道添加命令、参数、语句和脚本。</span><span class="sxs-lookup"><span data-stu-id="ff700-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="ff700-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="ff700-110">AddCommand</span></span>

<span data-ttu-id="ff700-111">您可以使用[AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法将命令添加到管道中。</span><span class="sxs-lookup"><span data-stu-id="ff700-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="ff700-112">例如，假设您希望获取计算机上正在运行的进程的列表。</span><span class="sxs-lookup"><span data-stu-id="ff700-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="ff700-113">运行此命令的方法如下所示。</span><span class="sxs-lookup"><span data-stu-id="ff700-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="ff700-114">创建一个 "[管理](/dotnet/api/System.Management.Automation.PowerShell)" 对象。</span><span class="sxs-lookup"><span data-stu-id="ff700-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="ff700-115">添加要执行的命令。</span><span class="sxs-lookup"><span data-stu-id="ff700-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="ff700-116">调用命令。</span><span class="sxs-lookup"><span data-stu-id="ff700-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="ff700-117">如果在调用[AddCommand 方法之前](/dotnet/api/System.Management.Automation.PowerShell.Invoke)多次调用了方法，则第一个命令的结果将通过管道传递到第二个命令，依此类推。</span><span class="sxs-lookup"><span data-stu-id="ff700-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="ff700-118">如果你不想通过管道将前一个命令的结果传递给命令，请改为通过调用[AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)来添加它。</span><span class="sxs-lookup"><span data-stu-id="ff700-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="ff700-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="ff700-119">AddParameter</span></span>

<span data-ttu-id="ff700-120">前面的示例执行一个不带任何参数的命令。</span><span class="sxs-lookup"><span data-stu-id="ff700-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="ff700-121">可以使用[PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法将参数添加到命令中。</span><span class="sxs-lookup"><span data-stu-id="ff700-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="ff700-122">例如，下面的代码获取在计算机上运行的名为 `PowerShell` 的所有进程的列表。</span><span class="sxs-lookup"><span data-stu-id="ff700-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="ff700-123">可以通过重复调用 AddParameter 方法来添加其他参数。</span><span class="sxs-lookup"><span data-stu-id="ff700-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="ff700-124">你还可以通过调用[AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法来添加参数名称和值的字典。</span><span class="sxs-lookup"><span data-stu-id="ff700-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="ff700-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="ff700-125">AddStatement</span></span>

<span data-ttu-id="ff700-126">您可以使用[AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法来模拟批处理，该方法将附加语句添加到管道的末尾。</span><span class="sxs-lookup"><span data-stu-id="ff700-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="ff700-127">下面的代码获取名称 `PowerShell`正在运行的进程的列表，然后获取正在运行的服务的列表。</span><span class="sxs-lookup"><span data-stu-id="ff700-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="ff700-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="ff700-128">AddScript</span></span>

<span data-ttu-id="ff700-129">您可以通过调用[AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法来运行现有的脚本。</span><span class="sxs-lookup"><span data-stu-id="ff700-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="ff700-130">下面的示例向管道添加一个脚本并运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="ff700-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="ff700-131">此示例假设名为 `D:\PSScripts`的文件夹中已有一个名为 `MyScript.ps1` 的脚本。</span><span class="sxs-lookup"><span data-stu-id="ff700-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="ff700-132">还有一个 AddScript 方法版本，该方法采用名为 `useLocalScope`的布尔参数。</span><span class="sxs-lookup"><span data-stu-id="ff700-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="ff700-133">如果将此参数设置为 `true`，则脚本将在本地作用域中运行。</span><span class="sxs-lookup"><span data-stu-id="ff700-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="ff700-134">以下代码将在本地作用域中运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="ff700-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="ff700-135">创建自定义运行空间</span><span class="sxs-lookup"><span data-stu-id="ff700-135">Creating a custom runspace</span></span>

<span data-ttu-id="ff700-136">虽然前面的示例中使用的默认运行空间加载了所有核心 Windows PowerShell 命令，但你可以创建一个自定义的运行空间，该运行空间仅加载指定的所有命令子集。</span><span class="sxs-lookup"><span data-stu-id="ff700-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="ff700-137">你可能希望执行此操作以提高性能（加载更多的命令是性能下降），或限制用户执行操作的能力。</span><span class="sxs-lookup"><span data-stu-id="ff700-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="ff700-138">仅公开有限数量的命令的运行空间称为受限制的运行空间。</span><span class="sxs-lookup"><span data-stu-id="ff700-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="ff700-139">若要创建受限制的运行空间，请使用[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) [类和 ". 管理类](/dotnet/api/System.Management.Automation.Runspaces.Runspace)"。</span><span class="sxs-lookup"><span data-stu-id="ff700-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="ff700-140">创建 InitialSessionState 对象</span><span class="sxs-lookup"><span data-stu-id="ff700-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="ff700-141">若要创建自定义运行空间，必须首先创建[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象。</span><span class="sxs-lookup"><span data-stu-id="ff700-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="ff700-142">在下面的示例中，我们将使用[RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory)来创建默认的 InitialSessionState 对象之后的运行空间。</span><span class="sxs-lookup"><span data-stu-id="ff700-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="ff700-143">约束运行空间</span><span class="sxs-lookup"><span data-stu-id="ff700-143">Constraining the runspace</span></span>

<span data-ttu-id="ff700-144">在上面的示例中，我们创建了一个默认的[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，该对象加载所有内置核心 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ff700-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="ff700-145">我们还可以调用[CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法来创建一个 InitialSessionState 对象，该对象只会加载 InitialSessionState 管理单元中的命令，而不是。</span><span class="sxs-lookup"><span data-stu-id="ff700-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="ff700-146">若要创建更受限制的运行空间，必须通过调用[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法来创建一个空的 InitialSessionState 对象，然后将命令添加到 InitialSessionState。</span><span class="sxs-lookup"><span data-stu-id="ff700-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="ff700-147">使用仅加载您指定的命令的运行空间可显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="ff700-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="ff700-148">你可以使用[SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)类的方法来定义初始会话状态的 cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="ff700-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="ff700-149">下面的示例创建一个空的初始会话状态，然后定义 `Get-Command`，并将 `Import-Module` 命令添加到初始会话状态。</span><span class="sxs-lookup"><span data-stu-id="ff700-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="ff700-150">然后创建一个受该初始会话状态约束的运行空间，并执行该运行空间中的命令。</span><span class="sxs-lookup"><span data-stu-id="ff700-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="ff700-151">创建初始会话状态。</span><span class="sxs-lookup"><span data-stu-id="ff700-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="ff700-152">定义命令并将其添加到初始会话状态。</span><span class="sxs-lookup"><span data-stu-id="ff700-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="ff700-153">创建并打开运行空间。</span><span class="sxs-lookup"><span data-stu-id="ff700-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="ff700-154">执行命令并显示结果。</span><span class="sxs-lookup"><span data-stu-id="ff700-154">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="ff700-155">运行时，此代码的输出将如下所示。</span><span class="sxs-lookup"><span data-stu-id="ff700-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
