---
title: 列表视图 (GroupBy) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860143"
---
# <a name="list-view-groupby"></a>列表视图 (GroupBy)

此示例演示如何实现将列表的行分隔成组的列表视图。 此列表视图显示的属性[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。 列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。
此示例演示如何实现将列表的行分隔成组的列表视图。 此列表视图显示的属性[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet。 列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

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

- [GroupBy](./viewselectedby-element-format.md)元素，用于定义一组新对象的显示方式。

- [ListControl](./listcontrol-element-format.md)定义由视图显示哪些属性的元素。

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素，用于定义列表视图中的某一行中显示的内容。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定义显示的属性的元素。

## <a name="example"></a>示例

下面的 XML 定义启动一个新的列表视图分组时的值[System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status)属性更改。 当启动每个组时，自定义标签将显示一个包含属性的新值。

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

下面的示例演示 Windows PowerShell 会显示如何[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象后加载此格式化文件。 通过 Windows PowerShell 会自动添加空白行添加之前和之后组标签。

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>另请参阅

[格式设置文件的示例](./examples-of-formatting-files.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
