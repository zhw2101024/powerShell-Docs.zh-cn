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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854983"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="443a4-102">设置显示数据的格式</span><span class="sxs-lookup"><span data-stu-id="443a4-102">Formatting Displayed Data</span></span>

<span data-ttu-id="443a4-103">您可以指定列表、 表或宽的视图中的单个数据点的显示方式。</span><span class="sxs-lookup"><span data-stu-id="443a4-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="443a4-104">可以使用`FormatString`元素定义的视图，或你的项目时可以使用`ScriptBlock`元素来调用`FormatString`对数据的方法。</span><span class="sxs-lookup"><span data-stu-id="443a4-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="443a4-105">使用 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="443a4-105">Using the FormatString Element</span></span>

<span data-ttu-id="443a4-106">在下面的示例值的`TotalProcessorTime`的属性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象的格式使用 FormatString 元素。</span><span class="sxs-lookup"><span data-stu-id="443a4-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="443a4-107">`TotalProcessorTime`属性</span><span class="sxs-lookup"><span data-stu-id="443a4-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



