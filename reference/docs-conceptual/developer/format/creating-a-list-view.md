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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368976"
---
# <a name="creating-a-list-view"></a>创建列表视图

列表视图以单个列的顺序（按顺序）显示数据。 列表中显示的数据可以是 .NET 属性的值或脚本的值。

## <a name="a-list-view-display"></a>列表视图显示

以下输出显示了 Windows PowerShell 如何显示[system.serviceprocess. Servicecontroller 的属性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[get-help](/powershell/module/microsoft.powershell.management/get-service) Cmdlet 返回的 Fullname 对象。 在此示例中，返回了三个对象，每个对象都由一个空行与前面的对象隔开。

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

下面的 XML 演示了用于显示[system.serviceprocess. Servicecontroller 的多个属性的列表视图架构。Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)对象。 您必须指定要在列表视图中显示的每个属性。

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

- [View](./view-element-format.md)元素是列表视图的父元素。 （这是表、宽和自定义控件视图的相同父元素。）

- [Name](./name-element-for-view-format.md)元素指定视图的名称。 此元素对于所有视图都是必需的。

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义使用视图的对象。 此元素是必需的。

- [GroupBy](./groupby-element-for-view-format.md)元素定义何时显示新的对象组。 每当特定属性或脚本的值发生更改时，就会启动一个新组。 此元素是可选的。

- [Controls](./controls-element-for-view-format.md)元素定义由列表视图定义的自定义控件。 控件使您可以进一步指定数据的显示方式。 此元素是可选的。 视图可以定义自己的自定义控件，也可以使用可由格式设置文件中的任何视图使用的公共控件。 有关自定义控件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。

- [ListControl](./listcontrol-element-format.md)元素定义视图中显示的内容以及如何设置它的格式。 与所有其他视图类似，列表视图可以显示对象属性的值或脚本生成的值。

有关定义简单列表视图的完整格式化文件的示例，请参阅[列表视图（基本）](./list-view-basic.md)。

## <a name="providing-definitions-for-your-list-view"></a>为列表视图提供定义

列表视图可以通过使用[ListControl](./listcontrol-element-format.md)元素的子元素来提供一个或多个定义。 通常，视图将只有一个定义。 在下面的示例中，视图提供了一个定义，用于显示系统的多个属性[。Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process)对象。 列表视图可以显示属性的值或脚本的值（在此示例中未显示）。

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

以下 XML 元素可用于为列表视图提供定义：

- [ListControl](./listcontrol-element-format.md)元素及其子元素定义视图中显示的内容。

- [ListEntries](./listentries-element-for-listcontrol-format.md)元素提供视图的定义。 在大多数情况下，视图将只有一个定义。 此元素是必需的。

- [ListEntry](./listentry-element-for-listcontrol-format.md)元素提供视图的定义。 至少需要一个[ListEntry](./listentry-element-for-listcontrol-format.md) ;但是，可以添加的元素数没有最大限制。 在大多数情况下，视图将只有一个定义。

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素指定由特定定义显示的对象。 此元素是可选的，仅当定义显示不同对象的多个[ListEntry](./listentry-element-for-listcontrol-format.md)元素时才需要此元素。

- [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md)元素指定其值显示在列表视图的行中的属性和脚本。

- "[列表](./listitems-element-for-listentry-for-listcontrol-format.md)元素" 指定其值显示在列表视图的行中的属性或脚本。 列表视图必须至少指定一个属性或脚本。 对于可以指定的行数没有最大限制。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素指定其值显示在行中的属性。 您必须指定属性或脚本，但不能同时指定两者。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素指定其值在行中显示的脚本。 您必须指定脚本或属性，但不能同时指定两者。

- [Label](./label-element-for-listitem-for-listcontrol-format.md)元素指定在行中的属性或脚本值左侧显示的标签。 此元素是可选的。 如果未指定标签，则显示属性或脚本的名称。 有关完整示例，请参阅[列表视图（标签）](./list-view-labels.md)。

- [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)元素指定要显示的行必须存在的条件。 有关向列表视图添加条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。 此元素是可选的。

- [格式字符串](./formatstring-element-for-listitem-for-listcontrol-format.md)元素指定用于显示属性或脚本的值的模式。 此元素是可选的。

有关定义简单列表视图的完整格式化文件的示例，请参阅[列表视图（基本）](./list-view-basic.md)。

## <a name="defining-the-objects-that-use-the-list-view"></a>定义使用列表视图的对象

可以通过两种方法来定义哪些 .NET 对象使用列表视图。 您可以使用[ViewSelectedBy](./viewselectedby-element-format.md)元素来定义可由视图的所有定义显示的对象，也可以使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素来定义由视图的特定定义显示的对象。 在大多数情况下，视图只有一个定义，因此对象通常由[ViewSelectedBy](./viewselectedby-element-format.md)元素定义。

下面的示例演示如何使用[ViewSelectedBy](./viewselectedby-element-format.md)和[TypeName](./typename-element-for-viewselectedby-format.md)元素定义列表视图显示的对象。 对于您可以指定的[TypeName](./typename-element-for-viewselectedby-format.md)元素的数量没有限制，它们的顺序并不重要。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

以下 XML 元素可用于指定列表视图所使用的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图显示的对象。

- [TypeName](./typename-element-for-viewselectedby-format.md)元素指定视图显示的 .net 对象。 完全限定的 .NET 类型名称是必需的。 您必须为视图指定至少一个类型或选择集，但没有可指定的最大元素数。

有关完整格式化文件的示例，请参阅[列表视图（基本）](./list-view-basic.md)。

下面的示例使用[ViewSelectedBy](./viewselectedby-element-format.md)和[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素。 使用选择集，其中有一组使用多个视图显示的相关对象，例如为同一对象定义列表视图和表视图。 有关如何创建选项集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

以下 XML 元素可用于指定列表视图所使用的对象：

- [ViewSelectedBy](./viewselectedby-element-format.md)元素定义列表视图显示的对象。

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md)元素指定可由视图显示的一组对象。 您必须为视图指定至少一个选择集或类型，但没有可指定的最大元素数。

下面的示例演示如何使用[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素定义由列表视图的特定定义显示的对象。 使用此元素，可以指定对象的 .NET 类型名称、对象的选择集或指定何时使用定义的选择条件。 有关如何创建选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

以下 XML 元素可用于指定列表视图的特定定义所使用的对象：

- [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md)元素定义由定义显示的对象。

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md)元素指定由定义显示的 .net 对象。 使用此元素时，必须提供完全限定的 .NET 类型名称。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)元素（未显示）指定可由此定义显示的一组对象。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。

