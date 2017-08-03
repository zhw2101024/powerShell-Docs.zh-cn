---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISESnippetCollection 对象"
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection 对象
  **ISESnippetCollection** 对象是 **ISESnippet** 对象的集合。 与 **PowerShellTab** 对象关联的文件集合是此类的成员。 比如 **$psISE.CurrentPowerShellTab.Files** 集合。

## <a name="methods"></a>方法

### <a name="load-filepathname-"></a>Load\( FilePathName \)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 加载包含用户定义的代码段的 .snippets.ps1xml 文件。 创建代码段最简单的方法就是使用 New-IseSnippet cmdlet，后者会自动将它们存储在配置文件文件夹中，以便你每次启动 Windows PowerShell ISE 时进行加载。

 **FilePathName** - 字符串，包含代码段定义的 .snippets.ps1xml 文件的路径和文件名。

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a>另请参阅
- [ISESnippetObject](The-ISESnippetObject.md) 
- [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)

  
