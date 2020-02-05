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
ms.openlocfilehash: cf181e8f26ebd4b9c57b5b0191809211f2471f13
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995574"
---
# <a name="supporting-online-help"></a>支持联机帮助

从 Windows PowerShell 3.0 开始，有两种方法可支持 Windows PowerShell 命令的 `Get-Help` Online 功能。 本主题说明如何针对不同的命令类型实现此功能。

## <a name="about-online-help"></a>关于联机帮助

联机帮助始终是 Windows PowerShell 的重要组成部分。 尽管 `Get-Help` cmdlet 在命令提示符处显示帮助主题，但许多用户喜欢联机阅读的体验，包括颜色编码、超链接以及在社区内容和基于 wiki 的文档中共享创意。 最重要的是，在可更新帮助出现之前，联机帮助提供了最新版本的帮助文件。

随着 Windows PowerShell 3.0 中的可更新帮助出现，联机帮助仍扮演着重要的角色。 除了灵活的用户体验外，联机帮助还向不或无法使用可更新帮助下载帮助主题的用户提供帮助。

## <a name="how-get-help--online-works"></a>Get-help-Online 工作方式

若要帮助用户查找命令的联机帮助主题，`Get-Help` 命令有一个联机参数，可在用户的默认 Internet 浏览器中打开命令的联机版本帮助主题。

例如，以下命令将打开 `Invoke-Command` cmdlet 的联机帮助主题。

```powershell
Get-Help Invoke-Command -Online
```

若要实现 `Get-Help` 联机，`Get-Help` cmdlet 会在以下位置查找联机版本帮助主题的统一资源标识符（URI）。

- 命令的帮助主题的 "相关链接" 部分中的第一个链接。 必须在用户计算机上安装 "帮助" 主题。 此功能是在 Windows PowerShell 2.0 中引入的。

- 任何命令的 HelpUri 属性。 即使在用户的计算机上未安装命令的帮助主题，也可以访问 HelpUri 属性。 此功能是在 Windows PowerShell 3.0 中引入的。

  `Get-Help` 在获取 HelpUri 属性值之前，将在 "相关链接" 部分中查找第一个条目中的 URI。 如果属性值不正确或已更改，则可以通过在第一个相关链接中输入不同的值来覆盖它。 但是，只有在用户计算机上安装了帮助主题后，第一个相关链接才有效。

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>将 URI 添加到命令帮助主题中的第一个相关链接

您可以通过将有效的 URI 添加到命令的基于 XML 的帮助主题的 "相关链接" 部分中的第一个条目来支持 `Get-Help`-Online 用于任何命令。 此选项仅在基于 XML 的帮助主题中有效，并且仅在用户计算机上安装了帮助主题时才有效。 如果安装了帮助主题并填充了 URI，则此值优先于命令的**HelpUri**属性。

若要支持此功能，URI 必须出现在 `maml:relatedLinks` 元素中第一个 `maml:relatedLinks/maml:navigationLink` 元素下的 `maml:uri` 元素中。

下面的 XML 显示 URI 的正确位置。 `maml:linkText` 元素中的 "联机版本：" 文本是最佳做法，但这不是必需的。

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>将 HelpUri 属性添加到命令

本部分介绍如何将 HelpUri 属性添加到不同类型的命令。

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>向 Cmdlet 添加 HelpUri 属性

对于用编写的C#cmdlet，请将**HelpUri**属性添加到 Cmdlet 类中。 特性的值必须是以 "http" 或 "https" 开头的 URI。

下面的代码演示 `Get-History` cmdlet 类的 HelpUri 属性。

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>将 HelpUri 属性添加到高级函数

对于高级函数，请将**HelpUri**属性添加到**CmdletBinding**属性。 属性的值必须是以 "http" 或 "https" 开头的 URI。

下面的代码演示了新的 Calendar 函数的 HelpUri 属性。

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>将 HelpUri 特性添加到 CIM 命令

对于 CIM 命令，请将**HelpUri**属性添加到 CDXML 文件中的**CmdletMetadata**元素。 特性的值必须是以 "http" 或 "https" 开头的 URI。

下面的代码显示了 "启动-调试 CIM 命令" 的 HelpUri 属性

```
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>向工作流添加 HelpUri 属性

对于使用 Windows PowerShell 语言编写的工作流，请添加 **。将 .Externalhelp**注释指令添加到工作流代码。 指令的值必须是以 "http" 或 "https" 开头的 URI。

> [!NOTE]
> Windows PowerShell 中基于 XAML 的工作流不支持 HelpUri 属性。

下面的代码演示了。工作流文件中的 .Externalhelp 指令。

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```