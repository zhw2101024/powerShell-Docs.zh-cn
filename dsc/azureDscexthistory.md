---
description: "了解 Azure 中 Desired State Configuration (DSC) 扩展的版本历史记录。"
ms.date: 2018-03-14
ms.topic: conceptual
keywords: "dsc, powershell, azure, 扩展"
title: "Azure DSC 扩展版本历史记录"
author: DCtheGeek
ms.author: dacoulte
ms.openlocfilehash: e324ff9db2aff36a7e13c3a222e3c50f6f1c5d39
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Azure Desired State Configuration 扩展版本历史记录

已根据需要更新 Azure Desired State Configuration (DSC) VM 扩展，以支持 Azure、Windows Server 和 Windows Management Framework (WMF) 提供的包含 Windows PowerShell 的增强功能和新功能。

本文将提供有关每个版本的 Azure DSC VM 扩展的信息、它支持的环境，以及对新功能或更改的注释与说明。

## <a name="latest-versions"></a>最新版本

### <a name="version-275"></a>版本 2.75

- **发布日期：**
  - 2018 年 3 月 5 日
- **OS 支持：**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Windows 客户端 7/8.1/10
  - Nano Server
- **WMF 支持：**
  - WMF 5.1
  - WMF 5.0 RTM
  - WMF 4.0 更新
  - WMF 4.0
- **环境：**
  - Azure
- **备注：**此版本使用包括在 Windows Server 2016 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/)（安装 WMF 需要重启）。 对于 Nano，DSC 角色安装在 VM 上。
- **新功能：**
  - 在 Github 最近移动到 TLS 1.2 后，无法使用 Azure Marketplace 中的 DIY 资源管理器模板将 VM 载入到 Azure 自动化 DSC，或使用 DSC 扩展来获取托管在 Github 上的任何配置。 部署扩展时将看到类似如下的错误：

    ```json
    {
        "code": "DeploymentFailed",
        "message": "At least one resource deployment operation failed. Please list deployment operations for details. Please see https://aka.ms/arm-debug for usage details.",
        "details": [{
            "code": "Conflict",
            "message": "{
                \"status\": \"Failed\",
                \"error\": {
                    \"code\": \"ResourceDeploymentFailure\",
                    \"message\": \"The resource operation completed with terminal provisioning state 'Failed'.\",
                    \"details\": [ {
                        \"code\": \"VMExtensionProvisioningError\",
                        \"message\": \"VM has reported a failure when processing extension 'Microsoft.Powershell.DSC'.
                        Error message: \\\"The DSC Extension failed to execute: Error downloading
                        https://github.com/Azure/azure-quickstart-templates/raw/master/dsc-extension-azure-automation-pullserver/UpdateLCMforAAPull.zip
                        after 29 attempts: The request was aborted: Could not create SSL/TLS secure channel..\\nMore information about the failure can
                        be found in the logs located under 'C:\\\\WindowsAzure\\\\Logs\\\\Plugins\\\\Microsoft.Powershell.DSC\\\\2.74.0.0' on the VM.\\\".\"
                    } ]
                }
            }"
        }]
    }
    ```

  - 在新的扩展版本中，现已强制执行 TLS 1.2。 部署扩展时，如果资源管理器模板中已具有 AutoUpgradeMinorVersion = true ，则该扩展将自动升级到 2.75。 若要进行手动更新，请在资源管理器模板中指定 `TypeHandlerVersion = 2.75`。

### <a name="version-219"></a>版本 2.19

- **发布日期：**
  - 2016 年 6 月 3 日
- **OS 支持：**
  - Windows Server 2016 Technical Preview
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
- **WMF 支持：**
  - WMF 5.0 RTM
  - WMF 4.0 更新
  - WMF 4.0
- **环境：**
  - Azure
  - Azure 中国
  - Azure 政府
- **备注：**此版本使用包括在 Windows Server 2016 Technical Preview 中的 DSC；对于其他 OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。
- **新功能：**
  - DSC 扩展现已在 Azure 中国投入使用。 此版本主要包含在 Azure 中国上运行扩展的修补程序。

## <a name="supported-versions"></a>支持的版本

> [!WARNING]
> 版本 2.4 至 2.13 使用 WMF 5.0 公共预览版，其签名证书在 2016 年 8 月过期。  有关此问题的详细信息，请参阅[博客文章](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/)。

