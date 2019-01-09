---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 从拉取服务器更新节点
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400358"
---
# <a name="update-nodes-from-a-pull-server"></a>从拉取服务器更新节点

以下各节假定您已设置请求服务器。 如果不设置拉取服务器，则可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。 本文将演示如何上传的资源，以便它们可供下载，并配置客户端会自动下载资源。 当该节点的收到的已分配的配置，通过**拉取**或**推送**(v5)，则会自动下载所需的 LCM 中指定的位置中的配置的任何资源。

## <a name="using-the-update-dscconfiguration-cmdlet"></a>使用 Update-dscconfiguration cmdlet

从 PowerShell 5.0 中，开始[Update-dscconfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet，强制更新其状态从拉服务器配置 LCM 中的节点。

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>使用调用 CIMMethod

在 PowerShell 4.0 中，可以仍手动强制请求客户端，以更新其配置中使用[Invoke-cimmethod](/powershell/module/cimcmdlets/invoke-cimmethod)。 下面的示例使用指定的凭据创建 CIM 会话、 调用相应的 CIM 方法和删除该会话。

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>另请参阅

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
