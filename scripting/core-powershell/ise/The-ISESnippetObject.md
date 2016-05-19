---
title: ISESnippet 对象
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
---
# ISESnippet 对象
  **ISESnippet** 对象是 Microsoft.PowerShell.Host.ISE.ISESnippet 类的实例。 **$psISE.CurrentPowerShellTab.Snippets** 集合的成员均为 **ISESnippet** 对象的示例。 创建代码段的最简单方法是使用 [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet。

## “属性”

###  <a name="DisplayName"></a> 作者
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 只读属性，可获取代码段作者的姓名。

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

###  <a name="Action"></a> CodeFragment
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 只读属性，可获取要插入到编辑器中的代码片段。

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

###  <a name="Shortcut"></a> 快捷方式
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。 

 只读属性，可获取菜单项的 Windows 键盘快捷方式。

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## 另请参阅
 [ISESnippetCollection 对象](The-ISESnippetCollection-Object.md) 
 [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


