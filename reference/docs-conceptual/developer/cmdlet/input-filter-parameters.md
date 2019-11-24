---
title: 输入筛选器参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364386"
---
# <a name="input-filter-parameters"></a>输入筛选参数

Cmdlet 可定义 `Filter`、`Include`和 `Exclude` 参数，这些参数可筛选 cmdlet 影响的输入对象集。

通常，输入对象集由 `InputObject`、`Path`或 `Name` 参数指定。 例如，一个 cmdlet 可以有一个 `Path` 参数，该参数使用通配符接受多个路径，并且每个路径指向一个输入对象。 一起使用时，`Filter`、`Include`和 `Exclude` 参数进一步限定了 cmdlet 在每次调用时所起的作用。

## <a name="include-and-exclude-parameters"></a>包括和排除参数

`Include` 和 `Exclude` 参数标识传递到 cmdlet 的输入对象集中包含或排除的对象。 如果筛选器可以用标准通配符语言表示，请使用这些参数。 （有关通配符的详细信息，请参阅[在 Cmdlet 参数中支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。）`Include` 参数包含名称与包含筛选器匹配的所有对象。 `Exclude` 参数会排除名称与筛选器匹配的所有对象。

## <a name="filter-parameter"></a>筛选器参数

`Filter` 参数指定了不以标准通配符语言表示的筛选器。 例如，Active Directory 服务接口（ADSI）或 SQL 筛选器可以通过其 `Filter` 参数传递给 cmdlet。 在 Windows PowerShell 提供的 cmdlet 中，这些筛选器由使用 cmdlet 访问数据存储的 Windows PowerShell 提供程序指定。 每个提供程序通常定义自己的筛选器。

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>如果未指定任何输入对象集，则进行筛选

如果未指定任何输入对象集，这通常意味着要针对所有对象进行筛选。 有关详细信息，请参阅[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)