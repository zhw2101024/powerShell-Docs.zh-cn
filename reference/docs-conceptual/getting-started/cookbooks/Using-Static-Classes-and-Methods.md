---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用静态类和方法"
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: fe41c7d6b45564e7b5bc2b922a18587c9745e26d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="55201-103">使用静态类和方法</span><span class="sxs-lookup"><span data-stu-id="55201-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="55201-104">不是所有 .NET Framework 类都可使用 **New-Object** 来创建。</span><span class="sxs-lookup"><span data-stu-id="55201-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="55201-105">例如，如果你尝试使用 **New-Object** 创建 **System.Environment** 或 **System.Math** 对象，你将收到以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="55201-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment
PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="55201-106">之所以发生这些错误，是因为无法从这些类创建新的对象。</span><span class="sxs-lookup"><span data-stu-id="55201-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="55201-107">这些类是不更改状态的方法和属性的引用库。</span><span class="sxs-lookup"><span data-stu-id="55201-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="55201-108">你无需创建这些类，只需要使用它们。</span><span class="sxs-lookup"><span data-stu-id="55201-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="55201-109">这样的类和方法称为*静态类*，因为它们不会被创建、销毁或更改。</span><span class="sxs-lookup"><span data-stu-id="55201-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="55201-110">为了明确这一点，我们将提供静态类的使用示例。</span><span class="sxs-lookup"><span data-stu-id="55201-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="55201-111">使用 System.Environment 获取环境数据</span><span class="sxs-lookup"><span data-stu-id="55201-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="55201-112">通常，在 Windows PowerShell 中使用对象的第一步是使用 Get-Member 找出其所包含的成员。</span><span class="sxs-lookup"><span data-stu-id="55201-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="55201-113">使用静态类，进程会稍有不同，因为实际类不是对象。</span><span class="sxs-lookup"><span data-stu-id="55201-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="55201-114">引用静态的 System.Environment 类</span><span class="sxs-lookup"><span data-stu-id="55201-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="55201-115">可以通过使用方括号将类名称括起来以引用静态类。</span><span class="sxs-lookup"><span data-stu-id="55201-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="55201-116">例如，可以通过在括号内键入名称来引用 **System.Environment**。</span><span class="sxs-lookup"><span data-stu-id="55201-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="55201-117">执行此操作会显示某些泛型类型的信息：</span><span class="sxs-lookup"><span data-stu-id="55201-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="55201-118">正如我们之前提到的，当你使用 **New-Object** 时，Windows PowerShell 会</span><span class="sxs-lookup"><span data-stu-id="55201-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="55201-119">使用 **New-Object**.时输入名称。</span><span class="sxs-lookup"><span data-stu-id="55201-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="55201-120">使用被括号括起来的类型名称时也会发生同样的情况，因此可以将 **\[System.Environment]** 指定为 **\[Environment]**。</span><span class="sxs-lookup"><span data-stu-id="55201-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="55201-121">**System.Environment** 类包含关于当前进程工作环境的一般信息，如果是在 Windows PowerShell 内工作，该进程为 powershell.exe。</span><span class="sxs-lookup"><span data-stu-id="55201-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="55201-122">如果尝试通过键入 **\[System.Environment] | Get-Member** 来查看此类的详细信息，对象类型将报告为 **System.RuntimeType**，而不是 **System.Environment**：</span><span class="sxs-lookup"><span data-stu-id="55201-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="55201-123">若要使用 Get-Member 查看静态成员，请指定 **Static** 参数：</span><span class="sxs-lookup"><span data-stu-id="55201-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="55201-124">现在我们可以从 System.Environment 选择要查看的属性。</span><span class="sxs-lookup"><span data-stu-id="55201-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="55201-125">显示 System.Environment 的静态属性</span><span class="sxs-lookup"><span data-stu-id="55201-125">Displaying Static Properties of System.Environment</span></span>
<span data-ttu-id="55201-126">System.Environment 的属性也是静态的，并且必须使用与常规属性不同的方式进行指定。</span><span class="sxs-lookup"><span data-stu-id="55201-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="55201-127">我们使用 **::** 向 Windows PowerShell 指示我们要使用静态方法或属性。</span><span class="sxs-lookup"><span data-stu-id="55201-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="55201-128">若要查看用于启动 Windows PowerShell 的命令，我们通过键入以下内容来检查 **CommandLine** 属性：</span><span class="sxs-lookup"><span data-stu-id="55201-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="55201-129">若要检查操作系统版本，通过键入以下内容显示 OSVersion 属性：</span><span class="sxs-lookup"><span data-stu-id="55201-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="55201-130">我们可以通过显示 **HasShutdownStarted** 属性来检查计算机是否处于关机进程中：</span><span class="sxs-lookup"><span data-stu-id="55201-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="55201-131">使用 System.Math 做数学</span><span class="sxs-lookup"><span data-stu-id="55201-131">Doing Math with System.Math</span></span>
<span data-ttu-id="55201-132">System.Math 静态类可用于执行某些数学运算。</span><span class="sxs-lookup"><span data-stu-id="55201-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="55201-133">**System.Math** 的大多数重要成员是方法，我们可以用过使用 **Get-Member** 来显示它们。</span><span class="sxs-lookup"><span data-stu-id="55201-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="55201-134">System.Math 的一些方法具有相同的名称，但可以按其参数的类型对其进行区分。</span><span class="sxs-lookup"><span data-stu-id="55201-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="55201-135">键入以下内容来列出 **System.Math** 类的方法。</span><span class="sxs-lookup"><span data-stu-id="55201-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="55201-136">这会显示多种数学方法。</span><span class="sxs-lookup"><span data-stu-id="55201-136">This displays several mathematical methods.</span></span> <span data-ttu-id="55201-137">以下是一个命令列表，展示了某些常用方法的工作原理：</span><span class="sxs-lookup"><span data-stu-id="55201-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```

