---
title: "使用软件安装"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 9f60be9bebe9dfaa98f495c8e9a9c0d8c2fa5cc2

---

# 使用软件安装
可以通过 WMI 的 **Win32\_Product** 类访问旨在使用 Windows Installer 的应用程序，但当今使用的所有应用程序并非都使用 Windows Installer。 由于 Windows Installer 提供了最广泛的标准技术用于使用可安装的应用程序，因此我们将主要使用这些应用程序。 使用替代安装例程的应用程序通常不由 Windows Installer 管理。 用于使用这些应用程序的特定技术将取决于安装程序软件和应用程序开发人员做出的决策。

> [!NOTE]
> 通常不能使用此处讨论的技术来管理通过将应用程序文件复制到计算机安装的应用程序。 你可以使用在“使用文件和文件夹”部分中讨论的技术将这些应用程序作为文件和文件夹进行管理。

### 列出 Windows Installer 应用程序
若要列出随 Windows Installer 一起在本地或远程系统上安装的应用程序，请使用以下简单的 WMI 查询：

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

若要将 Win32\_Product 对象的所有属性显示到显示屏中，请使用格式设置 cmdlet（例如 Format\-List cmdlet）的“Property”参数，值为 \*（全部）。

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

或者，可以使用 **Get\-WmiObject Filter** 参数仅选择 Microsoft .NET Framework 2.0。 由于此命令中使用的筛选器是 WMI 筛选器，它使用 WMI 查询语言 (WQL) 语法，而不是 Windows PowerShell 语法。 但是，：

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

请注意，WQL 查询经常使用诸如空格或等号等字符，这些字符在 Windows PowerShell 中均具有特殊含义。 为此，比较明智的做法是始终将“Filter”参数的值用引号括起来。 还可以使用 Windows PowerShell 转义符（反引号 (\`)），尽管它可能无法提高可读性。 以下命令等效于上述命令并返回相同的结果，但使用了反引号对特殊字符进行转义，而不是用引号将整个筛选器字符串括起来。

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

若要仅列出你感兴趣的属性，请使用格式设置 cmdlet 的“Property”参数列出所需的属性。

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

最后，若要仅查找已安装应用程序的名称，一个简单的 **Format\-Wide** 语句便可简化输出：

```
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

尽管我们现在有多种方法来查看使用 Windows Installer 进行安装的应用程序，但我们还没有考虑其他应用程序。 由于大多数标准应用程序都向 Windows 注册了其卸载程序，我们通过在 Windows 注册表中查找它们便可以在本地对其进行处理。

### 列出所有可卸载的应用程序
尽管无法保证找到系统上的每个应用程序，但可以在“添加或删除程序”对话框中显示的列表中查找所有程序。 “添加或删除程序”在以下注册表项中查找这些应用程序：

**HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**。

我们还可以检查此项以查找应用程序。 若要更加轻松地查看 Uninstall 项，我们可以将 Windows PowerShell 驱动器映射到此注册表位置：

```
PS>    

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> **HKLM:** 驱动器将映射到 **HKEY\_LOCAL\_MACHINE** 的根，因此我们在 Uninstall 项的路径中使用了该驱动器。 我们可以使用 **HKLM** 或 **HKEY\_LOCAL\_MACHINE**（而不是 **HKLM：**）指定注册表路径。 使用现有注册表驱动器的优点是我们可以使用 tab 自动补全来填充项名称，因此我们不需要键入它们。

我们现在具有一个名为“Uninstall”的驱动器，可用于快速方便地查找应用程序安装。 我们可以查找已安装应用程序的数量，方法是计算 Uninstall 中的注册表项数：Windows PowerShell 驱动器：

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

我们可以使用各种以 **Get\-ChildItem** 开头的技术进一步在此列表中搜索应用程序。 若要获取应用程序列表并将其保存在 **$UninstallableApplications** 变量中，请使用以下命令：

```
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> 为了清楚起见，我们在此处使用了较长的变量名称。 在实际应用中，没有必要使用长名称。 尽管可以使用 tab 自动补全输入变量名称，但也可以使用 1–2 个字符的名称提高速度。 在开发可重用代码时，较长的描述性名称最为有用。

若要显示 Uninstall 下注册表项中的注册表条目的值，请使用注册表项的 GetValue 方法。 该方法的值是注册表条目的名称。

例如，若要查找 Uninstall 项中应用程序的显示名称，请使用以下命令：

```
PS> Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("DisplayName") }
```

不能保证这些值是唯一的。 在以下示例中，两个已安装的项将显示为“Windows Media 编码器 9 系列”：

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### 安装应用程序
可以使用 **Win32\_Product** 类远程或本地安装 Windows Installer 程序包。

> [!NOTE]
> 若要在 Windows Vista、Windows Server 2008 以及更高版本的 Windows 上安装应用程序，你必须使用“以管理员身份运行”选项启动 Windows PowerShell。

在远程安装时，请使用通用命名约定 (UNC) 网络路径指定 .msi 程序包的路径，因为 WMI 子系统并不了解 Windows PowerShell 路径。 例如，若要在远程计算机 PC01 上安装位于网络共享 \\\\AppServ\\dsp 中的 NewPackage.msi 程序包，请在 Windows PowerShell 提示符下键入以下命令：

```
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq "Win32_Product"}).Install(\\AppSrv\dsp\NewPackage.msi)
```

不使用 Windows Installer 技术的应用程序可能具有可用于自动部署的特定于应用程序的方法。 若要确定是否存在用于部署自动化的方法，请查看应用程序的文档或咨询应用程序供应商的支持系统。 在某些情况下，即使应用程序供应商没有专门为安装自动化设计应用程序，安装程序软件制造商也可能会使用一些技术进行自动化。

### 删除应用程序
通过使用 Windows PowerShell 删除 Windows Installer 程序包与安装程序包的方式大致相同。 下面是一个根据其名称选择要卸载的程序包的示例；在某些情况下，使用 **IdentifyingNumber** 进行筛选可能会更容易：

```
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

即使是在本地执行操作，删除其他应用程序也并不那么简单。 我们可以通过提取 **UninstallString** 属性查找这些应用程序的命令行卸载字符串。 此方法适用于 Windows Installer 应用程序和显示在 Uninstall 项下方的旧程序：

```
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

如果愿意，你可以按显示名称筛选输出：

```
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -like "Win*"} | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

但是，如果不进行一些修改，这些字符串可能无法直接在 Windows PowerShell 提示符下使用。

### 升级 Windows Installer 应用程序
若要升级应用程序，你需要知道应用程序的名称和应用程序升级包的路径。 借助这些信息，你可以使用单个 Windows PowerShell 命令升级应用程序：

```
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```




<!--HONumber=Jun16_HO4-->


