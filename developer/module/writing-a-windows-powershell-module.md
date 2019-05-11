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
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229342"
---
# <a name="writing-a-windows-powershell-module"></a>编写 Windows PowerShell 模块

本文档面向管理员、 脚本开发人员和 cmdlet 的开发人员需要打包并分发其 Windows PowerShell cmdlet。 通过使用 Windows PowerShell 模块，可打包并分发你的 Windows PowerShell 解决方案，而无需使用经过编译的语言。

Windows PowerShell 模块可以对分区、 组织和抽象化成独立的、 可重用单元的 Windows PowerShell 代码。 使用这些可重用单元，可以轻松共享您直接与其他人的模块。 如果您是脚本开发人员，您还可以重新打包第三方模块来创建自定义基于脚本的应用程序。 模块，类似于如 Perl 和 Python，其他脚本语言中的模块，生产的脚本解决方案与优点，使你能够重新打包和抽象到多个组件一起使用可重用、 可再发行组件创建自定义解决方案。

在其最基本的 Windows PowerShell 会将保存为模块的.psm1 文件中任何有效的 Windows PowerShell 脚本代码。 PowerShell 还会自动将视为二进制 cmdlet 的任何程序集模块。 但是，您还可以使用模块 （或更具体地说，模块清单） 捆绑在一起的整个解决方案。 以下方案说明 Windows PowerShell 模块的典型用途。

### <a name="libraries"></a>库

模块可用于打包并分发内聚库执行常见任务的函数。 通常情况下，这些函数的名称共享反映它们的用途的常见任务的一个或多个名词。 这些函数也可以是类似于.NET Framework 类，都可以具有公共和私有成员。 例如，一个库可以包含一组函数的文件传输。 在这种情况下，（） 名词，专用于反映将常见的任务可能是"文件。

### <a name="configuration"></a>配置

模块可用于通过添加特定的 cmdlet、 提供程序、 函数和变量来自定义您的环境。

### <a name="compiled-code-development-and-distribution"></a>已编译的代码开发和分发

Cmdlet 和提供程序开发人员可以使用模块来测试和分发其编译的代码而无需创建管理单元。他们可以将包含已编译的代码作为模块 （二进制模块） 的程序集，而无需创建并注册管理单元。

## <a name="see-also"></a>另请参阅

[了解 Windows PowerShell 模块](./understanding-a-windows-powershell-module.md)

[如何编写 PowerShell 脚本模块](./how-to-write-a-powershell-script-module.md)

[如何编写 PowerShell 二进制模块](./how-to-write-a-powershell-binary-module.md)

[如何编写 PowerShell 模块清单](how-to-write-a-powershell-module-manifest.md)

[修改 PSModulePath 安装路径](./modifying-the-psmodulepath-installation-path.md)

[正在导入 PowerShell 模块](./importing-a-powershell-module.md)

[安装 PowerShell 模块](./installing-a-powershell-module.md)
