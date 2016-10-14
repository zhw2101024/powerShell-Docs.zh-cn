---
title: "功能或方案记录的示例模板"
contributor: KeithB
translationtype: Human Translation
ms.sourcegitcommit: 8c55ca4b972c8d708a09b922f27eec585ddc33d0
ms.openlocfilehash: 025565404b60cebefac27e51c70d70edb5e47bc9

---

>注意：提供建议的描述性标题和简短说明

## PowerShellGet 增强功能 ##
PowerShellGet 模块中的 cmdlet 已在 WMF 5.1 中得到很大程度的更新。 现在支持以下新方案：

- **代理支持：**将 Proxy 和 ProxyCredential 参数加入 PowerShellGet 模块（例如：Find-Module、Install-Module、Save-Module、Publish-Module）中所有的 Find-、Install-、Save- 和 Publish- cmdlet，现已支持使用具有内部代理的 PowerShellGet cmdlet。 
- **强制执行目录签名：**现在所有的 PowerShellGet cmdlet 都将检查并强制更新已签名模块。 PowerShellGet cmdlet 将检查使用新的 Catalog cmdlet 签名的模块，以确保尚未在传输过程中修改该模块，且对该模块的更新可能仅来自于原始发布服务器。 这将影响 Install-Module 和 Update-Module cmdlet。 
- **共享和获取角色功能：**角色功能是用于配置要约束的 Just Enough Administration 的终结点定义，将通过 PowerShell 模块中的 PowerShell 库共享。 Cmdlet 包括 Find-RoleCapability 和 New-PSRoleCapabilityFile。 
- **查找命令：**查找命令允许用户定位包含他们所查找的命令的 PowerShell 库中的模块。 
- **经过身份验证的存储库：**Visual Studio 包管理源要求身份验证，即现在通过 PowerShellGet cmdlet 支持的一些内容。

在 5.1 中已解决的用户反馈确定可改进的其他方面包括：

- **Install-Script 更改：**Install-script 使用的位置未自动添加到 5.1 中的用户路径。 此更改是在 PowerShellGet 的独立版本中进行的，现已包括到 WMF 5.1 中。
- **将元数据字段添加到现有脚本：**可在现有脚本上使用 Update-ScriptFileInfo，以将需要发布的默认元数据字段添加到 PowerShellGallery。 以前，用户需要手动将其合并到现有脚本。
- **将较低版本的模块发布到库：**现在可以使用 Publish-Module 将较当前上一个最高版本具有较低版本号的模块发布到库。 如果发布服务器发布其模块的 2.0.0 版本，此版本与 1.x 版本相比进行了重大更改，则它们无法轻松地将修补程序发布到版本 1.5.0。 现在，它们可以发布 1.5.1，这将改进对 PowerShell 库中模块维护的支持。 
- **安装脚本与模块时检查命令覆盖：**Install-Module 和 Install-Script 现在将检查以查看它们是否包含已出现在系统上的命令，并在出现该情况时默认出错。 
- **在 Publish- cmdlet 中引导 Nuget：**以前，在使用 Publish-Module 或 Publish-Script 时无法自动安装 Nuget 提供程序，这使得某些自动化任务非常困难。 用户现在可以添加-Force to Publish- 命令以绕过提示。 

>注意：涵盖新概念、实现、示例等的其他详细信息应链接到规范技术文档

**了解有关使用 PowerShellGet 的详细信息**
- [About-CatalogSigning]()
- []()
- [按 CompatiblePSEditions 筛选 Get-Module 结果]()
- [阻止脚本执行，除非在 PowerShell 的兼容版本上运行]()






<!--HONumber=Aug16_HO3-->


