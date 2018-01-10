---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_items_tab
ms.openlocfilehash: 8704091542de5c19817ab0b4f77fd98987084b5d
ms.sourcegitcommit: 1a0a0928c1e3cae4e8df8d79b0737bd7ed6b4e47
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="items-tab"></a>“项”选项卡

[“项”选项卡](https://www.powershellgallery.com/items)显示 PowerShell 库中的所有项。

可通过多种方法筛选、排序和搜索这些项。
若要查看某个特定项的详细信息，请单击该项。

## <a name="filter-by"></a>筛选依据

使用“筛选依据”下拉列表，用户可以按下列依据筛选结果：
* 包括预发行版
* 仅稳定版

若要了解“预发行版”和“稳定版”，请参阅 PowerShell 团队博客中的[在 PowerShellGet 和 PowerShell 库中添加的预发行版版本控制](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/)。

使用下拉列表下的复选框，用户可以按下列依据筛选结果：
* 项目类型
  - 模块
  - 脚本
* 类别
  - Cmdlet
  - DSC 资源
  - 功能
  - 角色功能
  - 工作流

若要仅查看 PowerShell 库中的模块，请选中“项类型”中的“模块”。
同样，若要仅查看 PowerShell 库中的脚本，请选中“项类型”中的“脚本”。

> [!NOTE]
> 筛选器为包含式。
> 例如，如果选中“Cmdlet”和/或“函数”，将显示包含 cmdlet 和函数的项。
> 如果未选中任何一个，则不会显示项。
> 同样，如果选择了所有类别，将仅显示包含这些类别之一的项。
> **不会显示不属于任何这些类别的项。**

## <a name="sort-by"></a>排序依据

使用“排序依据”下拉列表，用户可以按下列依据排序结果：
* 热门程度 - 热门程度取决于下载次数
* A-Z - 按项名称的字母顺序排序
* 最新 - 按发布日期顺序显示各项

## <a name="search-box"></a>搜索框

搜索框允许用户通过关键字来搜索项。
有关详细信息，请参阅[库搜索语法](psgallery_search_syntax.md)。
