---
title: 为 Windows PowerShell 模块编写帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360556"
---
# <a name="writing-help-for-windows-powershell-modules"></a>编写针对 Windows PowerShell 模块的帮助

Windows PowerShell 模块可以包含有关模块和模块成员（例如 cmdlet、提供程序、函数和脚本）的帮助主题。 @No__t cmdlet 以与为其他 Windows PowerShell 项显示帮助相同的格式显示模块帮助主题，用户使用标准的 @no__t 1 命令获取帮助主题。

本文档说明了模块帮助主题的格式和正确位置，并建议了模块帮助内容的准则。

## <a name="types-of-module-help"></a>模块的类型帮助

模块可以包含以下类型的帮助。

- **Cmdlet 帮助**。 描述模块中的 cmdlet 的帮助主题是使用 command Help 架构的 XML 文件

- **提供程序帮助**。 在模块中描述提供程序的帮助主题是使用提供程序帮助架构的 XML 文件。

- **函数帮助**。 描述模块中的函数的帮助主题可以是 XML 文件，这些文件使用命令帮助架构或在函数中使用基于注释的帮助主题，或者脚本或脚本模块

- **脚本帮助**。 描述模块中的脚本的帮助主题可以是 XML 文件，这些文件使用命令帮助架构或脚本模块中的基于注释的帮助主题。

- **概念（"关于"）帮助**。 您可以使用概念（"关于"）帮助主题描述模块及其成员，并说明如何将成员一起用于执行任务。 概念性帮助主题是带有 Unicode （UTF-8）编码的文本文件。 文件名必须使用 `about_<name>.help.txt` 格式，如 about_MyModule。 默认情况下，Windows PowerShell 包括超过100的有关帮助主题的概念，它们的格式与以下示例类似。

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>模块的位置帮助

@No__t cmdlet 在模块目录的特定于语言的子目录中查找模块帮助主题文件。

例如，下面的目录结构关系图显示了 SampleModule 模块的帮助主题的位置。

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> 在此示例中， *@no__t >* 占位符表示 `PSModulePath` 环境变量中的路径之一，例如 $home \documents\modules、$pshome \modules 或用户指定的自定义路径。

## <a name="getting-module-help"></a>获取模块帮助

当用户将模块导入到会话中时，该模块的帮助主题将与模块一起导入到会话中。 可以在模块清单中的 FileList 键的值中列出帮助主题文件，但帮助主题不受 @no__t cmdlet 的影响。

可以用不同的语言提供模块帮助主题。 @No__t cmdlet 会自动以 "控制面板" 的 "区域和语言选项" 项中为当前用户指定的语言显示模块帮助主题。 在 Windows Vista 和更高版本的 Windows 中，`Get-Help` 在模块目录的特定于语言的子目录中按照为 Windows 建立的语言回退标准搜索帮助主题。

从 Windows PowerShell 3.0 开始，运行 cmdlet 或函数的 `Get-Help` 命令将触发模块的自动导入。 @No__t cmdlet 立即显示模块中帮助主题的内容。

如果该模块不包含帮助主题，而且没有关于用户计算机上模块中的命令的帮助主题，`Get-Help` 会显示自动生成的帮助。 自动生成的帮助包括命令语法、参数、输入和输出类型，但不包含任何说明。 自动生成的帮助包括文本，该文本指示用户尝试使用 `Update-Help` cmdlet 从 Internet 或文件共享下载命令的帮助。 它还建议使用 `Get-Help` cmdlet 的**online**参数获取帮助主题的联机版本。

## <a name="supporting-updatable-help"></a>支持可更新的帮助

Windows PowerShell 3.0 和更高版本的 Windows PowerShell 的用户可以从 Internet 或本地文件共享下载和安装模块的更新帮助文件。 @No__t，`Save-Help` cmdlet 将隐藏用户的管理详细信息。 用户运行 `Update-Help` cmdlet，然后在 Windows PowerShell 命令提示符处使用 @no__t cmdlet 读取模块的最新帮助文件。 用户无需重启 Windows 或 Windows PowerShell。

防火墙之后的用户和无 Internet 访问权限的用户也可以使用可更新的帮助。 具有 Internet 访问权限的管理员使用 `Save-Help` cmdlet 下载最新的帮助文件并将其安装到文件共享。 然后，用户使用 @no__t cmdlet 的**Path**参数从文件共享获取最新的帮助文件。

模块作者可将帮助文件包含在模块中，并使用可更新的帮助来更新帮助文件，或从模块中忽略帮助文件，并使用可更新的帮助来安装和更新这些文件。

有关可更新帮助的详细信息，请参阅[支持可更新帮助](./supporting-updatable-help.md)。

## <a name="supporting-online-help"></a>支持联机帮助

不能或不在其计算机上安装更新的帮助文件的用户通常依赖于模块帮助主题的联机版本。 @No__t cmdlet 的**online**参数将在用户的默认 Internet 浏览器中打开 cmdlet 或高级函数帮助主题的联机版本。

@No__t cmdlet 使用 cmdlet 或函数的**HelpUri**属性的值查找帮助主题的联机版本。

从 Windows PowerShell 3.0 开始，你可以通过在 cmdlet 类上定义 HelpUri 属性或**CmdletBinding**属性的**HelpUri**属性，帮助用户找到 cmdlet 和函数帮助主题的联机版本。 该属性的值为 cmdlet 或函数的**HelpUri**属性的值。

有关详细信息，请参阅[支持联机帮助](./supporting-online-help.md)。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

[支持可更新帮助](./supporting-updatable-help.md)

[支持联机帮助](./supporting-online-help.md)