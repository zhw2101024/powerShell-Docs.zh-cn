---
title: PropertyName 元素 WideControl （格式） 的 WideItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860953"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName Element for WideItem for WideControl (Format)

指定其值宽视图中显示的对象的属性。

元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） WideItem 元素 （格式） 属性名称的配置元素 WideItem （格式）

## <a name="syntax"></a>语法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>属性和元素

以下各节描述的特性、 子元素和父元素的`PropertyName`元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideItem 元素 （格式）](./wideitem-element-for-widecontrol-format.md)|定义属性或其值宽视图中显示的脚本。|

## <a name="text-value"></a>文本值

指定显示其值的属性的名称。

## <a name="remarks"></a>备注

有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

## <a name="example"></a>示例

此示例显示了显示的 ProcessName 属性的值较宽的视图[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。

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

[WideItem 元素 （格式）](./wideitem-element-for-widecontrol-format.md)

[创建较宽的视图](./creating-a-wide-view.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
