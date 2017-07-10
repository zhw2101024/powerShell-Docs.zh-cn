---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="how-to-resolve-warning-package-your-package-name-failed-to-download-issue" class="xliff"></a>
## 如何解决“警告: 无法下载包‘你的包名称’”问题？




据报告，Install-Module 或 Update-Module 在某些计算机上有时会失败。
根据我们的调查，此问题与网络连接有关。
最近，我们更新了 NuGet 提供程序，使其可以可靠地下载包。
你可以按照以下说明安装 NuGet 提供程序的最新版本，然后安装或更新你的模块。
下面，我们使用“Azure”模块作为示例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

