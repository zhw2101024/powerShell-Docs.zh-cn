---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 从拉取服务器更新节点
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079092"
---
# <a name="update-nodes-from-a-pull-server"></a>从拉取服务器更新节点

以下部分假定你已设置拉取服务器。 如果尚未设置拉取服务器，则可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。 本文将演示如何上传资源以便下载，以及如何将客户端配置为自动下载资源。 当节点通过“拉取”或“推送”(v5) 接收已分配的配置时，将从 LCM 中指定的位置自动下载配置所需的任何资源。

## <a name="using-the-update-dscconfiguration-cmdlet"></a>使用 Update-DSCConfiguration cmdlet

从 PowerShell 5.0 开始，[Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet 强制节点从 LCM 中配置的拉服务器更新其配置。

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>使用 Invoke-CIMMethod

在 PowerShell 4.0 中，仍可以手动强制拉取客户端以使用 [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod) 更新其配置。 以下示例使用指定的凭据创建 CIM 会话、调用相应的 CIM 方法以及删除该会话。

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>另请参阅

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
