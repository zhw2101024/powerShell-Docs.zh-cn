---
ms.date: 06/03/2019
keywords: powershell,cmdlet
title: 使用软件安装
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830290"
---
# <a name="working-with-software-installations"></a>使用软件安装

可以通过 WMI 的 **Win32_Product** 类访问旨在使用 Windows Installer 的应用程序，但当今使用的所有应用程序并非都使用 Windows Installer。
使用替代安装例程的应用程序通常不由 Windows Installer 管理。
用于使用这些应用程序的特定技术取决于安装程序软件和应用程序开发人员做出的决策。 例如，通常不能使用此处讨论的技术来管理通过将文件复制到计算机上的文件夹安装的应用程序。 你可以使用在[使用文件和文件夹](Working-with-Files-and-Folders.md)中讨论的技术将这些应用程序作为文件和文件夹进行管理。

> [!CAUTION]
> Win32_Product  类不是查询优化。 使用通配符筛选器的查询导致 WMI 使用 MSI 提供程序枚举所有已安装的产品，然后按顺序解析完整列表以处理该筛选器。 这还会启动已安装包的一致性检查，从而验证和修复安装。 验证是一个缓慢的过程，可能会导致事件日志中出现错误。 有关详细信息，请参阅[知识库文章 974524](https://support.microsoft.com/help/974524)。

## <a name="listing-windows-installer-applications"></a>列出 Windows Installer 应用程序

若要列出随 Windows Installer 一起在本地或远程系统上安装的应用程序，请使用以下简单的 WMI 查询：

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

若要将 Win32_Product  对象的所有属性显示到显示屏中，请使用格式设置 cmdlet（例如 `Format-List` cmdlet）的“Property”  参数，值为 `*`（全部）。

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
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

或者，可以使用 `Get-CimInstance`  Filter 参数来仅选择 Microsoft .NET Framework 2.0。 “Filter”  参数的值使用 WMI 查询语言 (WQL) 语法，而不是 Windows PowerShell 语法。 例如：

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

若要仅列出你感兴趣的属性，请使用格式设置 cmdlet 的“Property”  参数列出所需的属性。

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>列出所有可卸载的应用程序

由于大多数标准应用程序都向 Windows 注册了卸载程序，我们通过在 Windows 注册表中查找它们便可以在本地对其进行处理。 无法保证找到系统上的每个应用程序。 但可以在“添加或删除程序”  中显示的列表中查找所有程序。  “添加或删除程序”在以下注册表项中查找这些应用程序：

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`”。

我们可以检查此项以查找应用程序。 若要更加轻松地查看 Uninstall 项，我们可以将 PowerShell 驱动器映射到此注册表位置：

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
我们现在具有一个名为“Uninstall:”的驱动器，可用于快速方便地查找应用程序安装。 我们可以查找已安装应用程序的数量，方法是计算''Uninstall: PowerShell''驱动器中的注册表项数：

```
(Get-ChildItem -Path Uninstall:).Count
459
```

我们可以使用各种以 **Get-ChildItem** 开头的技术进一步在此列表中搜索应用程序。 若要获取应用程序列表并将其保存在 **$UninstallableApplications** 变量中，请使用以下命令：

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

若要显示 Uninstall 下注册表项中的注册表条目的值，请使用注册表项的 GetValue 方法。 该方法的值是注册表条目的名称。

例如，若要查找 Uninstall 项中应用程序的显示名称，请使用以下命令：

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

不能保证这些值是唯一的。 在以下示例中，两个已安装的项将显示为“Windows Media 编码器 9 系列”：

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a>安装应用程序

可以使用 **Win32_Product** 类远程或本地安装 Windows Installer 程序包。

> [!NOTE]
> 若要安装应用程序，必须使用“以管理员身份运行”选项启动 PowerShell。

在远程安装时，请使用通用命名约定 (UNC) 网络路径指定 .msi 包的路径，因为 WMI 子系统并不了解 PowerShell 路径。 例如，若要在远程计算机 PC01 上安装位于网络共享 `\\AppServ\dsp` 中的 NewPackage.msi 包，请在 PowerShell 提示符下键入以下命令：

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

不使用 Windows Installer 技术的应用程序可能具有用于自动部署的特定于应用程序的方法。 查看应用程序的文档或咨询应用程序供应商的支持系统。

## <a name="removing-applications"></a>删除应用程序

通过使用 PowerShell 删除 Windows Installer 程序包与安装程序包的方式大致相同。 下面是一个根据其名称选择要卸载的程序包的示例；在某些情况下，使用 **IdentifyingNumber** 进行筛选可能会更容易：

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

即使是在本地执行操作，删除其他应用程序也并不那么简单。 我们可以通过提取 **UninstallString** 属性查找这些应用程序的命令行卸载字符串。
此方法适用于 Windows Installer 应用程序和显示在 Uninstall 项下方的旧程序：

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

如果愿意，你可以按显示名称筛选输出：

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

但是，如果不进行一些修改，这些字符串可能无法直接在 PowerShell 提示符下使用。

## <a name="upgrading-windows-installer-applications"></a>升级 Windows Installer 应用程序

若要升级应用程序，你需要知道应用程序的名称和应用程序升级包的路径。 借助这些信息，你可以使用单个 PowerShell 命令升级应用程序：

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
