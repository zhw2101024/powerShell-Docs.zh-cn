---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 使用软件安装
ms.openlocfilehash: d164064418ad7a0209166c81a7c3cc32a9db300a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737145"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="53440-103">使用软件安装</span><span class="sxs-lookup"><span data-stu-id="53440-103">Working with Software Installations</span></span>

<span data-ttu-id="53440-104">可以通过 WMI 的 **Win32_Product** 类访问旨在使用 Windows Installer 的应用程序，但当今使用的所有应用程序并非都使用 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="53440-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="53440-105">使用替代安装例程的应用程序通常不由 Windows Installer 管理。</span><span class="sxs-lookup"><span data-stu-id="53440-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="53440-106">用于使用这些应用程序的特定技术取决于安装程序软件和应用程序开发人员做出的决策。</span><span class="sxs-lookup"><span data-stu-id="53440-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="53440-107">例如，通常不能使用此处讨论的技术来管理通过将文件复制到计算机上的文件夹安装的应用程序。</span><span class="sxs-lookup"><span data-stu-id="53440-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="53440-108">你可以使用在[使用文件和文件夹](Working-with-Files-and-Folders.md)中讨论的技术将这些应用程序作为文件和文件夹进行管理。</span><span class="sxs-lookup"><span data-stu-id="53440-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="53440-109">Win32_Product  类不是查询优化。</span><span class="sxs-lookup"><span data-stu-id="53440-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="53440-110">使用通配符筛选器的查询导致 WMI 使用 MSI 提供程序枚举所有已安装的产品，然后按顺序解析完整列表以处理该筛选器。</span><span class="sxs-lookup"><span data-stu-id="53440-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="53440-111">这还会启动已安装包的一致性检查，从而验证和修复安装。</span><span class="sxs-lookup"><span data-stu-id="53440-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="53440-112">验证是一个缓慢的过程，可能会导致事件日志中出现错误。</span><span class="sxs-lookup"><span data-stu-id="53440-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="53440-113">有关详细信息，请参阅[知识库文章 974524](https://support.microsoft.com/help/974524)。</span><span class="sxs-lookup"><span data-stu-id="53440-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="53440-114">列出 Windows Installer 应用程序</span><span class="sxs-lookup"><span data-stu-id="53440-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="53440-115">若要列出随 Windows Installer 一起在本地或远程系统上安装的应用程序，请使用以下简单的 WMI 查询：</span><span class="sxs-lookup"><span data-stu-id="53440-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

<span data-ttu-id="53440-116">若要将 Win32_Product  对象的所有属性显示到显示屏中，请使用格式设置 cmdlet（例如 `Format-List` cmdlet）的“Property”  参数，值为 `*`（全部）。</span><span class="sxs-lookup"><span data-stu-id="53440-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="53440-117">或者，可以使用 `Get-CimInstance`**Filter** 参数来仅选择 Microsoft .NET 2.0 运行时。</span><span class="sxs-lookup"><span data-stu-id="53440-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET 2.0 Runtime.</span></span> <span data-ttu-id="53440-118">“Filter”  参数的值使用 WMI 查询语言 (WQL) 语法，而不是 Windows PowerShell 语法。</span><span class="sxs-lookup"><span data-stu-id="53440-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="53440-119">例如：</span><span class="sxs-lookup"><span data-stu-id="53440-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="53440-120">若要仅列出你感兴趣的属性，请使用格式设置 cmdlet 的“Property”  参数列出所需的属性。</span><span class="sxs-lookup"><span data-stu-id="53440-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="53440-121">列出所有可卸载的应用程序</span><span class="sxs-lookup"><span data-stu-id="53440-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="53440-122">由于大多数标准应用程序都向 Windows 注册了卸载程序，我们通过在 Windows 注册表中查找它们便可以在本地对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="53440-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="53440-123">无法保证找到系统上的每个应用程序。</span><span class="sxs-lookup"><span data-stu-id="53440-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="53440-124">但可以在下列注册表项的“添加或删除程序”  中显示的列表中查找所有程序：</span><span class="sxs-lookup"><span data-stu-id="53440-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs** in the following registry key:</span></span>

<span data-ttu-id="53440-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall` 列中的一个值匹配。</span><span class="sxs-lookup"><span data-stu-id="53440-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="53440-126">我们可以检查此项以查找应用程序。</span><span class="sxs-lookup"><span data-stu-id="53440-126">We can examine this key to find applications.</span></span> <span data-ttu-id="53440-127">若要更加轻松地查看 Uninstall 项，我们可以将 PowerShell 驱动器映射到此注册表位置：</span><span class="sxs-lookup"><span data-stu-id="53440-127">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

