---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 库搜索语法
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742850"
---
# <a name="gallery-search-syntax"></a>库搜索语法

您可以搜索 PowerShell 库使用[PowerShell 库的 web 站点](https://www.powershellgallery.com/)。
PowerShell 库网站上提供文本搜索框，其中使用单词、 短语和关键字表达式来缩小搜索结果。

## <a name="search-by-keywords"></a>按关键字搜索

    dsc azure sql

搜索尝试查找包含所有 3 个关键字的相关文档，并返回匹配的文档。

## <a name="search-using-phrases-and-keywords"></a>使用短语和关键字进行搜索

    "azure sql" deployment

在引号（“”）之间输入短语将搜索更改为查找特定的短语而不是单独的关键字。
匹配的文档通常应包含确切的短语“azure sql”，包括大写的变体。“Azure SQL”，并通常还包含“deployment”一词。

## <a name="filtering-on-fields"></a>按字段进行筛选

通过将字段名称作为搜索词前缀，可以搜索特定包 ID（或“Id”或“id”），或一些其他字段。

目前可搜索的字段有“Id”、“Version”、“Tags”、“Author”、“Owner”、“Functions”、“Cmdlet”、“DscResources”和“PowerShellVersion”。

[ID 和标题之间的区别是什么？ ID 是在控制台中使用的名称。 标题是在搜索结果中的包页顶部所显示的内容。]

## <a name="examples"></a>示例

    ID:PSReadline
    
查找包含"PSReadline"id 的程序包。

    Id:"AzureRM.Profile"

是另一种在其 ID 字段中查找具有“AzureRM.Profile”的包的方法。

“Id”筛选器是一个子字符串匹配，因此，如果搜索以下内容：

    Id:"azure"

这提供了结果，包括 AzureRM.Profile 和 Azure.Storage。

你也可以搜索单个字段中的多个关键字。 

    id:azure tags:intellisense

还可以执行短语搜索使用双引号引起来：

    id:"azure.storage"

搜索具有 DSC 标记的所有包。

    Tags:DSC

搜索具有指定函数的所有包。

    Functions:Get-TreeSize

搜索具有指定 cmdlet 的所有包。

    Cmdlets:Get-AzureRmEnvironment

搜索具有指定 DSC 资源名称的所有包。

    DscResources:xArchive

搜索具有指定 PowerShellVersion 的所有包

    PowerShellVersion:2.0

最后，如果你使用不支持的字段（如“commands”），我们将忽略该字段并搜索所有字段。 因此以下查询

    commands:blobs storage

的解释与此查询完全相同：

    blobs storage
