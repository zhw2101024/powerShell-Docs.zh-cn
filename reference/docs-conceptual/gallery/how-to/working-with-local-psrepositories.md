---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery,psget
title: 使用本地 PSRepository
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327988"
---
# <a name="working-with-local-powershellget-repositories"></a>使用本地 PowerShellGet 存储库

PowerShellGet 模块支持 PowerShell 库以外的存储库。
这些 cmdlet 支持以下场景：

- 支持在环境中使用一组受信任的、预先验证的 PowerShell 模块
- 测试构建 PowerShell 模块或脚本的 CI/CD 管道
- 将 PowerShell 脚本和模块交付给无法访问 Internet 的系统

本文介绍如何设置本地 PowerShell 存储库。 本文还介绍了可以从 PowerShell 库获得的 [OfflinePowerShellGetDeploy][] 模块。 该模块包含 cmdlet，用于将 PowerShellGet 的最新版本安装到本地存储库中。

## <a name="local-repository-types"></a>本地存储库类型

有两种方法可以创建本地 PSRepository：NuGet 服务器或文件共享。 每种类型都有优点和缺点：

NuGet 服务器

| 优点| 缺点 |
| --- | --- |
| 精确模拟 powershell 库功能 | 多层应用需要操作规划和支持 |
| NuGet 与 Visual Studio 等其他工具集成 | 需要身份验证模型和 NuGet 帐户管理 |
| NuGet 支持 `.Nupkg` 包中的元数据 | 发布需要进行 API 密钥管理和维护 |
| 提供搜索、包管理等。 | |

文件共享

| 优点| 缺点 |
| --- | --- |
| 易于设置、备份和维护 | PowerShellGet 使用的元数据不可用 |
| 简单安全模型 - 用户的共享权限 | 除了基本文件共享之外，没有 UI |
| 没有诸如替换现有项之类的约束 | 有限的安全性且没有有关用户更新内容的记录 |

PowerShellGet 适用于任一类型，并支持查找版本和依赖项安装。
但是，一些适用于 PowerShell 库的功能不适用于基本 NuGet 服务器或文件共享。

- 所有内容都是一个包 - 不区分脚本、模块、DSC 资源或角色功能。
- 文件共享服务器不能查看包元数据，包括标记。

## <a name="creating-a-local-repository"></a>创建本地存储库

以下文章列出了设置自己的 NuGet 服务器的步骤。

- [NuGet.Server][]

按照以下步骤操作，直到添加包为止。 本文稍后会介绍有关[发布包](#publishing-to-a-local-repository)的步骤。

对于基于文件共享的存储库，请确保用户有权访问文件共享。

## <a name="registering-a-local-repository"></a>注册本地存储库

在使用存储库之前，必须使用 `Register-PSRepository` 命令对其进行注册。
在下面的示例中，假定你信任自己的存储库，将“InstallationPolicy”  设置为“受信任”  。

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

请注意这两个命令处理 ScriptSourceLocation  方式的差异。 对于基于文件共享的存储库，SourceLocation  和 ScriptSourceLocation  必须匹配。 对于基于 Web 的存储库，它们必须不同，因此，在此示例中，在 SourceLocation  中添加了一个尾随的“/”。

如果希望将新创建的 PSRepository 作为默认存储库，则必须注销所有其他 PSRepository。 例如：

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> 保留了存储库名称“PSGallery”以供 PowerShell 库使用。 可以注销 PSGallery，但不能对任何其他存储库重用名称 PSGallery。

如需还原 PSGallery，请运行以下命令：

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>发布到本地存储库

一旦注册本地 PSRepository，就可以将其发布到本地 PSRepository。 有两个主要发布方案：发布你自己的模块和发布 PSGallery 中的模块。

### <a name="publishing-a-module-you-authored"></a>发布自己编写的模块

使用 `Publish-Module` 和 `Publish-Script` 将模块发布到本地 PSRepository，具体方法与对 PowerShell 库执行的操作相同。

- 指定代码的位置
- 提供 API 密钥
- 指定存储库名称。 例如，`-PSRepository LocalPSRepo`

> [!NOTE]
> 必须在 NuGet 服务器中创建一个帐户，然后登录以生成并保存 API 密钥。
> 对于文件共享，请对 NuGetApiKey 值使用任何非空字符串。

示例：

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 若要确保安全，不应在脚本中对 API 密钥进行硬编码。 使用安全的密钥管理系统。

### <a name="publishing-a-module-from-the-psgallery"></a>从 PSGallery 发布模块

要将模块从 PSGallery 发布到本地 PSRepository，可以使用“Save-Package”cmdlet。

- 指定包的名称
- 指定“NuGet”作为提供程序
- 将 PSGallery 位置指定为源 (https://www.powershellgallery.com/api/v2)
- 指定本地存储库的路径

例如：

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

如果本地 PSRepository 基于 Web，则需要另外执行一个使用 nuget.exe 的步骤才能进行发布。

请参阅有关使用 [nuget.exe][] 的文档。

## <a name="installing-powershellget-on-a-disconnected-system"></a>在断开连接的系统上安装 PowerShellGet

在要求系统与 Internet 断开连接的环境中，部署 PowerShellGet 非常困难。 PowerShellGet 有一个启动过程，它会在第一次使用时安装最新版本。 PowerShell 库中的 OfflinePowerShellGetDeploy 模块提供了支持此启动过程的 cmdlet。

若要启动离线部署，需要：

- 在连接 Internet 的系统和断开连接的系统上下载并安装 OfflinePowerShellGetDeploy
- 使用 `Save-PowerShellGetForOffline` cmdlet 在连接 Internet 的系统上下载 PowerShellGet 及其依赖项
- 将 PowerShellGet 及其依赖项从连接 Internet 的系统复制到断开连接的系统
- 在断开连接的系统上使用 `Install-PowerShellGetOffline`，将 PowerShellGet 及其依赖项置于适当的文件夹中

以下命令使用 `Save-PowerShellGetForOffline` 将所有组件都放入文件夹 `f:\OfflinePowerShellGet` 中

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

此时，必须使 `F:\OfflinePowerShellGet` 的内容对断开连接的系统可用。 运行 `Install-PowerShellGetOffline` cmdlet 在断开连接的系统上安装 PowerShellGet。

> [!NOTE]
> 在运行这些命令之前，不要在 PowerShell 会话中运行 PowerShellGet，这一点很重要。 一旦 PowerShellGet 加载到会话中，就无法更新组件。 如果意外启动 PowerShellGet，请退出并重启 PowerShell。

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

运行这些命令后，便可以将 PowerShellGet 发布到本地存储库。

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 若要确保安全，不应在脚本中对 API 密钥进行硬编码。 使用安全的密钥管理系统。

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
