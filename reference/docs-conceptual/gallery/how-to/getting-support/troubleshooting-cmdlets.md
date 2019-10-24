---
ms.date: 06/12/2017
contributor: manikb
keywords: 库,powershell,cmdlet,psget
title: cmdlet 故障排除
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352107"
---
# <a name="troubleshooting-cmdlets"></a>cmdlet 故障排除

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>如何解决“警告：无法下载包‘你的包名称’”问题

收到 `Install-Module` 或 `Update-Module` 有时在某些计算机上失败的报告。 根据我们的调查，此问题与网络连接有关。 最近，我们更新了 NuGet 提供程序，使其可以可靠地下载包。 你可以按照以下说明安装 NuGet 提供程序的最新版本，然后安装或更新你的模块。 下面，我们使用“Azure”模块作为示例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>所需的网络终结点

安装和更新 cmdlet 需要通过 Internet 访问连接 PowerShell 库使用的网络终结点。 请确保网络访问策略允许连接以下终结点。

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- [www.powershellgallery.com](www.powershellgallery.com)
- devopsgallerystorage.blob.core.windows.net
