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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360666"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>修改 PSModulePath 安装路径

@No__t-0 环境变量将路径存储到磁盘上安装的模块的位置。 当用户未指定模块的完整路径时，Windows PowerShell 使用此变量来查找模块。 此变量中的路径按它们出现的顺序进行搜索。

当 Windows PowerShell 启动时，将 `PSModulePath` 创建为具有以下默认值的系统环境变量： `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`。

## <a name="to-view-the-psmodulepath-variable"></a>查看 PSModulePath 变量

若要查看在 `PSModulePath` 变量中指定的路径，请键入以下命令：

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>向 PSModulePath 变量添加位置

若要向此变量添加路径，请使用以下方法之一：

- 若要添加仅适用于当前会话的临时值，请在命令行中运行以下命令：

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- 若要添加在会话打开时可用的永久值，请将以下命令添加到 Windows PowerShell 配置文件：

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  有关配置文件的详细信息，请参阅 Microsoft TechNet 库中的[about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) 。

- 若要向注册表添加持久性变量，请在 "**系统属性**" 对话框中使用环境变量编辑器创建名为 @no__t 的新用户环境变量。

- 若要通过使用脚本来添加持久性变量，请对环境类使用**SetEnvironmentVariable**方法。 例如，下面的脚本将 "C:\Program Files\Fabrikam\Module 路径添加到计算机的 PSModulePath 环境变量的值。 若要将路径添加到 user PSModulePath 环境变量，请将目标设置为 "User"。

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>从 PSModulePath 删除位置

您可以使用类似的方法从变量中移除路径：例如，`$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` 将从当前会话中删除**c:\ModulePath**路径。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)
