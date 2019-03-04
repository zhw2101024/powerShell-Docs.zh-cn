---
title: 创建列表视图 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861573"
---
# <a name="creating-a-list-view"></a>创建列表视图

列表视图 （按先后顺序） 的单个列中显示数据。 在列表中显示的数据可以是.NET 属性的值或脚本的值。

## <a name="a-list-view-display"></a>列表视图显示

以下输出显示了 Windows PowerShell 如何显示的属性[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。 在此示例中，返回了三个对象，其中从上述对象由一个空行分隔每个对象。

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>定义列表视图

下面的 XML 演示用于显示的多个属性的列表视图架构[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象。 必须指定想要在列表视图中显示每个属性。

```xml
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
```

以下 XML 元素用于定义列表视图：

- [视图](./view-element-format.md)元素是列表视图的父元素。 （这是对于表，，和自定义控件的视图相同的父元素）。

- [名称](./name-element-for-view-format.md)元素指定的视图的名称。 此元素是必需的所有视图。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。 此元素是必需的。

- [GroupBy](./groupby-element-for-view-format.md)元素定义何时显示新组的对象。 特定属性或脚本的值发生更改时启动新的组。 此元素是可选的。

- [控件](./controls-element-for-view-format.md)元素定义由列表视图中定义的自定义控件。 控件提供了一种方法，以便进一步指定如何显示数据。 此元素是可选的。 视图可以定义自己的自定义控件或它可以使用可由任意视图中的格式设置文件的公共控件。 有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

- [ListControl](./listcontrol-element-format.md)元素定义的视图中显示的内容和它的格式。 与所有其他视图类似，列表视图可以显示对象属性的值或值生成的脚本。

有关定义简单列表视图的完整格式设置文件的示例，请参阅[列表视图 （基本）](./list-view-basic.md)。

## <a name="providing-definitions-for-your-list-view"></a>提供在列表视图的定义

列表视图可以通过使用的子元素提供一个或多个定义[ListControl](./listcontrol-element-format.md)元素。 通常情况下，视图将具有只有一个定义。 在以下示例中，视图提供了显示的多个属性的单个定义[System.Diagnostics.Process？Displayproperty =](/dotnet/api/System.Diagnostics.Process)对象。 列表视图可以显示属性的值或脚本 （在示例中未显示） 的值。

```xml
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

```

以下 XML 元素可以用于提供列表视图的定义：

- [ListControl](./listcontrol-element-format.md)元素及其子元素定义的视图中显示的内容。

- [ListEntries](./listentries-element-for-listcontrol-format.md)元素提供了该视图的定义。 在大多数情况下，将具有只有一个定义的视图。 此元素是必需的。

- [ListEntry](./listentry-element-for-listcontrol-format.md)元素提供视图的定义。 至少一个[ListEntry](./listentry-element-for-listcontrol-format.md)是必需的; 但是，没有任何可以添加的元素数目的最大限制。 在大多数情况下，将具有只有一个定义的视图。

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素指定所显示的特定定义的对象。 此元素是可选的仅当定义多个需要[ListEntry](./listentry-element-for-listcontrol-format.md)元素，用于显示不同的对象。

- [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)元素指定的属性和其值显示在列表视图的行中的脚本。

- [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md)元素指定的属性或其值显示在列表视图的行中的脚本。 列表视图必须指定至少一个属性或脚本。 可以指定的行数没有最大限制。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素指定的行中显示其值的属性。 必须指定一个属性或脚本，但不能同时指定。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素指定其值显示的行中的脚本。 必须指定一个脚本或属性，但不能同时指定。

- [标签](./label-element-for-listitem-for-listcontrol-format.md)元素指定的行中的属性或脚本的值的左侧显示的标签。 此元素是可选的。 如果未指定一个标签，显示属性或脚本的名称。 有关完整示例，请参阅[列表视图 （标签）](./list-view-labels.md)。

- [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)元素指定要显示的行中必须存在的条件。 有关将条件添加到列表视图的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。 此元素是可选的。

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md)元素指定用于显示属性或脚本的值的模式。 此元素是可选的。

有关定义简单列表视图的完整格式设置文件的示例，请参阅[列表视图 （基本）](./list-view-basic.md)。

## <a name="defining-the-objects-that-use-the-list-view"></a>定义使用列表视图的对象

有两种方法定义的.NET 对象使用列表视图。 可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可显示的视图，或者您的所有定义的对象可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素来定义将显示哪些对象将视图的特定定义。 在大多数情况下，视图具有只有一个定义，因此对象通常由定义[ViewSelectedBy](./viewselectedby-element-format.md)元素。

下面的示例演示如何定义显示列表视图使用的对象[ViewSelectedBy](./viewselectedby-element-format.md)并[TypeName](./typename-element-for-viewselectedby-format.md)元素。 数量没有限制[TypeName](./typename-element-for-viewselectedby-format.md)元素可以指定和其顺序并不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

以下 XML 元素可以用于指定使用列表视图的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图将显示哪些对象。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素指定.NET 对象，该视图显示对象。 完全限定的.NET 类型名称是必需的。 必须指定至少一个类型或所选内容设置对于视图，但可以指定的元素没有最大数目。

有关完整的格式设置文件的示例，请参阅[列表视图 （基本）](./list-view-basic.md)。

下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)并[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。 使用的选项集，其中有一组相关的相同对象使用多个视图，例如何时定义列表视图和表视图，显示的对象。 有关如何创建选项集的详细信息，请参阅[定义的选项集，](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

以下 XML 元素可以用于指定使用列表视图的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图将显示哪些对象。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定一组视图可以显示的对象。 必须指定至少一个选择集或类型视图，但可以指定的元素没有最大数目。

下面的示例演示如何定义使用列表视图的特定定义所显示的对象[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素。 使用此元素，可以指定将对象、 选择一组对象或选择条件，指定当使用定义的.NET 类型名称。 有关如何创建所选条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

以下 XML 元素可以用于指定使用特定的列表视图中定义的对象：

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素定义在定义将显示哪些对象。

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素指定显示定义的.NET 对象。 使用此元素，完全限定的.NET 类型名称时，所需。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素 （未显示） 指定一组可显示的此定义的对象。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素 （未显示） 指定要使用此定义中必须存在的条件。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。 有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-list-view"></a>在列表视图中显示的对象的组

可以分隔成组的列表视图显示的对象。 这并不意味着定义组，仅特定属性或脚本的值发生更改时，Windows PowerShell 启动新的组。 在以下示例中，启动新的组时的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性更改。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

以下 XML 元素用于定义一组启动时：

- [GroupBy](./groupby-element-for-view-format.md)元素定义的属性或启动新的组，并定义如何显示组的脚本。

- [PropertyName](./propertyname-element-for-groupby-format.md)元素指定它的值发生更改时启动新的组的属性。 必须指定属性或脚本以启动组，但不能同时指定。

- [ScriptBlock](./scriptblock-element-for-groupby-format.md)元素指定它的值发生更改时启动新的组的脚本。 必须指定脚本或属性来启动组，但不能同时指定。

- [标签](./label-element-for-groupby-format.md)元素定义每个组的起始处显示标签。 除了指定此元素的文本，Windows PowerShell 显示触发的新组并添加一个空行之前和之后标签的值。 此元素是可选的。

- [CustomControl](./customcontrol-element-for-groupby-format.md)元素定义用于显示数据的控件。 此元素是可选的。

- [CustomControlName](./customcontrolname-element-for-groupby-format.md)元素指定一种常见或视图用于显示数据的控件。 此元素是可选的。

有关定义组的完整格式设置文件的示例，请参阅[列表视图 (GroupBy)](./list-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字符串

可以为视图，以进一步定义数据的显示方式添加格式设置字符串。 下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

可以使用以下 XML 元素来指定格式模式：

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素指定由该视图显示的数据。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素指定由该视图显示其值的属性。 必须指定一个属性或脚本，但不能同时指定。

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md)元素指定的格式模式，它定义如何在视图中显示的属性或脚本的值。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素 （未显示） 指定其值显示通过视图的脚本。 必须指定一个脚本或属性，但不能同时指定。

在以下示例中，`ToString`调用方法来设置脚本的值的格式。 脚本可以调用一个对象的任何方法。 因此，如果对象具有一种方法，如`ToString`，具有格式设置参数，该脚本可以调用该方法，以设置脚本的输出值的格式。

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

下面的 XML 元素可用于调用`ToString`方法：

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素指定由该视图显示的数据。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素 （未显示） 指定其值显示通过视图的脚本。 必须指定一个脚本或属性，但不能同时指定。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
