---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 筛选搜索结果
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003687"
---
# <a name="filtering-search-results"></a>筛选搜索结果

[“包”选项卡](https://www.powershellgallery.com/packages)显示 PowerShell 库中所有可用的包。

可通过多种方法筛选、排序和搜索这些包。
若要查看某个特定包的详细信息，请单击该包。

## <a name="filter-by"></a>筛选依据

使用“筛选依据”下拉列表，用户可以按下列依据筛选结果：
- 包括预发行版
- 仅稳定版

若要了解“预发行版”和“稳定版”，请参阅 PowerShell 团队博客中的[在 PowerShellGet 和 PowerShell 库中添加的预发行版版本控制](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/)。

使用下拉列表下的复选框，用户可以按下列依据筛选结果：
- 包类型
  - 模块
  - 脚本
- 类别
  - Cmdlet
  - DSC 资源
  - 功能
  - 角色功能
  - 工作流

若要仅查看 PowerShell 库中的模块，请选中“包类型”中的“模块”。
同样，若要仅查看 PowerShell 库中的脚本，请选中“包类型”中的“脚本”。

> [!NOTE]
> 筛选器为包含式。
> 例如，如果选中“Cmdlet”和/或“函数”，将显示包含 cmdlet 和函数的包。
> 如果未选中任何一个，则不会显示包。
> 同样，如果选择了所有类别，将仅显示包含这些类别之一的包。
> 不会显示不属于任何这些类别的包。

## <a name="sort-by"></a>排序依据

使用“排序依据”下拉列表，用户可以按下列依据排序结果：
- 热门程度 - 热门程度取决于下载次数
- A-Z - 按包名称的字母顺序排序
- 最新 - 按发布日期顺序显示各包

## <a name="search-box"></a>搜索框

使用搜索框，用户可以通过关键字来搜索包。
有关详细信息，请参阅[库搜索语法](search-syntax.md)。
