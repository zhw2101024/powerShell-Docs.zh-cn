---
title: WideControl 的 WideItem 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364936"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName Element for WideItem for WideControl (Format)

指定对象的属性，其值显示在宽视图中。

用于 WideItem 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式） WideItem 元素（格式） PropertyName 元素

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节介绍 `PropertyName` 元素的属性、子元素和父元素。

### <a name="attributes"></a>属性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideItem 元素（格式）](./wideitem-element-for-widecontrol-format.md)|定义其值在宽视图中显示的属性或脚本。|

## <a name="text-value"></a>文本值

指定显示其值的属性的名称。

## <a name="remarks"></a>备注

有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

## <a name="example"></a>示例

此示例显示了一个宽视图，其中[显示了 ProcessName 对象的](/dotnet/api/System.Diagnostics.Process)"" 属性的值。

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>另请参阅

[WideItem 元素（格式）](./wideitem-element-for-widecontrol-format.md)

[创建宽视图](./creating-a-wide-view.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
