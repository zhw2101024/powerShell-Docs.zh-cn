---
title: 列表视图（基本） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362806"
---
# <a name="list-view-basic"></a>列表视图 (Basic)

此示例演示如何实现显示 System.serviceprocess. Servicecontroller 的基本列表视图[？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[get-help](/powershell/module/microsoft.powershell.management/get-service) Cmdlet 返回的 Fullname 对象。 有关列表视图组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。

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

- 定义视图显示的属性的[ListControl](./listcontrol-element-format.md)元素。

- 定义在列表视图的行中显示的[内容的包含项元素。](./listitem-element-for-listitems-for-listcontrol-format.md)

- 定义要显示的属性的[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。

## <a name="example"></a>示例

下面的 XML 定义显示 System.serviceprocess. Servicecontroller 的四个属性的列表视图[。Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)对象。 在每一行中，属性的名称后跟属性的值。

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

下面的示例演示 Windows PowerShell 如何显示[system.serviceprocess. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)加载此格式化文件之后的 Fullname 对象。

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

[格式化文件的示例](./examples-of-formatting-files.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
