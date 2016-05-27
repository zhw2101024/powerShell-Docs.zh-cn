---
title:  创建 .NET 和 COM 对象 (New Object) 
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  2057b113-efeb-465e-8b44-da2f20dbf603
---

# 创建 .NET 和 COM 对象 (New-Object)
存在具有 .NET Framework 和 COM 接口的软件组件，使用它们可执行许多系统管理任务。 Windows PowerShell 允许你使用这些组件，因此你将不限于执行可通过使用 cmdlet 执行的任务。 Windows PowerShell 初始版本中的许多 cmdlet 对远程计算机无效。 我们将演示如何通过直接从 Windows PowerShell 使用 .NET Framework **System.Diagnostics.EventLog** 类在管理事件日志时绕过此限制。

### 使用 New-Object 进行事件日志访问
.NET Framework 类库包括一个名为 **System.Diagnostics.EventLog** 的类，该类可用于管理事件日志。 可以通过使用具有 **TypeName** 参数的 **New-Object** cmdlet 创建 .NET Framework 类的新实例。 例如，以下命令将创建事件日志引用：

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

尽管该命令创建了 EventLog 类的实例，但该实例不包含任何数据。 这是因为我们未指定特定的事件日志。 如何获取真正的事件日志？

#### 将构造函数与 New-Object 一起使用
若要引用特定的事件日志，需要指定日志的名称。 **New-Object** 具有 **ArgumentList** 参数。 作为值传递到此形参的实参将由对象的特殊的启动方法使用。 此方法叫做*构造函数*，因为它将用于构造对象。 例如，若要对获取应用程序日志的引用，请指定字符串“Application”作为实参：

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> 由于大多数 .NET Framework 核心类都包含在 System 命名空间中，所以如果 Windows PowerShell 找不到你指定的类型名称的匹配项，它将自动尝试查找你在 System 命名空间中指定的类。 这意味着你可以指定 Diagnostics.EventLog 而不指定 System.Diagnostics.EventLog。

#### 在变量中存储对象
你可能需要存储对对象的引用，以便在当前的 Shell 中使用。 尽管 Windows PowerShell 允许使用管道执行大量操作，减少了对变量的需求，但有时在变量中存储对对象的引用可以更方便地操纵这些对象。

Windows PowerShell 允许你创建实质上是命名对象的变量。 来自任何有效 Windows PowerShell 命令的输出都可以存储在变量中。 变量名始终以 $ 开头。 如果想要将应用程序日志引用存储在名为 $AppLog 的变量中，请键入该变量的名称，后跟一个等号，然后键入用于创建应用程序日志对象的命令：

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

如果随后键入 $AppLog，你将可以看到它包含应用程序日志：

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### 使用 New-Object 访问远程事件日志
上一节中使用的命令以本地计算机为目标；**Get-EventLog** cmdlet 可做到这一点。 若要访问远程计算机上的应用程序日志，必须同时将日志名称和计算机名称（或 IP 地址）作为参数提供。

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

我们已经有了对存储在 $RemoteAppLog 变量中的事件日志的引用，那么可以对它执行什么任务呢？

#### 使用对象方法清除事件日志
对象通常具有可调用以执行任务的方法。 可以使用 **Get-Member** 来显示与对象关联的方法。 下面的命令和已选的输出将显示 EventLog 类的一些方法：

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

**Clear()** 方法可以用于清除事件日志。 调用方法时，即使该方法不需要参数，也必须始终在方法名称后紧跟括号。 这使得 Windows PowerShell 方法能够区分该方法和具有相同名称的潜在属性。 键入以下命令以调用 **Clear** 方法：

```
PS> $RemoteAppLog.Clear()
```

键入以下命令以显示日志。 你将看到事件日志已清除，并且现在有 0 个条目而不是 262 个：

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### 使用 New-Object 创建 COM 对象
可以使用 **New-Object** 来处理组件对象模型 (COM) 组件。 组件的范围从 Windows 脚本宿主 (WSH) 包含的各种库到 ActiveX 应用程序（如大多数系统上安装的 Internet Explorer）。

**New-Object** 使用 .NET Framework 运行时可调用的包装器创建 COM 对象，因此调用 COM 对象时它与 .NET Framework 具有相同的限制。 若要创建 COM 对象，需要为 **ComObject** 参数指定要使用的 COM 类的编程标识符（或 *ProgId*）。 COM 用途限制的全面讨论和确定系统上可用的 ProgId 已超出本用户指南的范围，但来自环境的大多数已知对象（如 WSH）都可在 Windows PowerShell 内使用。

可通过指定以下 progid 来创建 WSH 对象：**WScript.Shell**、**WScript.Network**、**Scripting.Dictionary** 和 **Scripting.FileSystemObject**。 以下命令将创建这些对象：

