---
title: 列表视图 (Basic) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 1c683693c331ccfaf7355a0dd51801ed6fd39b3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853303"
---
# <a name="list-view-basic"></a>列表视图 (Basic)

此示例演示如何实现一个基本的列表视图，显示[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。 列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。
此示例演示如何实现一个基本的列表视图，显示[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。 列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

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

- [ListControl](./listcontrol-element-format.md)定义由视图显示哪些属性的元素。

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素，用于定义列表视图中的某一行中显示的内容。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定义显示的属性的元素。

## <a name="example"></a>示例

下面的 XML 定义显示的四个属性的列表视图[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象。 在每个行，跟属性的值显示的属性的名称。

```xml
<Configuration>
  <View>
    <Name>System.ServiceProcess.ServiceController</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
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
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

下面的示例演示 Windows PowerShell 会显示如何[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象后加载此格式化文件。

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>另请参阅

[格式设置文件的示例](./examples-of-formatting-files.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
