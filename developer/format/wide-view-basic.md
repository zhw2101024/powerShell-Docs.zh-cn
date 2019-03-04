---
title: 宽的视图 (Basic) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860103"
---
# <a name="wide-view-basic"></a>宽视图 (Basic)

此示例演示如何实现一个基本的宽视图，显示[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象`Get-Service`cmdlet。 有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。

### <a name="to-load-this-formatting-file"></a>若要加载此格式设置文件

1. 将 XML 从本主题的示例部分复制到文本文件中。

2. 保存文本文件。 请务必添加`format.ps1xml`扩展其标识为格式设置文件的文件。

3. 打开 Windows PowerShell 并运行以下命令以加载到当前会话中的格式设置文件： `Update-formatdata -prependpath PathToFormattingFile`。

   > [!WARNING]
   > 此格式设置文件定义显示由 Windows PowerShell 格式设置文件已定义的对象。 必须使用`prependPath`参数时运行 cmdlet，并且无法加载此格式设置文件作为一个模块。

## <a name="demonstrates"></a>说明

此格式设置文件演示了以下 XML 元素：

- [名称](./name-element-for-view-format.md)视图元素。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素，用于定义该视图将显示哪些对象。

- [WideItem](./wideitem-element-for-widecontrol-format.md)定义由视图显示哪些属性的元素。

## <a name="example"></a>示例

下面的 XML 定义中显示的值较宽的视图[System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName)属性。

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

下面的示例演示 Windows PowerShell 会显示如何[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象后加载此格式化文件。

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

[格式设置文件的示例](./examples-of-formatting-files.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
