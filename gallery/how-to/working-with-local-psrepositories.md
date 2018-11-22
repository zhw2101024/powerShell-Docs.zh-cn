---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery,psget
title: 使用本地 PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619191"
---
# <a name="working-with-local-powershellget-repositories"></a>使用本地 PowerShellGet 存储库

PowerShellGet 模块支持存储库之外 PowerShell 库。
这些 cmdlet 支持以下方案：

- 在您的环境中使用支持一组受信任的、 预先经过验证的 PowerShell 模块
- 测试生成 PowerShell 模块或脚本的 CI/CD 管道
- 为不能访问 internet 的系统提供的 PowerShell 脚本和模块

本文介绍如何设置本地 PowerShell 存储库。 本文还介绍了[OfflinePowerShellGetDeploy][] PowerShell 库中可用的模块。 此模块包含用于安装到本地存储库的最新版本的 PowerShellGet cmdlet。

## <a name="local-repository-types"></a>本地存储库类型

有两种方法来创建本地 PSRepository: NuGet 服务器或文件共享。 每种类型都有优点和缺点：

NuGet 服务器

| 优点| 缺点 |
| --- | --- |
| 精确模拟 powershell 库功能 | 多层应用程序需要规划的操作和支持 |
| NuGet 与 Visual Studio 中，其他工具集成 | 身份验证模型和所需的 NuGet 帐户管理 |
| NuGet 支持中的元数据`.Nupkg`包 | 发布操作要求 API 密钥管理和维护 |
| 提供搜索、 包管理，等等。 | |

文件共享

| 优点| 缺点 |
| --- | --- |
| 易于设置、 备份和维护 | 使用 PowerShellGet 的元数据不可用 |
| 简单安全模型的共享上的用户权限 | 除了基本文件共享没有用户界面 |
| 例如，现有的项目替换为任何约束 | 有限的安全和没有录制的内容更新者 |

PowerShellGet 适用于类型和支持查找的版本和依赖项安装。
但是，一些适用于 PowerShell 库的功能不适用于基本 NuGet 服务器或文件共享。

- 所有内容是一个包的脚本、 模块、 DSC 资源或角色功能没有差异。
- 文件共享服务器不能查看包元数据，包括标记。

## <a name="creating-a-local-repository"></a>创建本地存储库

以下文章列出了用于设置你自己的 NuGet 服务器的步骤。

- [NuGet.Server][]

按照添加包的点之前的步骤。 有关步骤[发布包](#publishing-to-a-local-repository)本文稍后介绍。

对于文件基于共享的存储库，请确保你的用户有权访问文件共享。

## <a name="registering-a-local-repository"></a>注册本地存储库

可以使用存储库之前，它必须使用注册`Register-PSRepository`命令。
在下面的示例**InstallationPolicy**设置为*受信任*，假定您信任您自己的存储库。

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

记下两个命令的处理方式的区别**ScriptSourceLocation**。 文件共享基于存储库，对于**SourceLocation**并**ScriptSourceLocation**必须匹配。 对于基于 web 的存储库，它们必须不同，因此，在此示例中的尾随"/"添加到**SourceLocation**。

如果您想新建的 PSRepository 为默认存储库，必须取消注册所有其他 PSRepositories。 例如：

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> PowerShell 库存储库名称 PSGallery' 保留供。 可以取消注册 PSGallery，但不能重复使用任何其他存储库的名称 PSGallery。

如果需要还原 PSGallery，运行以下命令：

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>发布到本地存储库

一旦注册本地 PSRepository 后，您可以将发布到本地 PSRepository。 有两个主要发布方案： 发布你自己的模块和发布提供 PSGallery 的模块。

### <a name="publishing-a-module-you-authored"></a>发布您编写的模块

使用`Publish-Module`和`Publish-Script`对于 PowerShell 库所做的相同方式将你的模块发布到本地 PSRepository。

- 指定你的代码的位置
- 提供 API 密钥
- 指定存储库名称。 例如，`-PSRepository LocalPSRepo`

> [!NOTE]
> 必须在 NuGet 服务器中创建一个帐户，然后登录以进行生成并保存的 API 密钥。
> 为文件共享，NuGetApiKey 值中使用任何非空字符串。

示例：

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 若要确保安全，API 密钥不应在脚本中硬编码。 使用安全的密钥管理系统。

### <a name="publishing-a-module-from-the-psgallery"></a>发布模块从 PSGallery

若要发布到本地 PSRepository PSGallery 提供模块，可以使用保存包 cmdlet。

- 指定包的名称
- 作为提供程序指定 NuGet
- PSGallery 位置指定为源 （ https://www.powershellgallery.com/api/v2)
- 指定本地存储库的路径

例如：

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

如果本地 PSRepository 是基于 web 的则需要使用 nuget.exe 来发布的其他步骤。

请参阅有关使用文档[nuget.exe][]。

## <a name="installing-powershellget-on-a-disconnected-system"></a>在断开连接的系统上安装 PowerShellGet

部署 PowerShellGet 会要求系统以与 internet 断开的环境中很困难。 PowerShellGet 有一个引导过程的第一次使用它将安装最新版本。 PowerShell 库中的 OfflinePowerShellGetDeploy 模块提供了支持此启动过程中的 cmdlet。

若要启动离线部署，需要：

- 下载并安装 OfflinePowerShellGetDeploy 在连接 internet 的系统和断开连接的系统
- 下载 PowerShellGet 和其依赖 internet 连接的系统使用`Save-PowerShellGetForOffline`cmdlet
- 将从连接 internet 的系统的 PowerShellGet 和其依赖项复制到断开连接的系统
- 使用`Install-PowerShellGetOffline`上断开连接的系统，PowerShellGet 和其依赖项放入适当的文件夹

以下命令使用`Save-PowerShellGetForOffline`可将所有组件都放入一个文件夹 `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

此时，您必须进行的内容`F:\OfflinePowerShellGet`供您断开连接的系统。 运行`Install-PowerShellGetOffline`cmdlet 来断开连接的系统上安装 PowerShellGet。

> [!NOTE]
> 不要在 PowerShell 会话中运行这些命令之前运行 PowerShellGet 至关重要。 PowerShellGet 加载到会话中，不能更新组件。 如果执行意外启动 PowerShellGet，请退出并重新启动 PowerShell。

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

运行这些命令后，已准备好将 PowerShellGet 发布到本地存储库。

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 若要确保安全，API 密钥不应在脚本中硬编码。 使用安全的密钥管理系统。

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
