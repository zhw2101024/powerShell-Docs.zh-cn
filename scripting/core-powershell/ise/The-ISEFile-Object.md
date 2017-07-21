---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEFile 对象"
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 0e1c09c4a92868448d76cc7b4954d250773ce2f2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="9509c-103">ISEFile 对象</span><span class="sxs-lookup"><span data-stu-id="9509c-103">The ISEFile Object</span></span>
  <span data-ttu-id="9509c-104">**ISEFile** 对象，表示 Windows PowerShell® 集成脚本环境 (ISE) 中的文件。</span><span class="sxs-lookup"><span data-stu-id="9509c-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="9509c-105">它是 Microsoft.PowerShell.Host.ISE.ISEFile 类的实例。</span><span class="sxs-lookup"><span data-stu-id="9509c-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="9509c-106">本主题列出其成员方法和成员属性。</span><span class="sxs-lookup"><span data-stu-id="9509c-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="9509c-107">**$PsISE.CurrentFile** 和 PowerShell 选项卡中的文件集合中的文件是 Microsoft.PowerShell.Host.ISE.ISEFile 类的所有实例。</span><span class="sxs-lookup"><span data-stu-id="9509c-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="9509c-108">方法</span><span class="sxs-lookup"><span data-stu-id="9509c-108">Methods</span></span>

###  <span data-ttu-id="9509c-109"><a name="save-override"></a> Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="9509c-109"><a name="save-override"></a> Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="9509c-110">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="9509c-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9509c-111">将该文件保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="9509c-111">Saves the file to disk.</span></span>

 <span data-ttu-id="9509c-112">**\[saveEncoding\]** - 可选 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
用于已保存文件的可选字符编码参数。</span><span class="sxs-lookup"><span data-stu-id="9509c-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="9509c-113">默认值是 **UTF8**。</span><span class="sxs-lookup"><span data-stu-id="9509c-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="9509c-114">**例外**</span><span class="sxs-lookup"><span data-stu-id="9509c-114">**Exceptions**</span></span>
 -   <span data-ttu-id="9509c-115">**System.IO.IOException**：无法保存该文件。</span><span class="sxs-lookup"><span data-stu-id="9509c-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <span data-ttu-id="9509c-116"><a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="9509c-116"><a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="9509c-117">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="9509c-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9509c-118">使用指定的文件名和编码保存文件。</span><span class="sxs-lookup"><span data-stu-id="9509c-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="9509c-119">**filename** - 字符串要用于保存该文件的名称。</span><span class="sxs-lookup"><span data-stu-id="9509c-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="9509c-120">**\[saveEncoding\]** - 可选 [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
用于已保存文件的可选字符编码参数。</span><span class="sxs-lookup"><span data-stu-id="9509c-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="9509c-121">默认值是 **UTF8**。</span><span class="sxs-lookup"><span data-stu-id="9509c-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="9509c-122">**例外**</span><span class="sxs-lookup"><span data-stu-id="9509c-122">**Exceptions**</span></span>
 -   <span data-ttu-id="9509c-123">**System.ArgumentNullException**：**filename** 参数为 null。</span><span class="sxs-lookup"><span data-stu-id="9509c-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

-   <span data-ttu-id="9509c-124">**System.ArgumentException**：**filename** 参数为空。</span><span class="sxs-lookup"><span data-stu-id="9509c-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

-   <span data-ttu-id="9509c-125">**System.IO.IOException**：无法保存该文件。</span><span class="sxs-lookup"><span data-stu-id="9509c-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="9509c-126">“属性”</span><span class="sxs-lookup"><span data-stu-id="9509c-126">Properties</span></span>

###  <span data-ttu-id="9509c-127"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="9509c-127"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="9509c-128">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="9509c-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9509c-129">只读属性，可获取包含此文件显示名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="9509c-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="9509c-130">名称显示在编辑器顶部的“文件”选项卡上。</span><span class="sxs-lookup"><span data-stu-id="9509c-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="9509c-131">名称结尾处存在星号 \(\*\)，表示文件具有未保存的更改。</span><span class="sxs-lookup"><span data-stu-id="9509c-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <span data-ttu-id="9509c-132"><a name="Editor"></a>编辑器</span><span class="sxs-lookup"><span data-stu-id="9509c-132"><a name="Editor"></a> Editor</span></span>
  <span data-ttu-id="9509c-133">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="9509c-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9509c-134">只读属性，可获取用于指定文件的[编辑器对象](The-ISEEditor-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="9509c-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <span data-ttu-id="9509c-135"><a name="Encoding"></a>编码</span><span class="sxs-lookup"><span data-stu-id="9509c-135"><a name="Encoding"></a> Encoding</span></span>
  <span data-ttu-id="9509c-136">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="9509c-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9509c-137">只读属性，可获取原始文件编码。</span><span class="sxs-lookup"><span data-stu-id="9509c-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="9509c-138">这是一个 **System.Text.Encoding** 对象。</span><span class="sxs-lookup"><span data-stu-id="9509c-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <span data-ttu-id="9509c-139"><a name="FullPath"></a> FullPath</span><span class="sxs-lookup"><span data-stu-id="9509c-139"><a name="FullPath"></a> FullPath</span></span>
  <span data-ttu-id="9509c-140">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="9509c-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9509c-141">只读属性，可获取指定已打开文件的完整路径的字符串。</span><span class="sxs-lookup"><span data-stu-id="9509c-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <span data-ttu-id="9509c-142"><a name="IsSaved"></a> IsSaved</span><span class="sxs-lookup"><span data-stu-id="9509c-142"><a name="IsSaved"></a> IsSaved</span></span>
  <span data-ttu-id="9509c-143">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="9509c-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9509c-144">只读布尔属性，如果在最后一次修改文件后保存了文件，则返回 **$true**。</span><span class="sxs-lookup"><span data-stu-id="9509c-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <span data-ttu-id="9509c-145"><a name="IsUntitled"></a> IsUntitled</span><span class="sxs-lookup"><span data-stu-id="9509c-145"><a name="IsUntitled"></a> IsUntitled</span></span>
  <span data-ttu-id="9509c-146">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="9509c-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9509c-147">只读属性，如果从未指定文件标题，则返回 **$true**。</span><span class="sxs-lookup"><span data-stu-id="9509c-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="9509c-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9509c-148">See Also</span></span>
- [<span data-ttu-id="9509c-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="9509c-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="9509c-150">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="9509c-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="9509c-151">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="9509c-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="9509c-152">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="9509c-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
