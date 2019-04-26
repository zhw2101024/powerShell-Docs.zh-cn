---
title: 创建较宽的视图 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066713"
---
# <a name="creating-a-wide-view"></a>创建宽视图

较宽的视图显示每个对象显示单个值。 显示的值可以是.NET 对象属性的值或脚本的值。 默认情况下，没有标签或此视图的标头。

## <a name="a-wide-view-display"></a>宽的视图显示

下面的示例演示如何显示 Windows PowerShell [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)返回的对象[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 时其输出通过管道传递给[Format-wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet。 (默认情况下[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 返回的表视图。)在此示例中，两个列用于显示有关每个返回的对象的进程名称。 不显示对象的属性的名称，仅属性的值。

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>定义宽视图

下面的 XML 演示的宽视图架构[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
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

以下 XML 元素用于定义较宽的视图：

- [视图](./view-element-format.md)元素是宽视图的父元素。 （这是表、 列表和自定义控件视图的相同父元素）。

- [名称](./name-element-for-view-format.md)元素指定的视图的名称。 此元素是必需的所有视图。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。 此元素是必需的。

- [GroupBy](./groupby-element-for-view-format.md)元素定义何时显示新组的对象。 特定属性或脚本的值发生更改时启动新的组。 此元素是可选的。

- [控件](./controls-element-for-view-format.md)元素定义宽视图定义的自定义控件。 控件提供了一种方法，以便进一步指定如何显示数据。 此元素是可选的。 视图可以定义自己的自定义控件或它可以使用可由任意视图中的格式设置文件的公共控件。 有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

- [WideControl](./widecontrol-element-format.md)元素及其子元素定义的视图中显示的内容。 在前面的示例中，视图设计用于显示[System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)属性。

有关完整的格式设置文件，用于定义较宽的简单视图的示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。

## <a name="providing-definitions-for-your-wide-view"></a>提供宽视图的定义

宽视图可以通过使用的子元素提供一个或多个定义[WideControl](./widecontrol-element-format.md)元素。 通常情况下，视图将具有只有一个定义。 在以下示例中，此视图提供单个的定义显示的值[System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)属性。 较宽的视图可以显示属性的值或脚本 （在示例中未显示） 的值。

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

以下 XML 元素可以用于提供较宽的视图的定义：

- [WideControl](./widecontrol-element-format.md)元素及其子元素定义的视图中显示的内容。

- [AutoSize](./autosize-element-for-widecontrol-format.md)元素指定列的大小和列数会调整基于数据的大小。 此元素是可选的。

- [ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素指定宽视图中显示的列数。 此元素是可选的。

- [WideEntries](./wideentries-element-for-widecontrol-format.md)元素提供了该视图的定义。 在大多数情况下，将具有只有一个定义的视图。 此元素是必需的。

- [WideEntry](./wideentry-element-for-widecontrol-format.md)元素提供视图的定义。 至少一个[WideEntry](./wideentry-element-for-widecontrol-format.md)是必需的; 但是，没有任何可以添加的元素数目的最大限制。 在大多数情况下，将具有只有一个定义的视图。

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素指定所显示的特定定义的对象。 此元素是可选的仅当定义多个需要[WideEntry](./wideentry-element-for-widecontrol-format.md)元素，用于显示不同的对象。

- [WideItem](./wideitem-element-for-widecontrol-format.md)元素指定由该视图显示的数据。 相比其他类型的视图，宽控件可以显示只有一项。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素指定由该视图显示其值的属性。 必须指定一个属性或脚本，但不能同时指定。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素指定由该视图显示其值的脚本。 必须指定一个脚本或属性，但不能同时指定。

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md)元素指定用于显示数据的模式。 此元素是可选的。

有关完整的格式设置文件中定义的宽的视图定义示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。

## <a name="defining-the-objects-that-use-the-wide-view"></a>定义使用宽的视图的对象

有两种方法定义的.NET 对象使用宽的视图。 可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可显示的视图，或者您的所有定义的对象可以使用[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素来定义将显示哪些对象将视图的特定定义。 在大多数情况下，视图具有只有一个定义，因此对象通常由定义[ViewSelectedBy](./viewselectedby-element-format.md)元素。

下面的示例演示如何定义宽视图使用显示的对象[ViewSelectedBy](./viewselectedby-element-format.md)并[TypeName](./typename-element-for-viewselectedby-format.md)元素。 数量没有限制[TypeName](./typename-element-for-viewselectedby-format.md)元素可以指定和其顺序并不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

以下 XML 元素可以用于指定由宽的视图的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义宽视图将显示哪些对象。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素指定视图显示的.NET。 完全限定的.NET 类型名称是必需的。 必须指定至少一个类型或所选内容设置对于视图，但可以指定的元素没有最大数目。

有关完整的格式设置文件的示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。

下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)并[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。 使用的选项集，其中有一组相关的相同对象使用多个视图，例如何时定义较宽的视图和表视图显示的对象。 有关如何创建选项集的详细信息，请参阅[定义的选项集，](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

以下 XML 元素可以用于指定由宽的视图的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义宽视图将显示哪些对象。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定一组视图可以显示的对象。 必须指定至少一个选择集或类型视图，但可以指定的元素没有最大数目。

下面的示例演示如何定义宽视图使用的特定定义所显示的对象[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素。 使用此元素，可以指定将对象、 选择一组对象或选择条件，指定当使用定义的.NET 类型名称。 有关如何创建所选条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

以下 XML 元素可以用于指定使用特定的宽的视图定义的对象：

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素定义在定义将显示哪些对象。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素指定显示定义的.NET。 在使用此元素的完全限定的.NET 类型名称是必需。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素 （未显示） 指定一组可显示的此定义的对象。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)元素 （未显示） 指定要使用此定义中必须存在的条件。 必须指定至少一个类型、 所选内容集或选择条件的定义，但可以指定的元素没有最大数目。 有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>在较宽的视图中显示的对象的组

可以分隔成组宽的视图显示的对象。 这并不意味着定义组，仅特定属性或脚本的值发生更改时，Windows PowerShell 启动新的组。 在以下示例中，启动新的组时的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性更改。

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

有关定义组的完整格式设置文件的示例，请参阅[宽的视图 (GroupBy)](./wide-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字符串

格式设置字符串可以添加到较宽的视图来进一步定义数据的显示方式。 下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

可以使用以下 XML 元素来指定格式模式：

- [WideItem](./wideitem-element-for-widecontrol-format.md)元素指定由该视图显示的数据。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素指定由该视图显示其值的属性。 必须指定一个属性或脚本，但不能同时指定。

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md)元素指定的格式模式，它定义如何在视图中显示的属性或脚本的值

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素 （未显示） 指定其值显示通过视图的脚本。 必须指定一个脚本或属性，但不能同时指定。

在以下示例中，`ToString`调用方法来设置脚本的值的格式。 脚本可以调用一个对象的任何方法。 因此，如果对象具有一种方法，如`ToString`，具有格式设置参数，该脚本可以调用该方法，以设置脚本的输出值的格式。

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

下面的 XML 元素可用于调用`ToString`方法：

- [WideItem](./wideitem-element-for-widecontrol-format.md)元素指定由该视图显示的数据。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素 （未显示） 指定其值显示通过视图的脚本。 必须指定一个脚本或属性，但不能同时指定。

## <a name="see-also"></a>另请参阅

[宽的视图 (Basic)](./wide-view-basic.md)

[宽的视图 (GroupBy)](./wide-view-groupby.md)

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
