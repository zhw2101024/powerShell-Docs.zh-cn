---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用软件安装
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293214"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="0d991-103">使用软件安装</span><span class="sxs-lookup"><span data-stu-id="0d991-103">Working with Software Installations</span></span>

<span data-ttu-id="0d991-104">可以通过 WMI 的 **Win32_Product** 类访问旨在使用 Windows Installer 的应用程序，但当今使用的所有应用程序并非都使用 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="0d991-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="0d991-105">由于 Windows Installer 提供了最广泛的标准技术用于使用可安装的应用程序，因此我们将主要使用这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="0d991-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="0d991-106">使用替代安装例程的应用程序通常不由 Windows Installer 管理。</span><span class="sxs-lookup"><span data-stu-id="0d991-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="0d991-107">用于使用这些应用程序的特定技术将取决于安装程序软件和应用程序开发人员做出的决策。</span><span class="sxs-lookup"><span data-stu-id="0d991-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="0d991-108">通常不能使用此处讨论的技术来管理通过将应用程序文件复制到计算机安装的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0d991-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="0d991-109">你可以使用在“使用文件和文件夹”部分中讨论的技术将这些应用程序作为文件和文件夹进行管理。</span><span class="sxs-lookup"><span data-stu-id="0d991-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="0d991-110">列出 Windows Installer 应用程序</span><span class="sxs-lookup"><span data-stu-id="0d991-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="0d991-111">若要列出随 Windows Installer 一起在本地或远程系统上安装的应用程序，请使用以下简单的 WMI 查询：</span><span class="sxs-lookup"><span data-stu-id="0d991-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="0d991-112">若要将 Win32_Product 对象的所有属性显示到显示屏中，请使用格式设置 cmdlet（例如 Format-List cmdlet）的“Property”参数，值为 \*（全部）。</span><span class="sxs-lookup"><span data-stu-id="0d991-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="0d991-113">或者，可以使用 **Get-WmiObject Filter** 参数仅选择 Microsoft .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="0d991-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="0d991-114">由于此命令中使用的筛选器是 WMI 筛选器，它使用 WMI 查询语言 (WQL) 语法，而不是 Windows PowerShell 语法。</span><span class="sxs-lookup"><span data-stu-id="0d991-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="0d991-115">但是，：</span><span class="sxs-lookup"><span data-stu-id="0d991-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="0d991-116">请注意，WQL 查询经常使用诸如空格或等号等字符，这些字符在 Windows PowerShell 中均具有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="0d991-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="0d991-117">为此，比较明智的做法是始终将“Filter”参数的值用引号括起来。</span><span class="sxs-lookup"><span data-stu-id="0d991-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="0d991-118">还可以使用 Windows PowerShell 转义符（反引号 (\`)），尽管它可能无法提高可读性。</span><span class="sxs-lookup"><span data-stu-id="0d991-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="0d991-119">以下命令等效于上述命令并返回相同的结果，但使用了反引号对特殊字符进行转义，而不是用引号将整个筛选器字符串括起来。</span><span class="sxs-lookup"><span data-stu-id="0d991-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="0d991-120">若要仅列出你感兴趣的属性，请使用格式设置 cmdlet 的“Property”参数列出所需的属性。</span><span class="sxs-lookup"><span data-stu-id="0d991-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="0d991-121">最后，若要仅查找已安装应用程序的名称，一个简单的 **Format-Wide** 语句便可简化输出：</span><span class="sxs-lookup"><span data-stu-id="0d991-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="0d991-122">尽管我们现在有多种方法来查看使用 Windows Installer 进行安装的应用程序，但我们还没有考虑其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="0d991-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="0d991-123">由于大多数标准应用程序都向 Windows 注册了其卸载程序，我们通过在 Windows 注册表中查找它们便可以在本地对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="0d991-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="0d991-124">列出所有可卸载的应用程序</span><span class="sxs-lookup"><span data-stu-id="0d991-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="0d991-125">尽管无法保证找到系统上的每个应用程序，但可以在“添加或删除程序”对话框中显示的列表中查找所有程序。</span><span class="sxs-lookup"><span data-stu-id="0d991-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="0d991-126">“添加或删除程序”在以下注册表项中查找这些应用程序：</span><span class="sxs-lookup"><span data-stu-id="0d991-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="0d991-127">**HKEY_LOCAL_MACHINE\\软件\\Microsoft\\Windows\\CurrentVersion\\卸载**。</span><span class="sxs-lookup"><span data-stu-id="0d991-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="0d991-128">我们还可以检查此项以查找应用程序。</span><span class="sxs-lookup"><span data-stu-id="0d991-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="0d991-129">若要更加轻松地查看 Uninstall 项，我们可以将 Windows PowerShell 驱动器映射到此注册表位置：</span><span class="sxs-lookup"><span data-stu-id="0d991-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="0d991-130">**HKLM:** 驱动器将映射到 **HKEY_LOCAL_MACHINE** 的根，因此我们在 Uninstall 项的路径中使用了该驱动器。</span><span class="sxs-lookup"><span data-stu-id="0d991-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="0d991-131">我们可以使用 **HKLM** 或 **HKEY_LOCAL_MACHINE**（而不是 **HKLM：**）指定注册表路径。</span><span class="sxs-lookup"><span data-stu-id="0d991-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="0d991-132">使用现有注册表驱动器的优点是我们可以使用 Tab 自动补全来填充项名称，因此我们不需要键入它们。</span><span class="sxs-lookup"><span data-stu-id="0d991-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="0d991-133">我们现在具有一个名为“Uninstall”的驱动器，可用于快速方便地查找应用程序安装。</span><span class="sxs-lookup"><span data-stu-id="0d991-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="0d991-134">我们可以查找已安装应用程序的数量，方法是计算 Uninstall 中的注册表项数：Windows PowerShell 驱动器：</span><span class="sxs-lookup"><span data-stu-id="0d991-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="0d991-135">我们可以使用各种以 **Get-ChildItem** 开头的技术进一步在此列表中搜索应用程序。</span><span class="sxs-lookup"><span data-stu-id="0d991-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="0d991-136">若要获取应用程序列表并将其保存在 **$UninstallableApplications** 变量中，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="0d991-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="0d991-137">为了清楚起见，我们在此处使用了较长的变量名称。</span><span class="sxs-lookup"><span data-stu-id="0d991-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="0d991-138">在实际应用中，没有必要使用长名称。</span><span class="sxs-lookup"><span data-stu-id="0d991-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="0d991-139">尽管可以使用 Tab 自动补全输入变量名称，但也可以使用 1-2 个字符的名称提高速度。</span><span class="sxs-lookup"><span data-stu-id="0d991-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="0d991-140">在开发可重用代码时，较长的描述性名称最为有用。</span><span class="sxs-lookup"><span data-stu-id="0d991-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="0d991-141">若要显示 Uninstall 下注册表项中的注册表条目的值，请使用注册表项的 GetValue 方法。</span><span class="sxs-lookup"><span data-stu-id="0d991-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="0d991-142">该方法的值是注册表条目的名称。</span><span class="sxs-lookup"><span data-stu-id="0d991-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="0d991-143">例如，若要查找 Uninstall 项中应用程序的显示名称，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="0d991-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="0d991-144">不能保证这些值是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0d991-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="0d991-145">在以下示例中，两个已安装的项将显示为“Windows Media 编码器 9 系列”：</span><span class="sxs-lookup"><span data-stu-id="0d991-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a><span data-ttu-id="0d991-146">安装应用程序</span><span class="sxs-lookup"><span data-stu-id="0d991-146">Installing Applications</span></span>

