---
title: 支持联机帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082135"
---
# <a name="supporting-online-help"></a>支持联机帮助

从 Windows PowerShell 3.0 开始，有两种方法来支持`Get-Help`Windows PowerShell 命令的联机功能。 本主题说明如何实现此功能对于不同的命令类型。

## <a name="about-online-help"></a>有关联机帮助

联机帮助始终是 Windows PowerShell 的关键部分。 尽管`Get-Help`cmdlet 显示帮助主题的命令提示符处，许多用户首选的联机读取，包括颜色编码、 超链接和社区内容和 wiki 基于文档中的共享想法的体验。 最重要的是之前可更新帮助的问世，, 联机帮助提供的帮助文件的最新版本。

随着在 Windows PowerShell 3.0 中的可更新帮助，联机帮助仍扮演着重要角色。 灵活的用户体验，除了联机帮助提供了向用户对于没有或不能使用可更新的帮助来下载帮助主题的帮助。

## <a name="how-get-help--online-works"></a>如何获取帮助的联机工作原理

若要帮助用户查找联机帮助主题的命令，`Get-Help`命令有一个用户的默认 Internet 浏览器中打开一个命令的帮助主题的联机版本的 Online 参数。

例如，以下命令将打开联机帮助主题中的`Invoke-Command`cmdlet。

```powershell
Get-Help Invoke-Command -Online
```

若要实现`Get-Help`-联机， `Get-Help` cmdlet 看起来的统一资源标识符 (URI) 的以下位置中的联机版本帮助主题。

- 该命令的帮助主题的相关链接部分中的第一个链接。 必须在用户计算机上安装的帮助主题。 在 Windows PowerShell 2.0 中引入了此功能。

- 任何命令的 HelpUri 属性。 即使在用户的计算机上未安装该命令的帮助主题时，才可访问 HelpUri 属性。 在 Windows PowerShell 3.0 中引入了此功能。

  `Get-Help` 查找之前获取的 HelpUri 属性值中的相关链接部分中的第一个条目的 URI。 如果属性值不正确或已更改，您可以通过在第一个相关链接中输入一个不同的值重写它。 但是，第一个相关链接仅适用于用户的计算机上安装的帮助主题。

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>将 URI 添加到命令的帮助主题的第一个相关链接

您可以支持`Get-Help`-联机的任何命令通过将是有效的 URI 添加到命令的基于 XML 的帮助主题的相关链接部分中的第一个条目。 此选项仅在基于 XML 的帮助主题中有效，并且仅适用于用户的计算机上安装的帮助主题。 当安装的帮助主题，并且填充 URI 时，此值将优先于**HelpUri**命令的属性。 有关基于 XML 的命令的帮助主题的信息，请参阅[Writing XML-Based 命令的帮助主题](../help/writing-xml-based-help-topics-for-commands.md)。

若要支持此功能，URI 必须出现在`maml:uri`下第一个元素`maml:relatedLinks/maml:navigationLink`中的元素`maml:relatedLinks`元素。

以下 XML 显示了 URI 的正确位置。 "联机版本:"中的文本`maml:linkText`元素是最佳做法，但它不是必需。

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>将 HelpUri 属性添加到命令

本部分演示如何将 HelpUri 属性添加到不同类型的命令。

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>将 HelpUri 属性添加到 Cmdlet

编写的 cmdlet 的C#，添加**HelpUri**在 Cmdlet 类的属性。 属性的值必须是"http"或"https"开头的 URI。

下面的代码演示的 HelpUri 属性`Get-History`cmdlet 类。

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>将 HelpUri 属性添加到高级功能

对于高级函数，添加**HelpUri**属性设置为**CmdletBinding**属性。 属性的值必须是"http"或"https"开头的 URI。

下面的代码显示了新建日历函数的 HelpUri 属性

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>将 HelpUri 属性添加到 CIM 命令

有关 CIM 命令，添加**HelpUri**归于**CmdletMetadata** CDXML 文件中的元素。 属性的值必须是"http"或"https"开头的 URI。

下面的代码演示开始调试 CIM 命令的 HelpUri 属性

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>将 HelpUri 属性添加到工作流

Windows PowerShell 语言编写而成的工作流，将添加 **。ExternalHelp**到工作流代码注释指令。 指令的值必须以"http"或"https"开头的 URI。

> [!NOTE]
> 有关基于 XAML 的 Windows PowerShell 中的工作流不支持的 HelpUri 属性。

下面的代码演示。工作流文件中的 ExternalHelp 指令。

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```