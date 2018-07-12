---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.1 中的已知问题
ms.openlocfilehash: 74e5a6763a8a780000bf876f34caa9646a2a416a
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892131"
---
# <a name="known-issues-in-wmf-51"></a>WMF 5.1 中的已知问题

> [!Note]
> 此信息可能随时发生更改。

## <a name="starting-powershell-shortcut-as-administrator"></a>以管理员身份启动 PowerShell 快捷方式

在安装 WMF 时，如果尝试以管理员身份通过该快捷方式启动 PowerShell，可能会显示“未指定的错误”消息。
以非管理员身份重新打开快捷方式，快捷方式现在甚至可以管理员身份工作。

## <a name="pester"></a>Pester

在本版本中，在 Nano 服务器上使用 Pester 时应注意两个问题：

- 由于 FULL CLR 和 CORE CLR 之间的差异，针对 Pester 自身运行测试可能导致一些失败。 特别是，Validate 方法不可用于 XmlDocument 类型。 众所周知，尝试验证 NUnit 输出日志的架构的六个测试都将失败。
- 一个代码覆盖率测试失败的原因是当前 Nano 服务器中不存在 *WindowsFeature* DSC 资源。 但是，这些故障通常是无害的，可以放心地忽略。

## <a name="operation-validation"></a>操作验证

- 由于帮助 URI 不起作用，针对 Microsoft.PowerShell.Operation.Validation 模块的 `Update-Help` 将失败

## <a name="dsc-after-uninstall-wmf"></a>卸载 WMF 后的 DSC

- 卸载 WMF 不会从配置文件夹中删除 DSC MOF 文档。 如果 MOF 文档包含在较旧系统中不可用的较新属性，DSC 将无法正常工作。 在这种情况下，请从提升的 PowerShell 控制台运行以下脚本，以清理 DSC 状态。

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>JEA 虚拟帐户

升级到 WMF 5.1 后，在 WMF 5.0 中配置为使用虚拟帐户的 JEA 终结点和会话配置不会配置为使用虚拟帐户。
也就是说，在 JEA 会话中运行的命令将在连接用户的身份（而不是临时管理员帐户）下运行，这可能会导致用户无法运行需要提升的权限的命令。
若要还原虚拟帐户，需要先取消注册，然后重新注册使用虚拟帐户的所有会话配置。

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```