---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 创建 .NET 和 COM 对象 (New Object)
ms.openlocfilehash: 6e98a159451bc7da4ba3b37eaeb813eb71590d2b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71325173"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="1fa1b-103">创建 .NET 和 COM 对象 (New-Object)</span><span class="sxs-lookup"><span data-stu-id="1fa1b-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="1fa1b-104">存在具有 .NET Framework 和 COM 接口的软件组件，使用它们可执行许多系统管理任务。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="1fa1b-105">Windows PowerShell 允许你使用这些组件，因此你将不限于执行可通过使用 cmdlet 执行的任务。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="1fa1b-106">Windows PowerShell 初始版本中的许多 cmdlet 对远程计算机无效。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="1fa1b-107">我们将演示如何通过直接从 Windows PowerShell 使用 .NET Framework **System.Diagnostics.EventLog** 类在管理事件日志时绕过此限制。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="1fa1b-108">使用 New-Object 进行事件日志访问</span><span class="sxs-lookup"><span data-stu-id="1fa1b-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="1fa1b-109">.NET Framework 类库包括一个名为 **System.Diagnostics.EventLog** 的类，该类可用于管理事件日志。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="1fa1b-110">可以通过使用具有 **TypeName** 参数的 **New-Object** cmdlet 创建 .NET Framework 类的新实例。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="1fa1b-111">例如，以下命令将创建事件日志引用：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="1fa1b-112">尽管该命令创建了 EventLog 类的实例，但该实例不包含任何数据。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="1fa1b-113">这是因为我们未指定特定的事件日志。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="1fa1b-114">如何获取真正的事件日志？</span><span class="sxs-lookup"><span data-stu-id="1fa1b-114">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="1fa1b-115">将构造函数与 New-Object 一起使用</span><span class="sxs-lookup"><span data-stu-id="1fa1b-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="1fa1b-116">若要引用特定的事件日志，需要指定日志的名称。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="1fa1b-117">**New-Object** 具有 **ArgumentList** 参数。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="1fa1b-118">作为值传递到此形参的实参将由对象的特殊的启动方法使用。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="1fa1b-119">此方法叫做*构造函数*，因为它将用于构造对象。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="1fa1b-120">例如，若要对获取应用程序日志的引用，请指定字符串“Application”作为实参：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="1fa1b-121">由于大多数 .NET Framework 核心类都包含在 System 命名空间中，所以如果 Windows PowerShell 找不到你指定的类型名称的匹配项，它将自动尝试查找你在 System 命名空间中指定的类。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="1fa1b-122">这意味着你可以指定 Diagnostics.EventLog 而不指定 System.Diagnostics.EventLog。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="1fa1b-123">在变量中存储对象</span><span class="sxs-lookup"><span data-stu-id="1fa1b-123">Storing Objects in Variables</span></span>

