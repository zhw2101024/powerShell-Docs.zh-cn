---
title: 宽的视图 (GroupBy) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083648"
---
# <a name="wide-view-groupby"></a>宽视图 (GroupBy)

此示例演示如何实现较宽的视图，显示的组[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象`Get-Service`cmdlet。 有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

### <a name="to-load-this-formatting-file"></a>若要加载此格式设置文件

1. 将 XML 从本主题的示例部分复制到文本文件中。

2. 保存文本文件。 请务必添加`format.ps1xml`扩展其标识为格式设置文件的文件。

3. 打开 Windows PowerShell 并运行以下命令以加载到当前会话中的格式设置文件： `Update-formatdata -prependpath PathToFormattingFile`。

   > [!WARNING]
   > 此格式设置文件定义已由 Windows PowerShell 格式设置文件定义的对象的显示。 必须使用`prependPath`参数时运行 cmdlet，并且无法加载此格式设置文件作为一个模块。

## <a name="demonstrates"></a>演示

此格式设置文件演示了以下 XML 元素：

- [名称](./name-element-for-view-format.md)视图元素。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素，用于定义该视图将显示哪些对象。

- [GroupBy](./groupby-element-for-view-format.md)元素，用于定义何时显示新组。

- [WideItem](./wideitem-element-for-widecontrol-format.md)定义由视图显示哪些属性的元素。

## <a name="example"></a>示例

下面的 XML 定义较宽的视图显示对象的组。 启动每个新组时的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性更改。

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

下面的示例演示 Windows PowerShell 会显示如何[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象后加载此格式化文件。

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a>另请参阅

[格式设置文件的示例](./examples-of-formatting-files.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
