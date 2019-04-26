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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082203"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>修改 PSModulePath 安装路径

`PSModulePath`环境变量存储在磁盘上安装的模块的位置的路径。 Windows PowerShell 使用此变量来查找模块时用户未指定模块的完整路径。 按它们的显示的顺序搜索此变量中的路径。

Windows PowerShell 启动时，`PSModulePath`创建为具有以下默认值的系统环境变量： `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`。

## <a name="to-view-the-psmodulepath-variable"></a>若要查看 PSModulePath 变量

若要查看中指定的路径`PSModulePath`变量中，键入以下命令：

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>若要将位置添加到 PSModulePath 变量

若要将路径添加到此变量，使用以下方法之一：

- 若要添加仅用于当前会话的临时值，请在命令行运行以下命令：

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- 若要添加可用的持久值每次打开会话，Windows PowerShell 配置文件中添加以下命令：

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  有关配置文件的详细信息，请参阅[about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) Microsoft TechNet 库中。

- 若要永久性变量添加到注册表，创建名为的新用户环境变量`PSModulePath`使用中的环境变量编辑器**系统属性**对话框。

- 若要使用脚本添加持久性的变量，请使用**SetEnvironmentVariable**环境类上的方法。 例如，以下脚本将添加"C:\Program Files\Fabrikam\Module 路径的计算机的 PSModulePath 环境变量的值。 将该路径添加到用户 PSModulePath 环境变量，请将目标设置为"User"。

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>若要从 PSModulePath 删除位置

您可以从使用类似的方法的变量中删除路径： 例如，`$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"`将删除**c:\ModulePath**从当前会话的路径。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)
