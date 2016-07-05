---
title: "ISEFile 对象"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: ce9364e8fb73a2d31b728430c590fef4175ebe26

---

# ISEFile 对象
  **ISEFile** 对象代表 Windows PowerShellÂ® 集成脚本环境 (ISE) 中的文件。 它是 Microsoft.PowerShell.Host.ISE.ISEFile 类的实例。 本主题列出其成员方法和成员属性。 **$PsISE.CurrentFile** 和 PowerShell 选项卡中的文件集合中的文件是 Microsoft.PowerShell.Host.ISE.ISEFile 类的所有实例。

## 方法

###  <a name="save-override"></a> Save\( \[saveEncoding\] \)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 将该文件保存到磁盘。

 **\[saveEncoding\]** – 可选 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 一个要用于已保存文件的可选字符编码参数。 默认值是 **UTF8**。

 **例外**
 -   **System.IO.IOException**：无法保存该文件。

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 使用指定的文件名和编码保存文件。

 **filename**\-字符串要用于保存该文件的名称。

 **\[saveEncoding\]** – 可选 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 一个要用于已保存文件的可选字符编码参数。 默认值是 **UTF8**。

 **例外**
 -   **System.ArgumentNullException**：**filename** 参数为 null。

-   **System.ArgumentException**：**filename** 参数为空。

-   **System.IO.IOException**：无法保存该文件。

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## “属性”

###  <a name="Displayname"></a> DisplayName
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取包含此文件显示名称的字符串。 名称显示在编辑器顶部的****“文件”选项卡上。 名称结尾处存在星号 \(\*\) 表示文件具有未保存的更改。

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <a name="Editor"></a> 编辑器
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取用于指定文件的[编辑器对象](The-ISEEditor-Object.md)。

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <a name="Encoding"></a> 编码
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取原始文件编码。 这是一个 **System.Text.Encoding** 对象。

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <a name="FullPath"></a> FullPath
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，可获取指定已打开文件的完整路径的字符串。

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <a name="IsSaved"></a> IsSaved
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读布尔属性，如果在最后一次修改文件后保存了文件，则返回 **$true**。

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <a name="IsUntitled"></a> IsUntitled
  在 Windows PowerShell ISE 2.0 和更高版本中受支持。 

 只读属性，如果从未指定文件标题，则返回 **$true**。

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## 另请参阅
 [ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
 [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Jun16_HO4-->


