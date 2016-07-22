---
title: "PackageManagement（又称为 OneGet）改进"
contributor: jianyunt, quoctruong
translationtype: Human Translation
ms.sourcegitcommit: 3b5a3bb0ef9cf123c0cee4a36890ac61431c85ff
ms.openlocfilehash: bb1129e6aa20b64e94ddb6d7b7cf7b51b1df9ca3

---

>注意：提供建议的描述性标题和简短说明

## PackageManagement（又称为 OneGet）改进 ##
以下是在 WMF 5.1 中进行的修复，用于解决 WMF 5.0 版本中的一些用户体验缺口。 

1 **版本别名**

**情形**：假定你在系统上安装了包 P1 的版本 1.0 和 2.0，并且现在要卸载版本 1.0，因此运行“uninstall-package -name P1 -version 1.0”。 你预计在运行该 cmdlet 之后将卸载版本 1.0。 但是结果是卸载了版本 2.0。 
    
此问题的原因在于“-version”参数是“-minimumversion”参数的别名。 当 OneGet 查找具有最低版本 1.0 的合格包时，它会返回最新版本。 在正常情况下需要此行为，因为查找最新版本是大多数人要进行的操作。 但是，它不应该应用于 uninstall-package 情况。
    
**解决方案**：在 OneGet 和 PowerShellGet 中已完全删除了 -version 别名。 

2 **多个用于启动 NuGet 提供程序的提示**

**情形**：在计算机上首次运行 Find-Module 或 install-module 或是其他 OneGet cmdlet 时，OneGet 会尝试启动 NuGet 提供程序。 这是因为 PowershellGet 提供程序还使用 NuGet 提供程序来下载 PowerShell 模块。 OneGet 随后会提示用户输入安装 NuGet 提供程序的权限。 用户选择“yes”进行启动之后，会安装最新版本的 NuGet 提供程序。 
    
但是，对于在计算机上安装了旧版本的 NuGet 提供程序的这种情况，较旧版本的 NuGet 有时会先加载到 PowerShell 会话中（这是 OneGet 中的争用条件）。 但是 PowerShellGet 需要更新版本的 Nuget 提供程序来正常运行，因此 PowerShellGet 会要求 OneGet 再次启动 NuGet 提供程序。 这就是为什么你会看到多个用于启动 NuGet 提供程序的提示。

**解决方案**：OneGet 现在加载最新版本的 NuGet 提供程序，以避免出现多个用于启动 NuGet 提供程序的提示。

还有一种解决方法，即手动删除旧版本的 NuGet 提供程序（NuGet-Anycpu.exe，如果在 $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies 中存在）


3 **仅具有 Intranet 的计算机**

**情形**：对于企业情形，人们在没有 Internet 访问，而是只有 Intranet 的环境中工作。 OneGet 在 WMF 5.0 中不支持这种情况。

**解决方案**：
- 你可以在其他计算机上通过 Internet 连接，使用命令“Install-PackageProvider -Name NuGet”下载 NuGet 提供程序。

- 在 $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget 或 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget 下查找你刚安装的 NuGet 提供程序。 

- 将二进制文件复制到你的计算机（没有 Internet 的那台计算机）也有权访问的文件夹或网络共享位置，然后使用“Install-PackageProvider NuGet -Source <Path to folder>”安装 NuGet 提供程序。


4 **事件日志**

安装包时，你会更改计算机的状态。 为进行诊断，OneGet 现在针对安装、卸载和保存包将事件记录到 Windows 事件日志中。 事件通道在操作方面与 PowerShell 相同，即，Microsoft-Windows-PowerShell。

5 **身份验证支持** OneGet 现在支持从需要基本身份验证的存储库查找和安装包。 你可以向 Find-Package 和 Install-Package cmdlet 提供凭据。 例如：
``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
6 **在代理后面使用 OneGet**

OneGet 现在采用代理参数：-ProxyCredential 和 -Proxy。 使用这些参数可以向 OneGet cmdlet 指定代理服务器 url 和代理凭据（默认情况下，我们使用系统代理设置）。 例如：
``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


