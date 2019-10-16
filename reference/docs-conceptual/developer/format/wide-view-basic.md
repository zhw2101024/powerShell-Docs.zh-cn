---
title: 宽视图（基本） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367936"
---
# <a name="wide-view-basic"></a>宽视图 (Basic)

此示例演示如何实现显示[system.serviceprocess. Servicecontroller 的基本视图？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由 `Get-Service` cmdlet 返回的 Fullname 对象。 有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。

### <a name="to-load-this-formatting-file"></a>加载此格式设置文件

1. 将本主题的 "示例" 部分中的 XML 复制到一个文本文件中。

2. 保存文本文件。 请确保将 @no__t 0 扩展添加到文件，以将其标识为格式文件。

3. 打开 Windows PowerShell 并运行以下命令，将格式化文件加载到当前会话中： `Update-formatdata -prependpath PathToFormattingFile`。

   > [!WARNING]
   > 此格式化文件定义已由 Windows PowerShell 格式设置文件定义的对象的显示。 当你运行 cmdlet 时，必须使用 @no__t 参数，并且无法将此格式化文件作为模块加载。

## <a name="demonstrates"></a>示例

此格式化文件演示了以下 XML 元素：

- 视图的[名称](./name-element-for-view-format.md)元素。

- 定义视图要显示的对象的[ViewSelectedBy](./viewselectedby-element-format.md)元素。

- 定义视图显示的属性的[WideItem](./wideitem-element-for-widecontrol-format.md)元素。

## <a name="example"></a>示例

下面的 XML 定义显示[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName)属性值的宽视图。

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a>另请参阅

[格式化文件的示例](./examples-of-formatting-files.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
