---
title: "ISESnippetCollection 对象"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
translationtype: Human Translation
ms.sourcegitcommit: 3222a0ba54e87b214c5ebf64e587f920d531956a
ms.openlocfilehash: d7debb2ca5560839f7fdb986d26255dba930d8f5

---

# ISESnippetCollection 对象
  **ISESnippetCollection** 对象是 **ISESnippet** 对象的集合。 与 **PowerShellTab** 对象关联的文件集合是此类的成员。 比如 **$psISE.CurrentPowerShellTab.Files** 集合。

## 方法

### Load\( FilePathName \)
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 加载包含用户定义的代码段的 .snippets.ps1xml 文件。 创建代码段最简单的方法就是使用 New-IseSnippet cmdlet，后者会自动将它们存储在配置文件文件夹中，以便你每次启动 Windows PowerShell ISE 时进行加载。

 **FilePathName** – 包含代码段定义的 .snippets.ps1xml 文件的路径和文件名。

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## 另请参阅
 [ISESnippetObject](The-ISESnippetObject.md) 
 [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Aug16_HO4-->


