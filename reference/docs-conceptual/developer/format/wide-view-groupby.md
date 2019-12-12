---
title: 宽视图（GroupBy） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367946"
---
# <a name="wide-view-groupby"></a>宽视图 (GroupBy)

此示例演示如何实现显示 System.serviceprocess. Servicecontroller 的组的宽视图[？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) `Get-Service` cmdlet 返回的 Fullname 对象。 有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

### <a name="to-load-this-formatting-file"></a>加载此格式设置文件

1. 将本主题的 "示例" 部分中的 XML 复制到一个文本文件中。

2. 保存文本文件。 请确保将 `format.ps1xml` 扩展添加到文件中，以将其标识为格式文件。

3. 打开 Windows PowerShell 并运行以下命令，将格式化文件加载到当前会话中： `Update-formatdata -prependpath PathToFormattingFile`。

   > [!WARNING]
   > 此格式化文件定义已由 Windows PowerShell 格式设置文件定义的对象的显示。 在运行 cmdlet 时，必须使用 `prependPath` 参数，并且不能将此格式化文件作为模块加载。

## <a name="demonstrates"></a>说明

此格式化文件演示了以下 XML 元素：

- 视图的[名称](./name-element-for-view-format.md)元素。

- 定义视图要显示的对象的[ViewSelectedBy](./viewselectedby-element-format.md)元素。

- 定义新组的显示时间的[GroupBy](./groupby-element-for-view-format.md)元素。

- 定义视图显示的属性的[WideItem](./wideitem-element-for-widecontrol-format.md)元素。

## <a name="example"></a>示例

下面的 XML 定义显示对象组的宽视图。 当[system.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性的值发生更改时，将启动每个新组。

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

下面的示例演示 Windows PowerShell 如何显示[system.serviceprocess. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)加载此格式化文件之后的 Fullname 对象。

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

[格式化文件的示例](./examples-of-formatting-files.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
