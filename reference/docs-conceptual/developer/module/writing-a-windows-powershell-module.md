---
title: 编写 Windows PowerShell 模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360616"
---
# <a name="writing-a-windows-powershell-module"></a>编写 Windows PowerShell 模块

本文档针对需要打包和分发其 Windows PowerShell cmdlet 的管理员、脚本开发人员和 cmdlet 开发人员编写。 通过使用 Windows PowerShell 模块，无需使用编译语言即可打包和分发 Windows PowerShell 解决方案。

使用 windows PowerShell 模块，可以将 Windows PowerShell 代码分区、组织和抽象到独立的可重用单元中。 使用这些可重用单元，可以轻松地与他人直接共享你的模块。 如果你是脚本开发人员，还可以重新打包第三方模块，以创建基于脚本的自定义应用程序。 模块与其他脚本语言（如 Perl 和 Python）中的模块相似，可实现使用可重用的可再发行组件的生产就绪脚本解决方案，并提供使你能够将多个组件重新打包和抽象到创建自定义解决方案。

在最基本的情况下，Windows PowerShell 会将 hbase-runner.psm1 文件中保存的任何有效的 Windows PowerShell 脚本代码视为模块。 PowerShell 还会将任何二进制 cmdlet 程序集自动视为模块。 但是，您还可以使用模块（或更具体地说，模块清单）将整个解决方案捆绑在一起。 以下方案介绍了 Windows PowerShell 模块的典型用法。

### <a name="libraries"></a>库

模块可用于打包和分发执行常见任务的具有相同功能的库。 通常情况下，这些函数的名称共享一个或多个名词，其中反映了它们所使用的常见任务。 这些函数也可以与 .NET Framework 类类似，因为它们可以拥有公共和私有成员。 例如，库可以包含一组用于文件传输的函数。 在这种情况下，反映常见任务的名词可能是 "file"。

### <a name="configuration"></a>配置

通过添加特定的 cmdlet、提供程序、函数和变量，可使用模块自定义环境。

### <a name="compiled-code-development-and-distribution"></a>编译的代码开发和分发

Cmdlet 和提供程序开发人员可以使用模块来测试和分发其已编译的代码，而无需创建管理单元。用户可以将包含已编译代码的程序集作为模块（二进制模块）导入，而无需创建和注册管理单元。

## <a name="see-also"></a>另请参阅

[了解 Windows PowerShell 模块](./understanding-a-windows-powershell-module.md)

[如何编写 PowerShell 脚本模块](./how-to-write-a-powershell-script-module.md)

[如何编写 PowerShell 二进制模块](./how-to-write-a-powershell-binary-module.md)

[如何编写 PowerShell 模块清单](how-to-write-a-powershell-module-manifest.md)

[修改 PSModulePath 安装路径](./modifying-the-psmodulepath-installation-path.md)

[导入 PowerShell 模块](./importing-a-powershell-module.md)

[安装 PowerShell 模块](./installing-a-powershell-module.md)
