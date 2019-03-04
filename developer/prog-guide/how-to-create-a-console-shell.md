---
title: 如何创建控制台 Shell |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853493"
---
# <a name="how-to-create-a-console-shell"></a>如何创建控制台 Shell

Windows PowerShell 提供了使 Shell 工具，也称为"请-工具包"，用于创建不可扩展的控制台 shell。 使用此新工具创建的 shell 不能通过 Windows PowerShell 管理单元的更高版本扩展。

## <a name="syntax"></a>语法

下面是用于运行使 Shell 从生成文件中的语法。

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>参数

下面是使 Shell 的参数的简要说明。

> [!CAUTION]
> 通过使 Shell 不支持程序集的 UNC 路径。

|参数|描述|
|---------------|-----------------|
|-out n.exe|必需。 命令行程序生成的名称。 路径指定为此参数的一部分。<br /><br /> 如果未指定，使 shell 会将".exe"追加到此值。 **注意：** 不要创建输出文件具有相同名称与引用的.dll 文件。 如果尝试这样做，请 Shell 工具将创建具有相同的名称，这将覆盖具有 cmdlet 源代码的.cs 文件的.cs 文件。|
|命名空间 ns|必需。 要用于派生的命名空间[System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration)品牌工具包生成和编译的类。|
|-lib libdirectory1[,libdirectory2,..]|对于.NET 程序集，包括 Windows PowerShell 程序集，通过指定的程序集搜索的目录`reference`参数、 间接引用另一个程序集的程序集和.NET 系统程序集。|
|-reference ca1.dll[,ca2.dll,...]|逗号分隔的要包括在 shell 中的程序集列表。 这些程序集包括所有 cmdlet 和提供程序程序集，以及应加载的资源程序集。 如果未指定此参数，然后一个外壳会生成包含核心 cmdlet 和提供的 Windows PowerShell 提供程序。<br /><br /> 可以使用其完整路径指定程序集，否则将使用指定的路径搜索它们`lib`参数。|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|要包括在 shell 中的格式数据的以逗号分隔列表。 如果未指定此参数，然后一个外壳会生成包含由 Windows PowerShell 提供的格式数据。|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|若要包括在 shell 中的数据类型以逗号分隔列表。 如果未指定此参数，然后一个外壳会生成包含由 Windows PowerShell 提供的类型数据。|
|-source c1.cs [,c2.cs,...]|提供的命令行程序开发人员，包含生成命令行程序所需的任何源代码的文件的名称。<br /><br /> 源代码文件可以包含任何以下源代码：<br /><br /> -重写默认授权管理器授权管理器实现。 （这可能还提供编译成程序集。）<br />程序集信息性特性声明： 如 AssemblyCompanyAttribute、 AssemblyCopyrightAttribute、 AssemblyFileVersionAttribute、 AssemblyInformationalVersionAttribute、 AssemblyProductAttribute，和AssemblyTrademarkAttribute。|
|-authorizationmanager authorizationManagerType|包含授权管理器实现的类型。 这可定义在源代码中，或编译到程序集 (由指定`reference`参数)。 如果未指定此参数，则使用默认的安全管理器。 值应为完整类型名称，包括命名空间。|
|-win32icon i.ico|命令行程序.exe 文件的图标。 如果未指定，shell 将具有 c# 编译器包含 （如果有） 的图标。|
|-initscript p.ps1|在 shell 启动配置文件。 该文件是包含"作为-是";没有有效性检查，可以使 Shell。|
|-builtinscript s1.ps1[,s2.ps1,...]|Shell 的内置脚本的列表。 在路径中，脚本之前发现这些脚本和命令行程序构建后不能更改其内容。<br /><br /> 将包含这些文件"作为-是";没有有效性检查，可以使 Shell。|
|-资源 resourcefile.txt|包含帮助和横幅 shell 的资源的.txt 文件。 第一个资源命名 ShellHelp，并且包含当 shell 调用使用了显示的文本`help`参数。 第二个资源命名 ShellBanner，并且它包含的文本和 shell 在交互模式下启动时显示的版权信息。<br /><br /> 如果未提供此参数，或这些资源不存在，则泛型帮助和横幅使用。|
|-cscflags cscFlags|标志应传递给C#编译器 (csc.exe)。 这些是通过传递不变。 如果此参数包含空格，它应该括在双引号中。|
|-?<br /><br /> -help|显示版权消息和使 Shell 命令行选项。|
|-verbose|在创建外壳程序时显示的详细信息。|

## <a name="see-also"></a>另请参阅

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)