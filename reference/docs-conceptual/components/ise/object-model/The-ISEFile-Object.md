---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEFile 对象
ms.openlocfilehash: 1069e46aa586b8df2050129194a909b90f77b745
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736992"
---
# <a name="the-isefile-object"></a>ISEFile 对象

**ISEFile** 对象，表示 Windows PowerShell® 集成脚本环境 (ISE) 中的文件。 它是 Microsoft.PowerShell.Host.ISE.ISEFile  类的实例。 本主题列出其成员方法和成员属性。 `$psISE.CurrentFile` 和 PowerShell 选项卡中的文件集合中的文件是 \*\***Microsoft.PowerShell.Host.ISE.ISEFile** 类的所有实例。

## <a name="methods"></a>方法

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

将该文件保存到磁盘。

**\[saveEncoding\]** - 可选 [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx)，用于已保存文件的可选字符编码参数。 默认值是 **UTF8**。

### <a name="exceptions"></a>例外

- **System.IO.IOException**：无法保存文件。

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

使用指定的文件名和编码保存文件。

**filename** - 字符串要用于保存该文件的名称。

**\[saveEncoding\]** - 可选 [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx)，用于已保存文件的可选字符编码参数。 默认值是 **UTF8**。

### <a name="exceptions"></a>例外

- **System.ArgumentNullException**：filename  参数为 Null。
- **System.ArgumentException**：filename  参数为空。
- **System.IO.IOException**：无法保存文件。

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>属性

### <a name="displayname"></a>DisplayName

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取包含此文件显示名称的字符串。 名称显示在编辑器顶部的  “文件”选项卡上。 名称结尾处存在星号 `(*)` 表示文件具有未保存的更改。

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>编辑器

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取用于指定文件的[编辑器对象](The-ISEEditor-Object.md)。

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>编码

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取原始文件编码。 这是一个 **System.Text.Encoding** 对象。

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，可获取指定已打开文件的完整路径的字符串。

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读布尔属性，如果在最后一次修改文件后保存了文件，则返回 `$true`。

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

在 Windows PowerShell ISE 2.0 和更高版本中受支持。

只读属性，如果从未指定文件标题，则返回 `$true`。

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>另请参阅

- [ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
