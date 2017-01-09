---
title: "WMF 5.1 中的已知问题"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 8f1b550e92c3c280b84664e0b1f9695172370522
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="known-issues-in-wmf-51"></a>WMF 5.1 中的已知问题 #

> 注意：此信息可能随时发生更改。

## <a name="starting-powershell-shortcut-as-administrator"></a>以管理员身份启动 PowerShell 快捷方式
在安装 WMF 时，如果尝试以管理员身份通过该快捷方式启动 PowerShell，可能会显示“未指定的错误”消息。
以非管理员身份重新打开快捷方式，快捷方式现在甚至可以管理员身份工作。

## <a name="pester"></a>Pester
在本版本中，在 Nano 服务器上使用 Pester 时应注意两个问题：

* 由于 FULL CLR 和 CORE CLR 之间的差异，针对 Pester 自身运行测试可能导致一些失败。 特别是，Validate 方法不可用于 XmlDocument 类型。 众所周知，尝试验证 NUnit 输出日志的架构的六个测试都将失败。 
* 一个代码覆盖率测试失败的原因是当前 Nano 服务器中不存在 *WindowsFeature* DSC 资源。 但是，这些故障通常是无害的，可以放心地忽略。

## <a name="operation-validation"></a>操作验证 

* 由于帮助 URI 不起作用，针对 Microsoft.PowerShell.Operation.Validation 模块的 Update-Help 将失败

## <a name="dsc-after-uninstall-wmf"></a>卸载 WMF 后的 DSC 
* 卸载 WMF 不会从配置文件夹中删除 DSC MOF 文档。 如果 MOF 文档包含在较旧系统中不可用的较新属性，DSC 将无法正常工作。 在这种情况下，请从提升的 PowerShell 控制台运行以下脚本，以清理 DSC 状态。
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  