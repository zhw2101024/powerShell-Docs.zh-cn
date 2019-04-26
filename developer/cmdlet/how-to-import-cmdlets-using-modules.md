---
title: 如何使用模块的 Cmdlet 导入 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067971"
---
# <a name="how-to-import-cmdlets-using-modules"></a>如何使用模块导入 Cmdlet

本主题介绍如何通过使用二进制模块导入的 Windows PowerShell 会话的 cmdlet。

> [!NOTE]
> 模块的成员可以包括 cmdlet、 提供程序、 函数、 变量、 别名和其他更多。 管理单元只能包含 cmdlet 和提供程序。

## <a name="how-to-load-cmdlets-using-a-module"></a>如何加载使用模块的 cmdlet

1. 创建具有相同的名称与程序集文件中实现这些 cmdlet 的模块文件夹。 在此过程中，模块文件夹中创建`system32`文件夹。

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. 请确保`PSModulePath`环境变量包含新的模块文件夹的路径。 默认情况下，系统文件夹已添加到`PSModulePath`环境变量。

3. 将 cmdlet 程序集复制到模块文件夹中。

4. 运行以下命令以将 cmdlet 添加到会话：

   `import-module [Module_Name]`

   此过程可以用于测试 cmdlet。 它将所有的 cmdlet 添加到该会话在程序集中。 不同类型的模块，若要加载的模块，以及如何限制将导出的模块元素的不同方式有关模块的详细信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[安装模块](../module/installing-a-powershell-module.md)