<span data-ttu-id="0d991-147">可以使用 **Win32_Product** 类远程或本地安装 Windows Installer 程序包。</span><span class="sxs-lookup"><span data-stu-id="0d991-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="0d991-148">若要在 Windows Vista、Windows Server 2008 以及更高版本的 Windows 上安装应用程序，你必须使用“以管理员身份运行”选项启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0d991-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="0d991-149">在远程安装时，请使用通用命名约定 (UNC) 网络路径指定 .msi 程序包的路径，因为 WMI 子系统并不了解 Windows PowerShell 路径。</span><span class="sxs-lookup"><span data-stu-id="0d991-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="0d991-150">例如，若要在远程计算机 PC01 上安装位于网络共享 \\\\AppServ\\dsp 中的 NewPackage.msi 程序包，请在 Windows PowerShell 提示符下键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="0d991-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="0d991-151">不使用 Windows Installer 技术的应用程序可能具有可用于自动部署的特定于应用程序的方法。</span><span class="sxs-lookup"><span data-stu-id="0d991-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="0d991-152">若要确定是否存在用于部署自动化的方法，请查看应用程序的文档或咨询应用程序供应商的支持系统。</span><span class="sxs-lookup"><span data-stu-id="0d991-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="0d991-153">在某些情况下，即使应用程序供应商没有专门为安装自动化设计应用程序，安装程序软件制造商也可能会使用一些技术进行自动化。</span><span class="sxs-lookup"><span data-stu-id="0d991-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="0d991-154">删除应用程序</span><span class="sxs-lookup"><span data-stu-id="0d991-154">Removing Applications</span></span>

<span data-ttu-id="0d991-155">通过使用 Windows PowerShell 删除 Windows Installer 程序包与安装程序包的方式大致相同。</span><span class="sxs-lookup"><span data-stu-id="0d991-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="0d991-156">下面是一个根据其名称选择要卸载的程序包的示例；在某些情况下，使用 **IdentifyingNumber** 进行筛选可能会更容易：</span><span class="sxs-lookup"><span data-stu-id="0d991-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="0d991-157">即使是在本地执行操作，删除其他应用程序也并不那么简单。</span><span class="sxs-lookup"><span data-stu-id="0d991-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="0d991-158">我们可以通过提取 **UninstallString** 属性查找这些应用程序的命令行卸载字符串。</span><span class="sxs-lookup"><span data-stu-id="0d991-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="0d991-159">此方法适用于 Windows Installer 应用程序和显示在 Uninstall 项下方的旧程序：</span><span class="sxs-lookup"><span data-stu-id="0d991-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="0d991-160">如果愿意，你可以按显示名称筛选输出：</span><span class="sxs-lookup"><span data-stu-id="0d991-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="0d991-161">但是，如果不进行一些修改，这些字符串可能无法直接在 Windows PowerShell 提示符下使用。</span><span class="sxs-lookup"><span data-stu-id="0d991-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="0d991-162">升级 Windows Installer 应用程序</span><span class="sxs-lookup"><span data-stu-id="0d991-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="0d991-163">若要升级应用程序，你需要知道应用程序的名称和应用程序升级包的路径。</span><span class="sxs-lookup"><span data-stu-id="0d991-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="0d991-164">借助这些信息，你可以使用单个 Windows PowerShell 命令升级应用程序：</span><span class="sxs-lookup"><span data-stu-id="0d991-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```