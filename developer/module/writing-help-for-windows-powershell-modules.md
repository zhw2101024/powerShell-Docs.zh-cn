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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082018"
---
# <a name="writing-help-for-windows-powershell-modules"></a>编写针对 Windows PowerShell 模块的帮助

Windows PowerShell 模块可以包含有关该模块以及模块成员，如 cmdlet、 提供程序、 函数和脚本帮助主题。 `Get-Help` Cmdlet 显示模块的帮助主题中的相同的格式为它的其他 Windows PowerShell 项，显示的帮助，而用户使用标准`Get-Help`命令以获取帮助主题。

本文档介绍的格式和模块帮助主题的正确位置并建议模块的帮助内容的指导原则。

## <a name="types-of-module-help"></a>类型的模块的帮助

模块可以包含以下类型的帮助。

- **Cmdlet 帮助**。 介绍在模块中的 cmdlet 的帮助主题是使用命令的 XML 文件可帮助架构

- **提供程序帮助**。 描述在模块中的提供程序的帮助主题是使用提供程序的 XML 文件可帮助架构。

- **函数帮助**。 可以使用命令的 XML 文件可帮助架构或函数，或在脚本或脚本模块中基于注释的帮助主题介绍在模块中的函数的帮助主题

- **脚本帮助**。 可以使用命令的 XML 文件可帮助架构或在脚本或脚本模块中基于注释的帮助主题介绍在模块中的脚本的帮助主题。

- **（"关于"） 帮助**。 描述的模块，并且其成员还将说明如何成员可以共同用于执行任务，您可以使用概念 （"关于"） 帮助主题。 概念帮助主题是使用 Unicode (utf-8) 编码的文本文件。 文件名称必须使用`about_<name>.help.txt`格式，如 about_MyModule.help.txt。 默认情况下，Windows PowerShell 包括超过 100 个概念有关帮助主题，并且它们的格式如下例所示。

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

## <a name="placement-of-module-help"></a>模块的帮助的位置

`Get-Help` Cmdlet 查找模块在模块目录的特定于语言的子目录中的帮助主题文件。

例如，以下目录结构关系图显示了有关 SampleModule 模块的帮助主题的位置。

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
> 在示例中，  *\<ModulePath >* 占位符表示中的路径之一`PSModulePath`环境变量，如 $home\Documents\Modules、 $pshome\Modules 或用户指定的自定义路径。

## <a name="getting-module-help"></a>获取模块的帮助

当用户将模块导入到会话时，该模块的帮助主题是导入到连同该模块的会话。 可以列出在模块清单中，文件列表项的值中的帮助主题文件，但不是受影响的帮助主题`Export-ModuleMember`cmdlet。

你可以提供不同的语言中的模块的帮助主题。 `Get-Help` Cmdlet 会自动显示为控制面板中的区域和语言选项项中的当前用户指定的语言中的模块的帮助主题。 在 Windows Vista 和更高版本的 Windows，`Get-Help`搜索根据建立 Windows 语言回退标准在模块目录的特定于语言的子目录中的帮助主题。

从运行的 Windows PowerShell 3.0 开始`Get-Help`cmdlet 或函数的命令触发自动导入的模块。 `Get-Help` Cmdlet 模块中将立即显示帮助主题的内容。

如果该模块不包含帮助主题，并且不会有帮助主题中用户的计算机上的模块命令`Get-Help`显示自动生成的帮助。 自动生成的帮助命令语法、 参数和输入和输出类型，包括但不包括任何说明。 自动生成帮助中包含文本，引导用户尝试使用`Update-Help`cmdlet 以从 Internet 或文件共享下载有关命令的帮助。 它还建议使用**联机**参数的`Get-Help`cmdlet 来获取帮助主题的联机版本。

## <a name="supporting-updatable-help"></a>支持可更新的帮助

用户的 Windows PowerShell 3.0 和更高版本的 Windows PowerShell 可以下载并安装的模块更新的帮助文件，从 Internet 还是从本地文件共享。 `Update-Help`和`Save-Help`cmdlet 隐藏用户的管理详细信息。 用户在运行`Update-Help`cmdlet，然后使用`Get-Help`cmdlet 来读取在 Windows PowerShell 命令提示符下的模块的最新帮助文件。 用户不需要重新启动 Windows 或 Windows PowerShell。

防火墙以及那些没有 Internet 访问权限的用户可以使用可更新帮助。 管理员具有 Internet 访问，请使用`Save-Help`cmdlet 来下载并安装到文件共享的最新帮助文件。 然后，用户使用**路径**参数的`Update-Help`cmdlet 来获取最新帮助文件从文件共享。

模块作者可以在模块中包含帮助文件，并使用可更新帮助以更新的帮助文件，或忽略模块的帮助文件并使用可更新的帮助来安装并更新它们。

有关可更新帮助的详细信息，请参阅[支持可更新帮助](./supporting-updatable-help.md)。

## <a name="supporting-online-help"></a>支持联机帮助

不能或不安装的用户更新其计算机上的文件通常依赖于模块的帮助主题的联机版本的帮助。 **联机**参数的`Get-Help`cmdlet 及其默认 Internet 浏览器中打开 cmdlet 或用户的高级的函数帮助主题的联机版本。

`Get-Help` Cmdlet 使用的值**HelpUri** cmdlet 或函数，以便查找帮助主题的联机版本的属性。

从 Windows PowerShell 3.0 开始，可帮助用户通过在 cmdlet 类上定义的 HelpUri 属性中查找 cmdlet 和函数的帮助主题的联机版本或**HelpUri**属性的**CmdletBinding**属性。 属性的值为的值**HelpUri** cmdlet 或函数的属性。

有关详细信息，请参阅[支持联机帮助](./supporting-online-help.md)。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 模块](./writing-a-windows-powershell-module.md)

[支持可更新帮助](./supporting-updatable-help.md)

[支持联机帮助](./supporting-online-help.md)