- [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)元素（未显示）指定必须存在的条件才能使用此定义。 您必须为定义至少指定一个类型、选择集或选择条件，但没有可指定的最大元素数。 有关定义选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。

## <a name="displaying-groups-of-objects-in-a-list-view"></a>在列表视图中显示对象组

可以将列表视图显示的对象划分为多个组。 这并不意味着你要定义一个组，只要特定属性或脚本的值发生变化，Windows PowerShell 就会启动一个新组。 在下面的示例中，只要[system.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性的值发生更改，就会启动一个新组。

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

有关定义组的完整格式化文件的示例，请参阅[列表视图（GroupBy）](./list-view-groupby.md)。

## <a name="using-format-strings"></a>使用格式字符串

可以将字符串的格式添加到视图中，以便进一步定义数据的显示方式。 下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

以下 XML 元素可用于指定格式模式：

- "[出现](./listitem-element-for-listitems-for-listcontrol-format.md)类型" 元素指定视图显示的数据。

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素指定其值由视图显示的属性。 您必须指定属性或脚本，但不能同时指定两者。

- "格式[字符串](./formatstring-element-for-listitem-for-listcontrol-format.md)" 元素指定定义属性或脚本值在视图中显示方式的格式模式。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素（未显示）指定其值由视图显示的脚本。 您必须指定脚本或属性，但不能同时指定两者。

在下面的示例中，调用 `ToString` 方法来设置脚本的值的格式。 脚本可以调用对象的任何方法。 因此，如果对象有一个具有格式参数的方法（如 `ToString`），则脚本可以调用该方法来设置脚本的输出值的格式。

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

以下 XML 元素可用于调用 `ToString` 方法：

- "[出现](./listitem-element-for-listitems-for-listcontrol-format.md)类型" 元素指定视图显示的数据。

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素（未显示）指定其值由视图显示的脚本。 您必须指定脚本或属性，但不能同时指定两者。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