<span data-ttu-id="1fa1b-124">你可能需要存储对对象的引用，以便在当前的 Shell 中使用。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="1fa1b-125">尽管 Windows PowerShell 允许使用管道执行大量操作，减少了对变量的需求，但有时在变量中存储对对象的引用可以更方便地操纵这些对象。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="1fa1b-126">Windows PowerShell 允许你创建实质上是命名对象的变量。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="1fa1b-127">来自任何有效 Windows PowerShell 命令的输出都可以存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="1fa1b-128">变量名始终以 $ 开头。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-128">Variable names always begin with $.</span></span> <span data-ttu-id="1fa1b-129">如果想要将应用程序日志引用存储在名为 $AppLog 的变量中，请键入该变量的名称，后跟一个等号，然后键入用于创建应用程序日志对象的命令：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="1fa1b-130">如果随后键入 $AppLog，你将可以看到它包含应用程序日志：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="1fa1b-131">使用 New-Object 访问远程事件日志</span><span class="sxs-lookup"><span data-stu-id="1fa1b-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="1fa1b-132">上一节中使用的命令以本地计算机为目标；**Get-EventLog** cmdlet 可做到这一点。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="1fa1b-133">若要访问远程计算机上的应用程序日志，必须同时将日志名称和计算机名称（或 IP 地址）作为参数提供。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="1fa1b-134">我们已经有了对存储在 $RemoteAppLog 变量中的事件日志的引用，那么可以对它执行什么任务呢？</span><span class="sxs-lookup"><span data-stu-id="1fa1b-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="1fa1b-135">使用对象方法清除事件日志</span><span class="sxs-lookup"><span data-stu-id="1fa1b-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="1fa1b-136">对象通常具有可调用以执行任务的方法。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="1fa1b-137">可以使用 **Get-Member** 来显示与对象关联的方法。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="1fa1b-138">下面的命令和已选的输出将显示 EventLog 类的一些方法：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="1fa1b-139">**Clear()** 方法可以用于清除事件日志。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="1fa1b-140">调用方法时，即使该方法不需要参数，也必须始终在方法名称后紧跟括号。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="1fa1b-141">这使得 Windows PowerShell 方法能够区分该方法和具有相同名称的潜在属性。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="1fa1b-142">键入以下命令以调用 **Clear** 方法：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="1fa1b-143">键入以下命令以显示日志。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-143">Type the following to display the log.</span></span> <span data-ttu-id="1fa1b-144">你将看到事件日志已清除，并且现在有 0 个条目而不是 262 个：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="1fa1b-145">使用 New-Object 创建 COM 对象</span><span class="sxs-lookup"><span data-stu-id="1fa1b-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="1fa1b-146">可以使用 **New-Object** 来处理组件对象模型 (COM) 组件。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="1fa1b-147">组件的范围从 Windows 脚本宿主 (WSH) 包含的各种库到 ActiveX 应用程序（如大多数系统上安装的 Internet Explorer）。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="1fa1b-148">**New-Object** 使用 .NET Framework 运行时可调用的包装器创建 COM 对象，因此调用 COM 对象时它与 .NET Framework 具有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="1fa1b-149">若要创建 COM 对象，需要为 **ComObject** 参数指定要使用的 COM 类的编程标识符（或 *ProgId*）。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="1fa1b-150">COM 用途限制的全面讨论和确定系统上可用的 ProgId 已超出本用户指南的范围，但来自环境的大多数已知对象（如 WSH）都可在 Windows PowerShell 内使用。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="1fa1b-151">可以通过指定以下 progid 来创建 WSH 对象：WScript.Shell  、WScript.Network  、Scripting.Dictionary  和 Scripting.FileSystemObject  。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="1fa1b-152">以下命令将创建这些对象：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="1fa1b-153">尽管在 Windows PowerShell 中可通过其他方法使用这些类的大多数功能，但使用 WSH 类执行某些任务（如创建快捷方式）仍更加简单。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="1fa1b-154">使用 WScript.Shell 创建桌面快捷方式</span><span class="sxs-lookup"><span data-stu-id="1fa1b-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="1fa1b-155">可以使用 COM 对象快速执行的一个任务是创建快捷方式。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="1fa1b-156">假设你想要在桌面上创建链接到 Windows PowerShell 主文件夹的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="1fa1b-157">首先需要创建对 **WScript.Shell** 的引用，我们会将其存储在名为 **$WshShell** 的变量中：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="1fa1b-158">Ge-Member 可用于 COM 对象，因此你可以通过键入以下内容浏览对象的成员：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="1fa1b-159">**Get-Member** 具有可选 **InputObject** 参数，你可以使用这个参数而不使用管道为 **Get-Member** 提供输入。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="1fa1b-160">如果改用命令 **Get-Member-InputObject $WshShell**，你会得到与如上所示相同的输出。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="1fa1b-161">如果使用 **InputObject**，它将视其参数为单个项。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="1fa1b-162">这意味着，如果变量中有几个对象，那么 **Get-Member** 会将它们视为一个对象数组。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="1fa1b-163">例如：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="1fa1b-164">**WScript.Shell CreateShortcut** 方法接受单个参数，即要创建的快捷方式文件的路径。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="1fa1b-165">我们可以键入桌面的完整路径，但还有更简单的方法。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="1fa1b-166">桌面通常由当前用户的主文件夹内名为 Desktop 的文件夹表示。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="1fa1b-167">Windows PowerShell 具有变量 **$Home**，它包含此文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="1fa1b-168">我们可以通过使用此变量指定主文件夹的路径，然后通过键入以下内容添加 Desktop 文件夹的名称和要创建的快捷方式的名称：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="1fa1b-169">当你在双引号内使用外观类似变量名称的项时，Windows PowerShell 将尝试替换匹配的值。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="1fa1b-170">如果使用单引号，Windows PowerShell 将不会替换该变量值。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="1fa1b-171">例如，请尝试键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="1fa1b-172">我们现在有一个名为 **$lnk** 的变量，其中包含新的快捷方式引用。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="1fa1b-173">如果想要查看其成员，你可以通过管道将它传递到 **Get-Member**。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="1fa1b-174">下面的输出显示了完成创建快捷方式所需使用的成员：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="1fa1b-175">我们需要指定 **TargetPath**（它是 Windows PowerShell 的应用程序文件夹），然后通过调用 **Save** 方法保存快捷方式 **$lnk**。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="1fa1b-176">Windows PowerShell 应用程序文件夹路径存储在变量 **$PSHome** 中，因此我们可以通过键入以下内容执行此操作：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="1fa1b-177">从 Windows PowerShell 使用 Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="1fa1b-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="1fa1b-178">使用 COM 可以使许多应用程序（包括 Microsoft Office 系列应用程序和 Internet Explorer）自动执行。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="1fa1b-179">Internet Explorer 阐明了有关使用基于 COM 的应用程序的一些典型方法和涉及的问题。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="1fa1b-180">通过指定 Internet Explorer ProgId **InternetExplorer.Application** 创建 Internet Explorer 实例：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="1fa1b-181">此命令将启动 Internet Explorer，但不显示它。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="1fa1b-182">如果你键入 Get-Process，将可以看到名为 iexplore 的进程正在运行。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="1fa1b-183">事实上，如果你退出 Windows PowerShell，该过程将继续运行。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="1fa1b-184">必须重启计算机或使用任务管理器等工具结束 iexplore 进程。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="1fa1b-185">作为独立进程（通常称为 *ActiveX 可执行文件*）启动的 COM 对象启动时可能显示也可能不显示用户界面窗口。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="1fa1b-186">如果它们创建而不显示窗口（如 Internet Explorer），则焦点通常会移到 Windows 桌面，这时必须显示窗口才能与其进行交互。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="1fa1b-187">通过键入 **$ie | Get-Member**，可以查看 Internet Explorer 的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="1fa1b-188">若要查看 Internet Explorer 窗口，请通过键入以下内容将 Visible 属性设置为 $true：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="1fa1b-189">然后可以通过使用 Navigate 方法导航到特定的 Web 地址：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("https://devblogs.microsoft.com/scripting/")
```

<span data-ttu-id="1fa1b-190">使用 Internet Explorer 对象模型的其他成员，可以从网页中检索文本内容。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="1fa1b-191">下面的命令将在当前网页的正文中显示 HTML 文本：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="1fa1b-192">若要从 PowerShell 内部关闭 Internet Explorer，请调用其 Quit() 方法：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="1fa1b-193">这将强制其关闭。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-193">This will force it to close.</span></span> <span data-ttu-id="1fa1b-194">尽管 $ie 变量仍然显示为 COM 对象，但它将不再包含有效引用。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="1fa1b-195">如果你尝试使用它，你将收到一个自动化错误：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="1fa1b-196">你可以使用 $ie = $null 等命令删除剩余的引用，或通过键入以下内容完全删除该变量：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="1fa1b-197">删除对 ActiveX 可执行文件的引用时，它会退出还是继续运行没有通用标准。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="1fa1b-198">具体取决于不同情况（如应用程序是否可见、已编辑的文档是否正在其中运行甚至 Windows PowerShell 是否仍在运行），应用程序可能退出也可能不退出。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="1fa1b-199">因此，应该为想要在 Windows PowerShell 中使用的每个 ActiveX 可执行文件测试终止行为。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="1fa1b-200">获取有关 .NET Framework 包装的 COM 对象的警告</span><span class="sxs-lookup"><span data-stu-id="1fa1b-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="1fa1b-201">在某些情况下，COM 对象可能具有相关联的 .NET Framework *运行时可调用包装器*（或称 RCW），它将由 **New-Object** 使用。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="1fa1b-202">因为 RCW 的行为可能与普通 COM 对象的行为不同，所以 **New-Object** 具有 **Strict** 参数，它将对访问 RCW 进行警告。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="1fa1b-203">如果指定 **Strict** 参数然后创建使用 RCW 的 COM 对象，你会收到一条警告消息：</span><span class="sxs-lookup"><span data-stu-id="1fa1b-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="1fa1b-204">尽管仍将创建该对象，但将警告你它不是标准 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="1fa1b-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>
