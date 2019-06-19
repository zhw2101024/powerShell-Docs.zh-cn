---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用注册表条目
ms.openlocfilehash: c1fd6f57f13240eb2039f2d5756796678800aee0
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030728"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="9a445-103">使用注册表条目</span><span class="sxs-lookup"><span data-stu-id="9a445-103">Working with Registry Entries</span></span>

<span data-ttu-id="9a445-104">因为注册表条目是项的属性而无法直接浏览，因此我们在使用它们时需要采取略有不同的方式。</span><span class="sxs-lookup"><span data-stu-id="9a445-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="9a445-105">列出注册表条目</span><span class="sxs-lookup"><span data-stu-id="9a445-105">Listing Registry Entries</span></span>

<span data-ttu-id="9a445-106">可采用许多不同的方法检查注册表条目。</span><span class="sxs-lookup"><span data-stu-id="9a445-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="9a445-107">最简单的方法是获取与某个项相关联的属性名称。</span><span class="sxs-lookup"><span data-stu-id="9a445-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="9a445-108">例如，若要查看注册表项 `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion` 中的条目名称，请使用 `Get-Item`。</span><span class="sxs-lookup"><span data-stu-id="9a445-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="9a445-109">注册表项具有一个通用名称为“Property”的属性，它是项中的注册表条目的列表。</span><span class="sxs-lookup"><span data-stu-id="9a445-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="9a445-110">以下命令选择 Property 属性并扩展这些项，以便它们可在列表中显示：</span><span class="sxs-lookup"><span data-stu-id="9a445-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="9a445-111">若要在可读性更强的窗体中查看注册表条目，请使用 `Get-ItemProperty`：</span><span class="sxs-lookup"><span data-stu-id="9a445-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="9a445-112">该项的 Windows PowerShell 相关的属性全都带有“PS”前缀，例如 **PSPath**、**PSParentPath**、**PSChildName** 和 **PSProvider**。</span><span class="sxs-lookup"><span data-stu-id="9a445-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="9a445-113">可以将 `*.*` 表示法用于引用当前位置。</span><span class="sxs-lookup"><span data-stu-id="9a445-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="9a445-114">可以先使用 `Set-Location` 以更改为 CurrentVersion  注册表容器：</span><span class="sxs-lookup"><span data-stu-id="9a445-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="9a445-115">另外，可以将内置 HKLM PSDrive 与 `Set-Location` 结合使用：</span><span class="sxs-lookup"><span data-stu-id="9a445-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="9a445-116">然后，可以将 `*.*` 表示法用于当前位置以列出属性，而无需指定完整路径：</span><span class="sxs-lookup"><span data-stu-id="9a445-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="9a445-117">路径扩展的工作方式与其在文件系统中的工作方式相同，因此在此位置中，你可以通过使用 `Get-ItemProperty -Path ..\Help` 来获取 `HKLM:\SOFTWARE\Microsoft\Windows\Help` 的 ItemProperty  列表。</span><span class="sxs-lookup"><span data-stu-id="9a445-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="9a445-118">获取单个注册表条目</span><span class="sxs-lookup"><span data-stu-id="9a445-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="9a445-119">如果你希望在注册表项中检索特定条目，可以使用几种可能的方法之一。</span><span class="sxs-lookup"><span data-stu-id="9a445-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="9a445-120">本示例查找 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion` 中的 DevicePath  的值。</span><span class="sxs-lookup"><span data-stu-id="9a445-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="9a445-121">通过使用 `Get-ItemProperty`，可使用 Path  参数指定键的名称，使用 Name  参数指定 DevicePath  条目的名称。</span><span class="sxs-lookup"><span data-stu-id="9a445-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="9a445-122">此命令返回标准 Windows PowerShell 属性以及 **DevicePath** 属性。</span><span class="sxs-lookup"><span data-stu-id="9a445-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="9a445-123">尽管 `Get-ItemProperty` 具有 Filter  、Include  和 Exclude  参数，但它们无法用于按属性名称进行筛选。</span><span class="sxs-lookup"><span data-stu-id="9a445-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="9a445-124">这些参数引用注册表项（即项路径），而不引用注册表条目。</span><span class="sxs-lookup"><span data-stu-id="9a445-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="9a445-125">注册表条目是项属性。</span><span class="sxs-lookup"><span data-stu-id="9a445-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="9a445-126">另一种方法是使用 Reg.exe 命令行工具。</span><span class="sxs-lookup"><span data-stu-id="9a445-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="9a445-127">有关 reg.exe 的帮助，请在命令提示符下键入 `reg.exe /?`。</span><span class="sxs-lookup"><span data-stu-id="9a445-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="9a445-128">若要查找 DevicePath 条目，请使用 reg.exe，如以下命令中所示：</span><span class="sxs-lookup"><span data-stu-id="9a445-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="9a445-129">还可以使用 WshShell  COM 对象查找某些注册表条目，尽管此方法对大型二进制数据或包含诸如“\\”字符的注册表条目名称不起作用也是如此。</span><span class="sxs-lookup"><span data-stu-id="9a445-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="9a445-130">将属性名称附加到带有 \\ 分隔符的项路径：</span><span class="sxs-lookup"><span data-stu-id="9a445-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="9a445-131">获取单个注册表条目</span><span class="sxs-lookup"><span data-stu-id="9a445-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="9a445-132">如果希望在注册表项中更改特定条目，可以使用几种可能的方法之一。</span><span class="sxs-lookup"><span data-stu-id="9a445-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="9a445-133">此示例修改 `HKEY_CURRENT_USER\Environment` 下的 Path  条目。</span><span class="sxs-lookup"><span data-stu-id="9a445-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="9a445-134">Path  条目指定在哪里可以找到可执行文件。</span><span class="sxs-lookup"><span data-stu-id="9a445-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="9a445-135">使用 `Get-ItemProperty` 检索 Path  条目的当前值。</span><span class="sxs-lookup"><span data-stu-id="9a445-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="9a445-136">添加新值，将其与 `;` 分离。</span><span class="sxs-lookup"><span data-stu-id="9a445-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="9a445-137">将 `Set-ItemProperty` 与指定的键、条目名称和值结合使用，以修改注册表条目。</span><span class="sxs-lookup"><span data-stu-id="9a445-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="9a445-138">尽管 `Set-ItemProperty` 具有 Filter  、Include  和 Exclude  参数，但它们无法用于按属性名称进行筛选。</span><span class="sxs-lookup"><span data-stu-id="9a445-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="9a445-139">这些参数引用注册表项（即项路径），而不引用注册表条目（即项属性）。</span><span class="sxs-lookup"><span data-stu-id="9a445-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="9a445-140">另一种方法是使用 Reg.exe 命令行工具。</span><span class="sxs-lookup"><span data-stu-id="9a445-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="9a445-141">有关 reg.exe 的帮助，请键入 **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="9a445-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="9a445-142">。</span><span class="sxs-lookup"><span data-stu-id="9a445-142">at a command prompt.</span></span>

<span data-ttu-id="9a445-143">下面的示例通过删除在上面的示例添加的路径来更改 Path  条目。</span><span class="sxs-lookup"><span data-stu-id="9a445-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="9a445-144">`Get-ItemProperty` 仍可用于检索当前值，以避免必须解析从 `reg query` 返回的字符串。</span><span class="sxs-lookup"><span data-stu-id="9a445-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="9a445-145">SubString  和 LastIndexOf  方法用于检索添加到 Path  条目的最后一个路径。</span><span class="sxs-lookup"><span data-stu-id="9a445-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="9a445-146">创建新注册表条目</span><span class="sxs-lookup"><span data-stu-id="9a445-146">Creating New Registry Entries</span></span>

<span data-ttu-id="9a445-147">若要将名为“PowerShellPath”的新条目添加到 CurrentVersion  键，请将 `New-ItemProperty` 与该键的路径、条目名称和条目的值一起使用。</span><span class="sxs-lookup"><span data-stu-id="9a445-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="9a445-148">对于此示例，我们将采用 Windows PowerShell 变量 `$PSHome` 的值，该变量可存储 Windows PowerShell 的安装目录的路径。</span><span class="sxs-lookup"><span data-stu-id="9a445-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="9a445-149">你可以通过使用以下命令来将新条目添加到项，该命令还会返回有关新条目的信息：</span><span class="sxs-lookup"><span data-stu-id="9a445-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="9a445-150">**PropertyType** 必须是以下表格中的 **Microsoft.Win32.RegistryValueKind** 枚举成员的名称：</span><span class="sxs-lookup"><span data-stu-id="9a445-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="9a445-151">PropertyType 值</span><span class="sxs-lookup"><span data-stu-id="9a445-151">PropertyType Value</span></span>|<span data-ttu-id="9a445-152">含义</span><span class="sxs-lookup"><span data-stu-id="9a445-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="9a445-153">Binary</span><span class="sxs-lookup"><span data-stu-id="9a445-153">Binary</span></span>|<span data-ttu-id="9a445-154">二进制数据</span><span class="sxs-lookup"><span data-stu-id="9a445-154">Binary data</span></span>|
|<span data-ttu-id="9a445-155">DWord</span><span class="sxs-lookup"><span data-stu-id="9a445-155">DWord</span></span>|<span data-ttu-id="9a445-156">一个数字，类型为有效的 UInt32</span><span class="sxs-lookup"><span data-stu-id="9a445-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="9a445-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="9a445-157">ExpandString</span></span>|<span data-ttu-id="9a445-158">一个字符串，可包含动态扩展的环境变量</span><span class="sxs-lookup"><span data-stu-id="9a445-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="9a445-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="9a445-159">MultiString</span></span>|<span data-ttu-id="9a445-160">一个多行字符串</span><span class="sxs-lookup"><span data-stu-id="9a445-160">A multiline string</span></span>|
|<span data-ttu-id="9a445-161">字符串</span><span class="sxs-lookup"><span data-stu-id="9a445-161">String</span></span>|<span data-ttu-id="9a445-162">任意字符串值</span><span class="sxs-lookup"><span data-stu-id="9a445-162">Any string value</span></span>|
|<span data-ttu-id="9a445-163">QWord</span><span class="sxs-lookup"><span data-stu-id="9a445-163">QWord</span></span>|<span data-ttu-id="9a445-164">8 字节的二进制数据</span><span class="sxs-lookup"><span data-stu-id="9a445-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="9a445-165">你可以通过为 **Path** 参数指定一组值来将注册表条目添加到多个位置：</span><span class="sxs-lookup"><span data-stu-id="9a445-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="9a445-166">还可以替代预先存在的注册表条目值，方法是将 Force  参数添加到任何 `New-ItemProperty` 命令。</span><span class="sxs-lookup"><span data-stu-id="9a445-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="9a445-167">重命名注册表条目</span><span class="sxs-lookup"><span data-stu-id="9a445-167">Renaming Registry Entries</span></span>

<span data-ttu-id="9a445-168">若要将 PowerShellPath  条目重命名为“PSHome”，请使用 `Rename-ItemProperty`：</span><span class="sxs-lookup"><span data-stu-id="9a445-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="9a445-169">若要显示重命名的值，请将 **PassThru** 参数添加到该命令。</span><span class="sxs-lookup"><span data-stu-id="9a445-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="9a445-170">删除注册表条目</span><span class="sxs-lookup"><span data-stu-id="9a445-170">Deleting Registry Entries</span></span>

<span data-ttu-id="9a445-171">若要删除 PSHome 和 PowerShellPath 注册表条目，请使用 `Remove-ItemProperty`：</span><span class="sxs-lookup"><span data-stu-id="9a445-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
