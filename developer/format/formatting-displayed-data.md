---
title: 显示格式的数据 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065659"
---
# <a name="formatting-displayed-data"></a>设置显示数据的格式

您可以指定列表、 表或宽的视图中的单个数据点的显示方式。 可以使用`FormatString`元素定义的视图，或你的项目时可以使用`ScriptBlock`元素来调用`FormatString`对数据的方法。

## <a name="using-the-formatstring-element"></a>使用 FormatString 元素

在下面的示例值的`TotalProcessorTime`的属性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象的格式使用 FormatString 元素。 `TotalProcessorTime`属性

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



