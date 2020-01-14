---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippet 对象
ms.openlocfilehash: 60456ec90f56753fa96f141b8b8299ef3f7e41c9
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736958"
---
# <a name="the-isesnippetobject"></a>ISESnippet 对象

**ISESnippet** 对象是 Microsoft.PowerShell.Host.ISE.ISESnippet 类的实例。 `$psISE.CurrentPowerShellTab.Snippets` 集合的成员均为 ISESnippet 对象的示例。  创建代码段的最简单方法是使用 [New-IseSnippet](/reference/5.1/ISE/New-IseSnippet.md) cmdlet。

## <a name="properties"></a>属性

### <a name="author"></a>作者

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

只读属性，可获取代码段作者的姓名。

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

只读属性，可获取要插入到编辑器中的代码片段。

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>快捷方式

在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

只读属性，可获取菜单项的 Windows 键盘快捷方式。

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>另请参阅

- [ISESnippetCollection 对象](The-ISESnippetCollection-Object.md)
- [Windows PowerShell ISE 脚本对象模型的用途](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)
