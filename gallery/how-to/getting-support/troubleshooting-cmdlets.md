---
ms.date: 06/12/2017
contributor: manikb
keywords: 库,powershell,cmdlet,psget
title: cmdlet 故障排除
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892468"
---
# <a name="troubleshooting-cmdlets"></a>cmdlet 故障排除

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>如何解决“警告: 无法下载包‘你的包名称’”问题

收到 `Install-Module` 或 `Update-Module` 有时在某些计算机上失败的报告。
根据我们的调查，此问题与网络连接有关。
最近，我们更新了 NuGet 提供程序，使其可以可靠地下载包。
你可以按照以下说明安装 NuGet 提供程序的最新版本，然后安装或更新你的模块。
下面，我们使用“Azure”模块作为示例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```