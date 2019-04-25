---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.1 中的 Bug 修复
ms.openlocfilehash: f53fc40b79a3906ac2025b0eff342c0705b82655
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085042"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="32f62-103">WMF 5.1 中的 Bug 修复</span><span class="sxs-lookup"><span data-stu-id="32f62-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="32f62-104">Bug 修复</span><span class="sxs-lookup"><span data-stu-id="32f62-104">Bug fixes</span></span>

<span data-ttu-id="32f62-105">WMF 5.1 中修复了以下值得注意的 bug：</span><span class="sxs-lookup"><span data-stu-id="32f62-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="32f62-106">模块自动发现完全遵循 `$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="32f62-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span>

<span data-ttu-id="32f62-107">WMF 3 中引入了模块自动发现（调用命令时自动加载模块而无需使用显式 Import-Module）。</span><span class="sxs-lookup"><span data-stu-id="32f62-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="32f62-108">引入时，PowerShell 会在使用 `$env:PSModulePath` 之前检查 `$PSHome\Modules` 中的命令。</span><span class="sxs-lookup"><span data-stu-id="32f62-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="32f62-109">WMF 5.1 将此行为更改为完全遵循 `$env:PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="32f62-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="32f62-110">这允许定义 PowerShell 提供的命令（例如 `Get-ChildItem`）的用户创作模块自动加载并正确重写内置命令。</span><span class="sxs-lookup"><span data-stu-id="32f62-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="32f62-111">文件重定向不再硬编码 `-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="32f62-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span>

<span data-ttu-id="32f62-112">在所有以前版本的 PowerShell 中，无法控制文件重定向运算符使用的文件编码（例如 `Get-ChildItem > out.txt`），因为 PowerShell 添加了 `-Encoding Unicode`。</span><span class="sxs-lookup"><span data-stu-id="32f62-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="32f62-113">从 WMF 5.1 开始，现在可以通过设置 `$PSDefaultParameterValues` 来更改重定向的文件编码：</span><span class="sxs-lookup"><span data-stu-id="32f62-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="32f62-114">修复了 `System.Reflection.TypeInfo` 成员访问中的回归</span><span class="sxs-lookup"><span data-stu-id="32f62-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span>

<span data-ttu-id="32f62-115">WMF 5.0 中引入的回归会破坏 `System.Reflection.RuntimeType` 的成员访问（例如 `[int].ImplementedInterfaces`）。</span><span class="sxs-lookup"><span data-stu-id="32f62-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="32f62-116">WMF 5.1 中已修复了此 bug。</span><span class="sxs-lookup"><span data-stu-id="32f62-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="32f62-117">修复了与 COM 对象相关的一些问题</span><span class="sxs-lookup"><span data-stu-id="32f62-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="32f62-118">WMF 5.0 引入了一个新 COM 绑定器，用于对 COM 对象调用方法和访问 COM 对象的属性。</span><span class="sxs-lookup"><span data-stu-id="32f62-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="32f62-119">这一新绑定器显著提高了性能，但是同样引入了一些 bug，在 WMF 5.1 中已修复了它们。</span><span class="sxs-lookup"><span data-stu-id="32f62-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="32f62-120">参数转换并不总是正确执行</span><span class="sxs-lookup"><span data-stu-id="32f62-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="32f62-121">在以下示例中：</span><span class="sxs-lookup"><span data-stu-id="32f62-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="32f62-122">SendKeys 方法需要一个字符串，但是 PowerShell 未将字符转换为字符串，而是将转换延迟到 IDispatch::Invoke，后者使用 VariantChangeType 进行转换，在此示例中，这导致发送键“1”、“7”和“3”而不是预期的 Volume.Mute 键。</span><span class="sxs-lookup"><span data-stu-id="32f62-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="32f62-123">可枚举 COM 对象并不总是正确处理</span><span class="sxs-lookup"><span data-stu-id="32f62-123">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="32f62-124">PowerShell 通常可枚举大多数可枚举对象，但是在 WMF 5.0 中引入的回归会阻止实现 IEnumerable 的 COM 对象的枚举。</span><span class="sxs-lookup"><span data-stu-id="32f62-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="32f62-125">例如：</span><span class="sxs-lookup"><span data-stu-id="32f62-125">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="32f62-126">在上面的示例中，WMF 5.0 错误地将 Scripting.Dictionary 写入管道，而不是枚举键/值对。</span><span class="sxs-lookup"><span data-stu-id="32f62-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="32f62-127">此更改还解决了 [Connect 上的问题 1752224](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="32f62-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="32f62-128">不允许在类中使用 `[ordered]`</span><span class="sxs-lookup"><span data-stu-id="32f62-128">`[ordered]` was not allowed inside classes</span></span>

<span data-ttu-id="32f62-129">WMF 5.0 引入了会对类中使用的类型文本进行验证的类。</span><span class="sxs-lookup"><span data-stu-id="32f62-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="32f62-130">`[ordered]` 类似于类型文本，但不是真正的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="32f62-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="32f62-131">WMF 5.0 错误地对类中的 `[ordered]` 报告错误：</span><span class="sxs-lookup"><span data-stu-id="32f62-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="32f62-132">有关涉及多个版本的主题的帮助不起作用</span><span class="sxs-lookup"><span data-stu-id="32f62-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="32f62-133">在 WMF 5.1 之前，如果安装了模块的多个版本，并且它们都共享帮助主题（例如 about_PSReadline），则 `help about_PSReadline` 会返回多个主题，没有明确的方法来查看实际帮助。</span><span class="sxs-lookup"><span data-stu-id="32f62-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="32f62-134">WMF 5.1 通过返回有关最新版本主题的帮助来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="32f62-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="32f62-135">`Get-Help` 不提供某种方法，这种方法用于指定希望获取相关帮助的版本。</span><span class="sxs-lookup"><span data-stu-id="32f62-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="32f62-136">若要解决此问题，请导航到模块目录，然后使用工具（如自己喜爱的编辑器）来直接查看帮助。</span><span class="sxs-lookup"><span data-stu-id="32f62-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="32f62-137">从 STDIN 中读取的 powershell.exe 停止运行</span><span class="sxs-lookup"><span data-stu-id="32f62-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="32f62-138">客户使用本机应用中的 `powershell -command -` 来执行通过 STDIN 传入脚本的 PowerShell。遗憾的是，由于控制台主机中的其他变更，导致此操作中断。</span><span class="sxs-lookup"><span data-stu-id="32f62-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="32f62-139">powershell.exe 在启动时形成 CPU 使用率峰值</span><span class="sxs-lookup"><span data-stu-id="32f62-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="32f62-140">PowerShell 使用 WMI 查询来检查是否是通过组策略启动，以免导致延迟登录。</span><span class="sxs-lookup"><span data-stu-id="32f62-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="32f62-141">WMI 查询最终将 tzres.mui.dll 注入系统中的每个进程，因为 WMI Win32_Process 类会尝试检索本地时区信息。</span><span class="sxs-lookup"><span data-stu-id="32f62-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="32f62-142">这会导致 wmiprvse（WMI 提供程序主机）出现 CPU 大峰值。</span><span class="sxs-lookup"><span data-stu-id="32f62-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="32f62-143">解决方法是使用 Win32 API 调用来获取相同信息，而不是使用 WMI。</span><span class="sxs-lookup"><span data-stu-id="32f62-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
