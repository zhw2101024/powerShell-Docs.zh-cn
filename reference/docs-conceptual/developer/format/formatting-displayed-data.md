---
title: 设置显示的数据的格式 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363696"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="ce2f5-102">设置显示数据的格式</span><span class="sxs-lookup"><span data-stu-id="ce2f5-102">Formatting Displayed Data</span></span>

<span data-ttu-id="ce2f5-103">您可以指定如何显示列表、表或宽视图中的各个数据点。</span><span class="sxs-lookup"><span data-stu-id="ce2f5-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="ce2f5-104">在定义视图的项时，可以使用 `FormatString` 元素，也可以使用 `ScriptBlock` 元素对数据调用 `FormatString` 方法。</span><span class="sxs-lookup"><span data-stu-id="ce2f5-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="ce2f5-105">使用格式字符串元素</span><span class="sxs-lookup"><span data-stu-id="ce2f5-105">Using the FormatString Element</span></span>

<span data-ttu-id="ce2f5-106">在下面的示例中，使用 "格式字符串" 元素[设置 "`TotalProcessorTime`" 对象的](/dotnet/api/System.Diagnostics.Process)"" 属性的值。</span><span class="sxs-lookup"><span data-stu-id="ce2f5-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="ce2f5-107">`TotalProcessorTime` 属性</span><span class="sxs-lookup"><span data-stu-id="ce2f5-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



