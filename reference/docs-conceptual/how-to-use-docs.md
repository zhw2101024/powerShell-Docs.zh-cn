---
ms.date: 09/25/2019
keywords: powershell,cmdlet
title: 如何使用 PowerShell 文档
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281652"
---
# <a name="how-to-use-the-powershell-documentation"></a>如何使用 PowerShell 文档

欢迎使用 PowerShell 联机文档。 此站点包含以下 PowerShell 版本的 cmdlet 参考：

- PowerShell 7（预览版）
- PowerShell 6
- PowerShell 5.1
- PowerShell 5.0
- PowerShell 4.0
- PowerShell 3.0

## <a name="selecting-your-version"></a>选择你的版本

默认情况下，此站点显示最新版本的 PowerShell 的文档。 一些 cmdlet 在不同版本的 PowerShell 中的工作方式有所不同。 确保查看所使用的 PowerShell 版本的文档。

使用页面顶部的版本选取器来选择所需的 PowerShell 版本。

![版本选取器](images/how-to-use-docs/picker-vall.gif)

可以通过查看 `$PSversionTable.PSVersion` 值来验证所使用的 PowerShell 版本。 下面的示例演示 Windows PowerShell v5.1 的输出。

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a>搜索文章

有两种方法可以搜索 Docs 中的内容。最简单的方法是使用版本选取器下的筛选器框。 只需输入文章标题中出现的字词即可。 该页面显示匹配文章的列表。 还可以从该列表中选择用于搜索整个站点的选项。

![筛选器框](images/how-to-use-docs/filter-search.gif)