<span data-ttu-id="53440-128">我们现在具有一个名为“Uninstall:”的驱动器，可用于快速方便地查找应用程序安装。</span><span class="sxs-lookup"><span data-stu-id="53440-128">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="53440-129">我们可以查找已安装应用程序的数量，方法是计算''Uninstall: PowerShell''驱动器中的注册表项数：</span><span class="sxs-lookup"><span data-stu-id="53440-129">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

<span data-ttu-id="53440-130">我们可以使用各种以 `Get-ChildItem` 开头的技术进一步在此列表中搜索应用程序。</span><span class="sxs-lookup"><span data-stu-id="53440-130">We can search this list of applications further by using a variety of techniques, beginning with `Get-ChildItem`.</span></span> <span data-ttu-id="53440-131">若要获取应用程序列表并将其保存在 `$UninstallableApplications` 变量中，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="53440-131">To get a list of applications and save them in the `$UninstallableApplications` variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="53440-132">若要显示 Uninstall 下注册表项中的注册表条目的值，请使用注册表项的 GetValue 方法。</span><span class="sxs-lookup"><span data-stu-id="53440-132">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="53440-133">该方法的值是注册表条目的名称。</span><span class="sxs-lookup"><span data-stu-id="53440-133">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="53440-134">例如，若要查找 Uninstall 项中应用程序的显示名称，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="53440-134">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="53440-135">不能保证这些值是唯一的。</span><span class="sxs-lookup"><span data-stu-id="53440-135">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="53440-136">在以下示例中，两个已安装的项将显示为“Windows Media 编码器 9 系列”：</span><span class="sxs-lookup"><span data-stu-id="53440-136">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : http://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a><span data-ttu-id="53440-137">安装应用程序</span><span class="sxs-lookup"><span data-stu-id="53440-137">Installing Applications</span></span>

<span data-ttu-id="53440-138">可以使用 **Win32_Product** 类远程或本地安装 Windows Installer 程序包。</span><span class="sxs-lookup"><span data-stu-id="53440-138">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="53440-139">若要安装应用程序，必须使用“以管理员身份运行”选项启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="53440-139">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="53440-140">在远程安装时，请使用通用命名约定 (UNC) 网络路径指定 .msi 包的路径，因为 WMI 子系统并不了解 PowerShell 路径。</span><span class="sxs-lookup"><span data-stu-id="53440-140">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="53440-141">例如，若要在远程计算机 PC01 上安装位于网络共享 `\\AppServ\dsp` 中的 NewPackage.msi 包，请在 PowerShell 提示符下键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="53440-141">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="53440-142">不使用 Windows Installer 技术的应用程序可能具有用于自动部署的特定于应用程序的方法。</span><span class="sxs-lookup"><span data-stu-id="53440-142">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="53440-143">查看应用程序的文档或咨询应用程序供应商的支持系统。</span><span class="sxs-lookup"><span data-stu-id="53440-143">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="53440-144">删除应用程序</span><span class="sxs-lookup"><span data-stu-id="53440-144">Removing Applications</span></span>

<span data-ttu-id="53440-145">通过使用 PowerShell 删除 Windows Installer 程序包与安装程序包的方式大致相同。</span><span class="sxs-lookup"><span data-stu-id="53440-145">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="53440-146">下面是一个根据其名称选择要卸载的程序包的示例；在某些情况下，使用 **IdentifyingNumber** 进行筛选可能会更容易：</span><span class="sxs-lookup"><span data-stu-id="53440-146">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="53440-147">即使是在本地执行操作，删除其他应用程序也并不那么简单。</span><span class="sxs-lookup"><span data-stu-id="53440-147">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="53440-148">我们可以通过提取 **UninstallString** 属性查找这些应用程序的命令行卸载字符串。</span><span class="sxs-lookup"><span data-stu-id="53440-148">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="53440-149">此方法适用于 Windows Installer 应用程序和显示在 Uninstall 项下方的旧程序：</span><span class="sxs-lookup"><span data-stu-id="53440-149">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="53440-150">如果愿意，你可以按显示名称筛选输出：</span><span class="sxs-lookup"><span data-stu-id="53440-150">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="53440-151">但是，如果不进行一些修改，这些字符串可能无法直接在 PowerShell 提示符下使用。</span><span class="sxs-lookup"><span data-stu-id="53440-151">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="53440-152">升级 Windows Installer 应用程序</span><span class="sxs-lookup"><span data-stu-id="53440-152">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="53440-153">若要升级应用程序，你需要知道应用程序的名称和应用程序升级包的路径。</span><span class="sxs-lookup"><span data-stu-id="53440-153">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="53440-154">借助这些信息，你可以使用单个 PowerShell 命令升级应用程序：</span><span class="sxs-lookup"><span data-stu-id="53440-154">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