```
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

尽管在 Windows PowerShell 中可通过其他方法使用这些类的大多数功能，但使用 WSH 类执行某些任务（如创建快捷方式）仍更加简单。

### 使用 WScript.Shell 创建桌面快捷方式
可以使用 COM 对象快速执行的一个任务是创建快捷方式。 假设你想要在桌面上创建链接到 Windows PowerShell 主文件夹的快捷方式。 首先需要创建对 **WScript.Shell** 的引用，我们会将其存储在名为 **$WshShell** 的变量中：

```
$WshShell = New-Object -ComObject WScript.Shell
```

Ge-Member 可用于 COM 对象，因此你可以通过键入以下内容浏览对象的成员：

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** 具有可选 **InputObject** 参数，你可以使用这个参数而不使用管道为 **Get-Member** 提供输入。 如果改用命令 **Get-Member-InputObject $WshShell**，你会得到与如上所示相同的输出。 如果使用 **InputObject**，它将视其参数为单个项。 这意味着，如果变量中有几个对象，那么 **Get-Member** 会将它们视为一个对象数组。 例如：

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

**WScript.Shell CreateShortcut** 方法接受单个参数，即要创建的快捷方式文件的路径。 我们可以键入桌面的完整路径，但还有更简单的方法。 桌面通常由当前用户的主文件夹内名为 Desktop 的文件夹表示。 Windows PowerShell 具有变量 **$Home**，它包含此文件夹的路径。 我们可以通过使用此变量指定主文件夹的路径，然后通过键入以下内容添加 Desktop 文件夹的名称和要创建的快捷方式的名称：

```
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

当你在双引号内使用外观类似变量名称的项时，Windows PowerShell 将尝试替换匹配的值。 如果使用单引号，Windows PowerShell 将不会替换该变量值。 例如，请尝试键入以下命令：

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

我们现在有一个名为 **$lnk** 的变量，其中包含新的快捷方式引用。 如果想要查看其成员，你可以通过管道将它传递到 **Get-Member**。 下面的输出显示了完成创建快捷方式所需使用的成员：

<pre>PS> $lnk | Get-Member TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b} Name             MemberType   Definition ----             ----------   ---------- ...Save             Method       void Save () ...TargetPath       Property     string TargetPath () {get} {set} ...</pre>

我们需要指定 **TargetPath**（它是 Windows PowerShell 的应用程序文件夹），然后通过调用 **Save** 方法保存快捷方式 **$lnk**。 Windows PowerShell 应用程序文件夹路径存储在变量 **$PSHome** 中，因此我们可以通过键入以下内容执行此操作：

<pre>$lnk.TargetPath = $PSHome $lnk.Save()</pre>

### 从 Windows PowerShell 使用 Internet Explorer
使用 COM 可以使许多应用程序（包括 Microsoft Office 系列应用程序和 Internet Explorer）自动执行。 Internet Explorer 阐明了有关使用基于 COM 的应用程序的一些典型方法和涉及的问题。

通过指定 Internet Explorer ProgId **InternetExplorer.Application** 创建 Internet Explorer 实例：

```
$ie = New-Object -ComObject InternetExplorer.Application
```

此命令将启动 Internet Explorer，但不显示它。 如果你键入 Get-Process，将可以看到名为 iexplore 的进程正在运行。 事实上，如果你退出 Windows PowerShell，该过程将继续运行。 必须重启计算机或使用任务管理器等工具结束 iexplore 进程。

> [!NOTE]
> 作为独立进程（通常称为 *ActiveX 可执行文件*）启动的 COM 对象启动时可能显示也可能不显示用户界面窗口。 如果它们创建而不显示窗口（如 Internet Explorer），则焦点通常会移到 Windows 桌面，这时必须显示窗口才能与其进行交互。

通过键入 **$ie | Get-Membe**，可以查看 Internet Explorer 的属性和方法。 若要查看 Internet Explorer 窗口，请通过键入以下内容将 Visible 属性设置为 $true：

```
$ie.Visible = $true
```

然后可以通过使用 Navigate 方法导航到特定的 Web 地址：

```
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

使用 Internet Explorer 对象模型的其他成员，可以从网页中检索文本内容。 下面的命令将在当前网页的正文中显示 HTML 文本：

```
$ie.Document.Body.InnerText
```

若要从 PowerShell 内部关闭 Internet Explorer，请调用其 Quit() 方法：

```
$ie.Quit()
```

这将强制其关闭。 尽管 $ie 变量仍然显示为 COM 对象，但它将不再包含有效引用。 如果你尝试使用它，你将收到一个自动化错误：

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

你可以使用 $ie = $null 等命令删除剩余的引用，或通过键入以下内容完全删除该变量：

```
Remove-Variable ie
```

> [!NOTE]
> 删除对 ActiveX 可执行文件的引用时，它会退出还是继续运行没有通用标准。 具体取决于不同情况（如应用程序是否可见、已编辑的文档是否正在其中运行甚至 Windows PowerShell 是否仍在运行），应用程序可能退出也可能不退出。 因此，应该为想要在 Windows PowerShell 中使用的每个 ActiveX 可执行文件测试终止行为。

### 获取有关 .NET Framework 包装的 COM 对象的警告
在某些情况下，COM 对象可能具有相关联的 .NET Framework *运行时可调用包装器*（或称 RCW），它将由 **New-Object** 使用。 因为 RCW 的行为可能与普通 COM 对象的行为不同，所以 **New-Object** 具有 **Strict** 参数，它将对访问 RCW 进行警告。 如果指定 **Strict** 参数然后创建使用 RCW 的 COM 对象，你会收到一条警告消息：

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

尽管仍将创建该对象，但将警告你它不是标准 COM 对象。



<!--HONumber=May16_HO2-->


