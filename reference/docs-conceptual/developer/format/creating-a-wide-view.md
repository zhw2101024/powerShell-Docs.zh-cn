---
title: 创建宽视图 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368946"
---
# <a name="creating-a-wide-view"></a>创建宽视图

宽视图为显示的每个对象显示单个值。 显示的值可以是 .NET 对象属性的值或脚本的值。 默认情况下，此视图没有标签或标题。

## <a name="a-wide-view-display"></a>宽视图显示

下面的示例演示了 Windows PowerShell 如何显示在将其输出传送到[格式范围](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide)cmdlet 时由[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 返回的[system.object](/dotnet/api/System.Diagnostics.Process)对象。 （默认情况下，[获取进程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)cmdlet 返回表视图。）在此示例中，两个列用于显示每个返回对象的进程的名称。 不显示对象属性的名称，只显示属性的值。

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

下面的 XML 显示了[system.object](/dotnet/api/System.Diagnostics.Process)对象的宽视图架构。

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

以下 XML 元素用于定义宽视图：

- [View](./view-element-format.md)元素是宽视图的父元素。 （这是表、列表和自定义控件视图的相同父元素。）

- [Name](./name-element-for-view-format.md)元素指定视图的名称。 此元素对于所有视图都是必需的。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。 此元素是必需的。

- [GroupBy](./groupby-element-for-view-format.md)元素定义何时显示新的对象组。 每当特定属性或脚本的值发生更改时，就会启动一个新组。 此元素是可选的。

- [Controls](./controls-element-for-view-format.md)元素定义由宽视图定义的自定义控件。 控件使您可以进一步指定数据的显示方式。 此元素是可选的。 视图可以定义自己的自定义控件，也可以使用可由格式设置文件中的任何视图使用的公共控件。 有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

- [WideControl](./widecontrol-element-format.md)元素及其子元素定义视图中显示的内容。 在前面的示例中，视图设计为显示[Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)属性。

有关定义简单宽视图的完整格式化文件的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。

## <a name="providing-definitions-for-your-wide-view"></a>为宽视图提供定义

宽视图可以通过使用[WideControl](./widecontrol-element-format.md)元素的子元素来提供一个或多个定义。 通常，视图将只有一个定义。 在下面的示例中，视图提供了一个显示[Processname](/dotnet/api/System.Diagnostics.Process.ProcessName)属性值的定义。 宽视图可以显示属性的值或脚本的值（示例中未显示）。

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

以下 XML 元素可用于为宽视图提供定义：

- [WideControl](./widecontrol-element-format.md)元素及其子元素定义视图中显示的内容。

- [AutoSize](./autosize-element-for-widecontrol-format.md)元素指定是否根据数据大小调整列大小和列数。 此元素是可选的。

- [ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素指定在宽视图中显示的列数。 此元素是可选的。

- [WideEntries](./wideentries-element-for-widecontrol-format.md)元素提供视图的定义。 在大多数情况下，视图将只有一个定义。 此元素是必需的。

- [WideEntry](./wideentry-element-for-widecontrol-format.md)元素提供视图的定义。 至少需要一个[WideEntry](./wideentry-element-for-widecontrol-format.md) ;但是，可以添加的元素数没有最大限制。 在大多数情况下，视图将只有一个定义。

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素指定由特定定义显示的对象。 此元素是可选的，仅当定义显示不同对象的多个[WideEntry](./wideentry-element-for-widecontrol-format.md)元素时才需要此元素。

- [WideItem](./wideitem-element-for-widecontrol-format.md)元素指定视图显示的数据。 与其他类型的视图不同，范围广泛的控件只能显示一项。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素指定其值由视图显示的属性。 您必须指定属性或脚本，但不能同时指定两者。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素指定其值由视图显示的脚本。 您必须指定脚本或属性，但不能同时指定两者。

- "[格式字符串](./formatstring-element-for-wideitem-for-widecontrol-format.md)" 元素指定用于显示数据的模式。 此元素是可选的。

有关定义宽视图定义的完整格式化文件的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。

## <a name="defining-the-objects-that-use-the-wide-view"></a>定义使用大视图的对象

可以通过两种方法来定义哪些 .NET 对象使用宽视图。 您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可由视图的所有定义显示的对象，也可以使用[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素来定义由视图的特定定义显示的对象。 在大多数情况下，视图只有一个定义，因此对象通常由[ViewSelectedBy](./viewselectedby-element-format.md)元素定义。

下面的示例演示如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定义宽视图显示的对象。 对于您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素的数量没有限制，它们的顺序并不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

以下 XML 元素可用于指定宽视图使用的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义宽视图显示的对象。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素指定视图显示的 .net。 完全限定的 .NET 类型名称是必需的。 您必须为视图指定至少一个类型或选择集，但没有可指定的最大元素数。

有关完整格式化文件的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。

下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。 使用选择集，其中有一组使用多个视图显示的相关对象，例如为同一对象定义宽视图和表视图。 有关如何创建选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

以下 XML 元素可用于指定宽视图使用的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义宽视图显示的对象。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定可由视图显示的一组对象。 您必须为视图指定至少一个选择集或类型，但没有可指定的最大元素数。

下面的示例演示如何使用[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素定义由宽视图的特定定义显示的对象。 使用此元素，可以指定对象的 .NET 类型名称、对象的选择集或指定何时使用定义的选择条件。 有关如何创建选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

以下 XML 元素可用于指定由大视图的特定定义使用的对象：

- [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md)元素定义由定义显示的对象。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素指定由定义显示的 .net。 使用此元素时，需要完全限定的 .NET 类型名称。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素（未显示）指定可由此定义显示的一组对象。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)元素（未显示）指定必须存在的条件才能使用此定义。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。 有关定义选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>以宽视图显示对象组

您可以将由宽视图显示的对象划分为多个组。 这并不意味着你要定义一个组，只要特定属性或脚本的值发生变化，Windows PowerShell 就会启动一个新组。 在下面的示例中，只要[system.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性的值发生更改，就会启动一个新组。

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

以下 XML 元素用于定义组的启动时间：

- [GroupBy](./groupby-element-for-view-format.md)元素定义用于启动新组和定义组显示方式的属性或脚本。

- [PropertyName](./propertyname-element-for-groupby-format.md)元素指定在其值更改时启动新组的属性。 您必须指定一个属性或脚本来启动组，但不能同时指定两者。

- [ScriptBlock](./scriptblock-element-for-groupby-format.md)元素指定在其值更改时启动新组的脚本。 您必须指定脚本或属性以启动组，但不能同时指定两者。

- [标签](./label-element-for-groupby-format.md)元素定义在每个组的开头显示的标签。 除了此元素指定的文本，Windows PowerShell 还显示触发新组的值，并在标签之前和之后添加一个空白行。 此元素是可选的。

- [CustomControl](./customcontrol-element-for-groupby-format.md)元素定义用于显示数据的控件。 此元素是可选的。

- [CustomControlName](./customcontrolname-element-for-groupby-format.md)元素指定用于显示数据的通用控件或视图控件。 此元素是可选的。

有关定义组的完整格式化文件的示例，请参阅[宽视图（GroupBy）](./wide-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字符串

可以将字符串的格式添加到宽视图，进一步定义数据的显示方式。 下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

以下 XML 元素可用于指定格式模式：

- [WideItem](./wideitem-element-for-widecontrol-format.md)元素指定视图显示的数据。

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md)元素指定其值由视图显示的属性。 您必须指定属性或脚本，但不能同时指定两者。

- "格式[字符串](./formatstring-element-for-wideitem-for-widecontrol-format.md)" 元素指定定义属性或脚本值在视图中显示方式的格式模式

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素（未显示）指定其值由视图显示的脚本。 您必须指定脚本或属性，但不能同时指定两者。

在下面的示例中，调用 `ToString` 方法来设置脚本的值的格式。 脚本可以调用对象的任何方法。 因此，如果对象有一个具有格式参数的方法（如 `ToString`），则脚本可以调用该方法来设置脚本的输出值的格式。

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

以下 XML 元素可用于调用 `ToString` 方法：

- [WideItem](./wideitem-element-for-widecontrol-format.md)元素指定视图显示的数据。

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md)元素（未显示）指定其值由视图显示的脚本。 您必须指定脚本或属性，但不能同时指定两者。

## <a name="see-also"></a>另请参阅

[宽视图（基本）](./wide-view-basic.md)

[宽视图（GroupBy）](./wide-view-groupby.md)

[编写 PowerShell 格式化文件](./writing-a-powershell-formatting-file.md)
