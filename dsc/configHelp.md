---
title: "编写 DSC 配置的帮助"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: f4dc0265246195cc2320bcaf9d7f9abf7b1405a3
ms.openlocfilehash: becacd2dcbc6fd0edd9154a45342edc5c536935b

---

# 编写 DSC 配置的帮助

>适用于：Windows PowerShell 5.0

可在 DSC 配置中使用基于注释的帮助。 若要访问帮助内容，用户可以使用 `-?` 调用配置函数或使用 [Get-Help](https://technet.microsoft.com/en-us/library/hh849696.aspx) cmdlet。 若要详细了解基于 PowerShell 注释的帮助内容，请参阅 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/hh847834.aspx)。

下面的示例演示了一个脚本，它包含一个配置及其各自基于注释的帮助：

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword. 
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description. 
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters 
(and their descriptions) appear in help topic. To change the order, change the syntax.

.PARAMETER FilePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$ComputerName,[string]$FilePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## 查看配置帮助

若要查看有关配置的帮助，请使用带有函数名称的 **Get-help** cmdlet，或键入后跟 `-?` 的函数名称。 下面展示了在传递给 **Get-Help** 时上一个函数的输出：

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1
    
SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.
    
    
SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] 
    <String>] [[-FilePath] <String>] [<CommonParameters>]
    
    
DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.
    

RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## 另请参阅
* [DSC 配置](configurations.md)




<!--HONumber=Jun16_HO4-->


