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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854463"
---
# <a name="input-filter-parameters"></a>输入筛选参数

Cmdlet 可以定义`Filter`， `Include`，和`Exclude`筛选会影响该 cmdlet 的输入对象的集合的参数。

通常，由指定输入对象的集合`InputObject`， `Path`，或`Name`参数。 例如，一个 cmdlet 可以具有`Path`接受多个路径使用通配符字符和每个路径指向输入对象的参数。 一起使用， `Filter`， `Include`，和`Exclude`参数进一步限定 cmdlet 在每次调用它的工作方式的路径。

## <a name="include-and-exclude-parameters"></a>Include 和 Exclude 参数

`Include`和`Exclude`参数标识要包含或排除从传递给该 cmdlet 的输入对象的集合的对象。 可以在标准通配符语言中表示筛选器时，请使用这些参数。 (有关通配符的详细信息，请参阅[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。)`Include`参数包括其名称与包含筛选器匹配的所有对象。 `Exclude`参数不包括其名称的筛选器匹配的所有对象。

## <a name="filter-parameter"></a>筛选器参数

`Filter`参数指定的标准通配符语言中未表示的筛选器。 例如，Active Directory 服务接口 (ADSI) 或 SQL 筛选器可能会传递给该 cmdlet 通过其`Filter`参数。 在 Windows PowerShell 提供 cmdlet，这些筛选器指定通过使用 cmdlet 来访问数据存储区的 Windows PowerShell 提供程序。 通常，每个提供程序定义自己的筛选器。

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>如果不指定了输入对象的任何组筛选

如果指定的输入对象未设置，则这通常意味着要针对的所有对象进行筛选。 有关详细信息，请参阅[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)