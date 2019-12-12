---
title: 扩展对象的属性 |Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364446"
---
# <a name="extending-properties-for-objects"></a>扩展对象的属性

扩展 .NET Framework 对象时，可以将别名属性、代码属性、备注属性、脚本属性和属性集添加到对象。 以下部分介绍了定义这些属性的 XML。

> [!NOTE]
> 以下部分中的示例来自 PowerShell 安装目录中的默认 `Types.ps1xml` 类型文件（`$PSHOME`）。 有关详细信息，请参阅[关于 types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。

## <a name="alias-properties"></a>别名属性

Alias 属性定义现有属性的新名称。

在下面的示例中， **Count**属性添加到了[system.object](/dotnet/api/System.Array)类型中。 [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty)元素将扩展属性定义为别名属性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定新名称。 [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername)元素指定别名引用的现有属性。 还可以将 `AliasProperty` 元素添加到[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成员。

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a>代码属性

一个代码属性引用 .NET Framework 对象的静态属性。

在下面的示例中， **Mode**属性添加到[DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo)类型中。 [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty)元素将扩展属性定义为代码属性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定扩展属性的名称。 [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference)元素定义扩展属性引用的静态方法。 还可以将 `CodeProperty` 元素添加到[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成员。

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a>记下属性

Note 属性定义具有静态值的属性。

在下面的示例中， **Status**属性（其值始终为 "**成功**"）将添加到[DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo)类型中。 [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty)元素将扩展属性定义为附注属性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定扩展属性的名称。 [值](/dotnet/api/system.management.automation.psnoteproperty.value)元素指定扩展属性的静态值。 还可以将 `NoteProperty` 元素添加到[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成员。

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a>脚本属性

脚本属性定义一个属性，其值为脚本的输出。

在下面的示例中，将**VersionInfo**属性添加到[FileInfo](/dotnet/api/System.IO.FileInfo)类型。 [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty)元素将扩展属性定义为脚本属性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定扩展属性的名称。 [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript)元素指定生成属性值的脚本。 还可以将 `ScriptProperty` 元素添加到[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成员。

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a>属性集

属性集定义一组可由集名称引用的扩展属性。
例如，[格式表](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**属性**参数可以指定要显示的特定属性集。 指定属性集时，仅显示属于该集的属性。

对于可以为对象定义的属性集的数量没有限制。 但是，必须在**PSStandardMembers**成员集中指定用于定义对象的默认显示属性的属性集。 在 `Types.ps1xml` 类型文件中，默认属性集名称包括**DefaultDisplayProperty**、**使用 defaultdisplaypropertyset**和**DefaultKeyPropertySet**。 将忽略添加到**PSStandardMembers**成员集中的任何其他属性集。

在下面的示例中，**使用 defaultdisplaypropertyset**属性集添加到[System.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController)类型的**PSStandardMembers**成员集中。 [PropertySet](/dotnet/api/system.management.automation.pspropertyset)元素定义一组属性。 [Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定属性集的名称。 和， [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames)元素指定集的属性。 还可以将 `PropertySet` 元素添加到[Type](/dotnet/api/system.management.automation.pstypename)元素的成员。

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a>另请参阅

[关于类型. types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System.object](/dotnet/api/System.Management.Automation)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
