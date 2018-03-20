---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISESnippet 对象"
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f1b023291826d5568eb8bdf5a898a00228825276
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="the-isesnippetobject"></a>ISESnippet 对象
  **ISESnippet** 对象是 Microsoft.PowerShell.Host.ISE.ISESnippet 类的实例。 **$psISE.CurrentPowerShellTab.Snippets** 集合的成员均为 **ISESnippet** 对象的示例。 创建代码段的最简单方法是使用 [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet。

## <a name="properties"></a>“属性”

### <a name="author"></a>作者
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 只读属性，可获取代码段作者的姓名。

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a>CodeFragment
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 只读属性，可获取要插入到编辑器中的代码片段。

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a>快捷方式
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 只读属性，可获取菜单项的 Windows 键盘快捷方式。

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>另请参阅
- [ISESnippetCollection 对象](The-ISESnippetCollection-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