### <a name="version-270---272"></a>版本 2.70 - 2.72

- **发布日期：**2017 年 11 月 13 日
- **OS 支持：**Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1、Windows 客户端 7/8.1/10、Nano Server
- **WMF 支持：**WMF 5.1、WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/)（安装 WMF 需要重启）。 对于 Nano，DSC 角色安装在 VM 上。
- **新功能：**
  - 进行了 Bug 修复和改进，简化了通过门户 UI 以及资源管理器模板使用 DSC Azure 自动化的过程。  有关详细信息，请参阅 DSC 扩展文档中的[默认配置脚本](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/extensions-dsc-overview#default-configuration-script)。

### <a name="version-226"></a>版本 2.26

- **发布日期：**2017 年 6 月 9 日
- **OS 支持：**Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1、Windows 客户端 7/8.1/10、Nano Server
- **WMF 支持：**WMF 5.1、WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/)（安装 WMF 需要重启）。 对于 Nano，DSC 角色安装在 VM 上。
- **新功能：**
  - 遥测改进。

### <a name="version-225"></a>版本 2.25

- **发布日期：**2017 年 6 月 2 日
- **OS 支持：**Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1、Windows 客户端 7/8.1/10、Nano Server
- **WMF 支持：**WMF 5.1、WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/)（安装 WMF 需要重启）。 对于 Nano，DSC 角色安装在 VM 上。
- **新功能：**
  - 添加了多项 bug 修复和其他小的改进。

### <a name="version-224"></a>版本 2.24

- **发布日期：**2017 年 4 月 13 日
- **OS 支持：**Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1、Nano Server
- **WMF 支持：**WMF 5.1、WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/)（安装 WMF 需要重启）。 对于 Nano，DSC 角色安装在 VM 上。
- **新功能：**
  - 将 VM UUID 和 DSC 代理 ID 公开为扩展元数据。 添加了其他小的改进。

### <a name="version-223"></a>版本 2.23

- **发布日期：**2017 年 3 月 15 日
- **OS 支持：**Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1、Nano Server
- **WMF 支持：**WMF 5.1、WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/)（安装 WMF 需要重启）。 对于 Nano，DSC 角色安装在 VM 上。
- **新功能：**
  - 添加了多项 bug 修复和其他改进。

### <a name="version-222"></a>版本 2.22

- **发布日期：**2017 年 2 月 8 日
- **OS 支持：**Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1、Nano Server
- **WMF 支持：**WMF 5.1、WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/)（安装 WMF 需要重启）。 对于 Nano，DSC 角色安装在 VM 上。
- **新功能：**
  - DSC 扩展现在支持 WMF 5.1。
  - 添加了其他小的改进。

### <a name="version-221"></a>版本 2.21

- **发布日期：**2016 年 12 月 2 日
- **OS 支持：**Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1、Nano Server
- **WMF 支持：**WMF 5.1 预览版、WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。 对于 Nano，DSC 角色安装在 VM 上。
- **新功能：**
  - 现在可在 Nano Server 上使用 DSC 扩展。 此版本主要包含用于在 Nano Server 上运行扩展的代码更改。
  - 添加了其他小的改进。

### <a name="version-220"></a>版本 2.20

- **发布日期：**2016 年 8 月 2 日
- **OS 支持：**Windows Server 2016 Technical Preview、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1
- **WMF 支持：**WMF 5.1 预览版、WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 Technical Preview 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。
- **新功能：**
  - 支持 WMF 5.1 预览版。 此版本在首次发布时是一个可选升级，必须在资源管理器模板中指定 Wmfversion =“5.1PP”来安装 WMF 5.1 预览版。 若 Wmfversion =“latest”，则仍安装 [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)。 有关 WMF 5.1 预览版的详细信息，请参阅[此博客]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/)。
  - 添加了其他小的修复和改进。

### <a name="version--219"></a>版本 2.19

- **发布日期：**2016 年 6 月 3 日
- **OS 支持：**Windows Server 2016 Technical Preview、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1
- **WMF 支持：**WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure、Azure 中国、Azure 政府
- **备注：**此版本使用包括在 Windows Server 2016 Technical Preview 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。
- **新功能：**
  - DSC 扩展现已在 Azure 中国投入使用。 此版本主要包含在 Azure 中国上运行扩展的修补程序。

### <a name="version-218"></a>版本 2.18

