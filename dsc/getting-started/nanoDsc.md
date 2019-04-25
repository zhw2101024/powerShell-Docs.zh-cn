---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用 Nano Server 上的 DSC
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079721"
---
# <a name="using-dsc-on-nano-server"></a>使用 Nano Server 上的 DSC

> 适用于：Windows PowerShell 5.0

**Nano Server 上的 DSC** 是 Windows Server 2016 媒体 `NanoServer\Packages` 文件夹中的可选包。 通过以下方法为 Nano Server 创建 VHD 后可以安装此包：将 **Microsoft-NanoServer-DSC-Package** 指定为 **New-NanoServerImage** 函数的 **Packages** 参数值。 例如，如果你要为虚拟机创建 VHD，则命令如下所示：

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

若要了解如何安装和使用 Nano Server，以及如何使用 PowerShell 远程处理来管理 Nano Server，请参阅 [Getting Started with Nano Server（Nano Server 入门）](/windows-server/get-started/getting-started-with-nano-server)。

## <a name="dsc-features-available-on-nano-server"></a>Nano Server 上可用的 DSC 功能

由于与完整版的 Windows Server 相比，Nano Server 仅支持一组数量有限的 API，因此 Nano Server 上的 DSC 暂时没有与完整 SKU 上运行的 DSC 等同的完整功能。 Nano Server 上的 DSC 正处于积极开发中，且功能尚未完善。

下面的 DSC 功能当前在 Nano Server 上均可用：

推送和请求模式

- 完整版 Windows Server 上存在的所有 DSC cmdlet，包括：
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- 编译配置（请参阅 [DSC 配置](../configurations/configurations.md)）

  **问题：** 在配置编译期间密码加密不起作用（请参阅[保护 MOF 文件](../pull-server/secureMOF.md)）。

- 编译元配置（请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)）

- 在用户上下文内运行资源（请参阅[使用用户凭据运行 DSC (RunAs)](../configurations/runAsUser.md)）

- 基于类的资源（请参阅[使用 PowerShell 类编写自定义 DSC 资源](../resources/authoringResourceClass.md)）

- 调试 DSC 资源（见[调试 DSC 资源](../troubleshooting/debugResource.md)）

  **问题：** 在资源使用 PsDscRunAsCredential 时不起作用（请参阅[使用用户凭据运行 DSC](../configurations/runAsUser.md)）

- [指定跨节点依赖关系](../configurations/crossNodeDependencies.md)

- [资源版本控制](../configurations/sxsResource.md)

- 请求客户端（配置和资源）（请参阅[使用配置名称设置请求客户端](../pull-server/pullClientConfigNames.md)）

- [部分配置（请求和推送）](../pull-server/partialConfigs.md)

- [向请求服务器报告](../pull-server/reportServer.md)

- MOF 加密

- 事件日志记录

- Azure 自动化 DSC 报告

- 功能齐全的资源

- **存档**
- **环境**
- **文件**
- **日志**
- **ProcessSet**
- **注册表**
- **脚本**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll**（请参阅[请参阅指定跨节点依赖关系](../configurations/crossNodeDependencies.md)）
- **WaitForAny**（请参阅[指定跨节点依赖关系](../configurations/crossNodeDependencies.md)）
- **WaitForSome**（请参阅[指定跨节点依赖关系](../configurations/crossNodeDependencies.md)）

- 实现部分功能的资源
- **组**
- **GroupSet**

  **问题：** 如果调用两次特定实例（运行相同的配置两次），上面的资源失败

- **服务**
- **ServiceSet**

  **问题：** 仅对处于正在启动/停止（状态）的服务有效。 如果有人尝试更改其他服务属性（如 startuptype、credentials、description 等），则会失败。 引发的错误类似于：

  找不到类型 [management.managementobject]: 请验证包含此类型的程序集是否已加载。

- 无法实现功能的资源
- **用户**

## <a name="dsc-features-not-available-on-nano-server"></a>Nano Server 上不可用的 DSC 功能

下面的 DSC 功能当前在 Nano 服务器上不可用：

- 使用加密的密码解密 MOF 文档
- 请求服务器 - 当前不能在 Nano Server 上设置请求服务器
- 不在功能工作列表中的任何内容

## <a name="using-custom-dsc-resources-on-nano-server"></a>在 Nano Server 上使用自定义 DSC 资源

由于 Nano Server 上仅可使用的有限的 Windows API 集和 CLR 库，因此在完整 CLR 版的 Windows 上运行的 DSC 资源并不一定适用于 Nano Server。
在部署任意 DSC 资源到生产环境之前，先完成端到端测试。

## <a name="see-also"></a>另请参阅

- [Nano Server 入门](/windows-server/get-started/getting-started-with-nano-server)
