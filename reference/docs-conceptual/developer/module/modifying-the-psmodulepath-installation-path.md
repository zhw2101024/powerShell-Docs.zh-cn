---
title: 修改 PSModulePath 安装路径 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953834"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>修改 PSModulePath 安装路径

`PSModulePath` 环境变量将路径存储到磁盘上安装的模块的位置。 当用户未指定模块的完整路径时，PowerShell 将使用此变量来查找模块。 此变量中的路径按它们出现的顺序进行搜索。

启动 PowerShell 时，`PSModulePath` 将创建为具有以下默认值的系统环境变量： Windows PowerShell 的 `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` 或 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules`。

## <a name="to-view-the-psmodulepath-variable"></a>查看 PSModulePath 变量

若要查看在 `PSModulePath` 变量中指定的路径，请键入以下命令：

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>向 PSModulePath 变量添加位置

若要向此变量添加路径，请使用以下方法之一：

- 若要添加仅适用于当前会话的临时值，请在命令行中运行以下命令：

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- 若要添加在会话打开时可用的永久值，请将上述命令添加到 PowerShell 配置文件（`$PROFILE`） >

  有关配置文件的详细信息，请参阅 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。

- 若要向注册表添加持久性变量，请在 "**系统属性**" 对话框中使用环境变量编辑器创建名为 `PSModulePath` 的新用户环境变量。

- 若要通过使用脚本来添加持久性变量，请在[SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable)类上使用 .net[方法。](https://docs.microsoft.com/dotnet/api/system.environment) 例如，以下脚本将 `C:\Program Files\Fabrikam\Module` 路径添加到计算机 `PSModulePath` 环境变量的值。 若要将 `PSModulePath` 环境变量的路径添加到用户，请将 "目标" 设置为 "User"。

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>从 PSModulePath 删除位置

您可以使用类似的方法从变量中移除路径：例如，`$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 将从当前会话中删除**c:\ModulePath**路径。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)