- **发布日期：**2016 年 6 月 3 日
- **OS 支持：**Windows Server 2016 Technical Preview、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1
- **WMF 支持：**WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 Technical Preview 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。
- **新功能：**
  - 当遥测修补程序下载（已知 Azure DNS 问题）或安装期间出现错误时不阻止遥测。
  - 修复了扩展在重启后停止处理配置的间歇性问题。 这将导致 DSC 扩展仍然处于“正在转换”状态。
  - 添加了其他小的修复和改进。

### <a name="version-217"></a>版本 2.17

- **发布日期：**2016 年 4 月 26 日
- **OS 支持：**Windows Server 2016 Technical Preview、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1
- **WMF 支持：**WMF 5.0 RTM、WMF 4.0 更新、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 Technical Preview 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。
- **新功能：**
  - 支持 WMF 4.0 更新。 有关 WMF 4.0 更新的详细信息，请参阅[此博客](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/)。
  - 针对在 DSC 扩展安装期间或在扩展安装后应用 DSC 配置时出现的错误的重试逻辑。 作为此更改的一部分，如果之前安装失败或重新执行之前失败的 DSC 配置，则扩展将至多重试安装三次，直到达到完成状态（成功/错误）或传入新请求。 如果扩展因无效的用户设置/用户输入失败，则不会重试。 在这种情况下，需要使用新的请求和正确的用户设置再次调用扩展。 注意：DSC 扩展依赖于重试的 Azure VM 代理。 Azure VM 代理使用最后失败的请求调用扩展，直到达到成功或错误状态。

### <a name="version-216"></a>版本 2.16

- **发布日期：**2016 年 4 月 21 日
- **OS 支持：**Windows Server 2016 Technical Preview、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1
- **WMF 支持：**WMF 5.0 RTM、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 Technical Preview 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。
- **新功能：**
  - 错误处理的改进和其他小的 bug 修复。
  - DSC 扩展设置中的新属性。 已添加 AdvancedOptions 中的“ForcePullAndApply”，以便使 DSC 扩展在刷新模式为拉取（与默认的推送模式相反）时执行 DSC 配置。 有关详细信息，请参阅[此博客](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/)，获取有关 DSC 扩展设置的详细信息。

### <a name="version-215"></a>版本 2.15

- **发布日期：**2016 年 3 月 14 日
- **OS 支持：**Windows Server 2016 Technical Preview、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1
- **WMF 支持：**WMF 5.0 RTM、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 Technical Preview 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。
- **新功能：**
  - 在扩展版本 2.14 中，包括了对安装 WMF RTM 的更改。 从扩展版本 2.13.2.0 升级到 2.14.0.0 时，你可能会注意到某些 DSC cmdlet 失败或配置失败，并出现错误“未找到含给定属性值的实例”。 有关详细信息，请参阅 [DSC 发行说明](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc)。 2.15 版中已添加这些问题的解决方法。
  - 遗憾的是，如果你已安装版本 2.14 且遇到上述两个问题之一，则将需要手动执行这些步骤。  在提升的 PowerShell 会话中：
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>版本 2.14

- **发布日期：**2016 年 2 月 25 日
- **OS 支持：**Windows Server 2016 Technical Preview、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 SP1
- **WMF 支持：**WMF 5.0 RTM、WMF 4.0
- **环境：**Azure
- **备注：**此版本使用包括在 Windows Server 2016 Technical Preview 中的 DSC；对于其他 Windows OS，它将安装 [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/)（安装 WMF 需要重启）。
- **新功能：**
  - 使用 WMF RTM。
  - 启用数据收集，以提高 DSC 扩展的质量。 有关详细信息，请参阅[博客](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/)。
  - 在资源管理器模板中为扩展提供更新的设置格式。 有关详细信息，请参阅[博客](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/)。
  - Bug 修复和其他增强功能。

## <a name="next-steps"></a>后续步骤

- 有关 PowerShell DSC 的详细信息，请转到 [PowerShell 文档中心](overview.md)。
- 检查 [DSC 扩展的资源管理器模板](/azure/virtual-machines/windows/extensions-dsc-template)。
- 有关可使用 PowerShell DSC 管理的更多功能及更多 DSC 资源，请浏览 [PowerShell gallery](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0)（PowerShell 库）。
- 有关将敏感参数传递到配置的详细信息，请参阅[使用 DSC 扩展处理程序安全管理凭据](/azure/virtual-machines/windows/extensions-dsc-credentials)。