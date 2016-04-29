---
title: Windows PowerShell 术语表
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
---
# Windows PowerShell 术语表


|术语|定义|
|--------|--------------|
|二进制模块|一个 Windows PowerShell 模块，其根模块是一个二进制模块文件 (.dll)。 二进制模块可能包含或不包含模块清单。|
|通用参数|一个参数，它由 Windows PowerShell 引擎添加到所有 cmdlet 和高级函数中。|
|使用点获取来源|在 Windows PowerShell 中，若要启动一个命令，可在该命令前键入一个点和一个空格。 采用点获取其来源的命令运行在当前范围而非新范围中。 命令创建的任何变量、别名、函数或驱动器都创建于当前范围，并在命令完成时提供给用户。|
|动态模块|一个仅存在于内存中的模块。 Import-PSSession cmdlet 创建动态模块。|
|动态参数|在某些情况下添加到 Windows PowerShell cmdlet、函数或脚本的一个参数。 Cmdlet、函数、提供程序和脚本可以添加动态参数。|
|格式设置文件|一个 Windows PowerShell XML 文件，它具有 .format.ps1xml 扩展名且定义 Windows PowerShell 如何基于对象的 .NET Framework 类型来显示对象。|
|全局会话状态|包含 Windows PowerShell 会话用户可访问的数据的会话状态。|
|主机|Windows PowerShell 引擎用于与用户进行通信的接口。 例如，主机指定 Windows PowerShell 和用户之间处理提示的方式。|
|主机应用程序|将 Windows PowerShell 引擎加载到其进程中并使用它执行操作的程序。|
|输入处理方法|Cmdlet 可用于处理其以输入形式所接收的记录的一种方法。 输入处理方法包括 BeginProcessing 方法、ProcessRecord 方法、EndProcessing 方法以及 StopProcessing 方法。|
|清单模块|一个 Windows PowerShell 模块，它具有一个清单且其 ModulesToProcess 项为空。|
|模块清单|一个 Windows PowerShell 数据文件 (.psd1)，描述模块的内容并控制模块的处理方式。|
|模块会话状态|包含 Windows PowerShell 模块公用和专用数据的会话状态。 此会话状态中的私有数据不可供 Windows PowerShell 会话的用户使用。|
|非终止错误|不能阻止 Windows PowerShell 继续处理命令的错误。|
|名词|在 Windows PowerShell cmdlet 名称中连字符后面的单词。 名词描述了 cmdlet 在其上进行操作的资源。|
|参数集|可用于相同的命令中以执行特定操作的一组参数。|
|管|在 Windows PowerShell 中，将前一个命令的结果作为输入发送到管道中的下一个命令。|
|管道|一系列由管道运算符 (&#124;) (ASCII 124) 连接的命令。 每个管道运算符将前一个命令的结果作为输入发送到下一个命令。|
|PSSession|一种由用户创建、管理和关闭的 Windows PowerShell 会话类型。|
|根模块|模块清单中在 ModuleToProcess 项中指定的模块。|
|运行空间|在 Windows PowerShell 中，在其中执行管道中每个命令的操作环境。|
|脚本块|在 Windows PowerShell 编程语言中，可作为单个单元使用的语句或表达式的一个集合。 脚本块可以接受参数并返回值。|
|脚本模块|一个 Windows PowerShell 模块，其根模块是一个脚本模块文件 (.psm1)。 脚本模块可能包含或不包含模块清单。|
|脚本模块文件|一个包含 Windows PowerShell 脚本的文件。 该脚本定义脚本模块导出的成员。 脚本模块文件具有 .psm1 文件扩展名。|
|shell|用于将命令传递到操作系统的命令解释器。|
|开关参数|一个不带实参的形参。|
|终止错误|阻止 Windows PowerShell 处理命令的错误。|
|事务|一个工作的原子单元。 必须将事务中的工作作为一个整体来完成；如果该事务的任何部分失败，那么整个事务都会失败。|
|类型文件|一个 Windows PowerShell XML 文件，它具有 .ps1xml 扩展名且扩展 Windows PowerShell 中 Microsoft.NET Framework 类型的属性。|
|动作|在 Windows PowerShell cmdlet 名称中连字符前面的单词。 它说明该 cmdlet 将执行的操作。|
|Windows PowerShell|为 IT 管理员提供全面控制以及实现系统管理任务自动化的一个命令行 Shell 和基于任务的脚本技术。|
|Windows PowerShell 命令|导致操作被执行的管道中的元素。 Windows PowerShell 命令可以在键盘上输入或以编程方式调用。|
|Windows PowerShell 数据文件|具有 .psd1 文件扩展名的文本文件。 Windows PowerShell 将数据文件用于多种用途，例如存储模块清单数据和存储用于脚本国际化的已翻译的字符串。|
|Windows PowerShell 驱动器|一个提供直接访问数据存储的虚拟驱动器。 它可以由 Windows PowerShell 提供程序定义或是在命令行中创建。 在命令行创建的驱动器是特定于会话的驱动器，并在会话关闭时丢失。|
|Windows PowerShell 集成脚本环境 (ISE)|一个 Windows PowerShell 主机应用程序，使你能够运行命令并在友好、语法着色、符合 Unicode 的环境中编写、测试和调试脚本。|
|Windows PowerShell 模块|一个独立的可重用单元，使你能够对 Windows PowerShell 代码进行分区、组织和抽象化。 模块可以包含 cmdlet、提供程序、函数、变量和其他可作为单个单元导入的资源类型。|
|Windows PowerShell 提供程序|一个基于 Microsoft .NET Framework 的程序，用于使专用数据存储中的数据在 Windows PowerShell 中可用，以便你可以查看和管理它。|
|Windows PowerShell 脚本|以 Windows PowerShell 语言编写的脚本。|
|Windows PowerShell 脚本文件|具有 .ps1 扩展名且包含以 Windows PowerShell 语言编写的脚本的文件。|
|Windows PowerShell 管理单元|定义一组可以添加到 Windows PowerShell 环境中的 cmdlet、提供程序和 Microsoft .NET Framework 的资源。|
|[!INCLUDE[wps_2](../Token/wps_2_md.md)] 工作流|工作流是一系列经过编程的连接步骤，会执行长期运行的任务，或是需要在多个设备或托管节点之间协调多个步骤。 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 工作流使 IT 专业人员和开发人员可以按工作流的形式创作一系列多设备管理活动，或工作流中的单一任务。 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 工作流使你能够调整并将 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 脚本和 XAML 作为工作流运行。|



<!--HONumber=Apr16_HO1-->


