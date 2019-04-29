---
title: 将属性扩展的对象 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 496e363b041194563d46c09eee67a12055bb54b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068141"
---
# <a name="extending-properties-for-objects"></a>扩展对象的属性

扩展.NET Framework 对象时，您可以将别名属性、 代码属性、 便笺属性、 脚本属性和属性集的对象。 以下各节介绍了用于定义这些属性的 XML。

> [!NOTE]
> 以下各节中的示例是从 Windows PowerShell 安装目录中的默认 Types.ps1xml 类型文件 (`$pshome`)。

## <a name="alias-properties"></a>别名属性

别名属性定义的现有属性的新名称。

在以下示例中，`Count`属性添加到[System.Array？Displayproperty =](/dotnet/api/System.Array)类型。 [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1)元素定义的扩展的属性作为别名属性。 [名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的新名称。 并且， [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a)元素指定由该别名引用的现有属性。 (您还可以添加[AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1)元素的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)

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

代码属性引用的.NET Framework 对象的静态属性。

在以下示例中，`Node`属性添加到[System.IO.Directoryinfo？Displayproperty =](/dotnet/api/System.IO.DirectoryInfo)类型。 [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db)元素中定义的扩展的属性为代码属性。 [名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的扩展属性的名称。 并且， [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0)元素定义引用的扩展属性的静态方法。 (您还可以添加[CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db)元素的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)

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

## <a name="note-properties"></a>请注意属性

请注意属性定义具有静态值的属性。

在以下示例中，`Status`属性 （其值始终为"成功"） 添加到[System.IO.Directoryinfo？Displayproperty =](/dotnet/api/System.IO.DirectoryInfo)类型。 [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb)元素中定义的扩展的属性的附注属性; 为[名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定名称的扩展属性; 并[值](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c)元素指定扩展属性的静态值。 ( [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb)还可以将元素添加到的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)

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

脚本属性定义其值为脚本的输出的属性。

在以下示例中，`VersionInfo`属性添加到[System.IO.FileInfo？Displayproperty =](/dotnet/api/System.IO.FileInfo)类型。 [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350)元素定义的扩展的属性作为脚本属性。 [名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的扩展属性的名称。 并且， [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c)元素指定生成的属性值的脚本。 (您还可以添加[ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350)元素的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)

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

属性集定义扩展集的名称，可以引用的属性的组。 例如，`Property`的参数[Format-table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet 可以指定特定的属性设置为显示。 当指定了属性集时，显示属于集的那些属性。

可以为对象定义的属性集的数量没有限制。 但是，必须在 PSStandardMembers 成员组中指定用于定义对象的默认显示属性的属性集。 在 Types.ps1xml 类型文件中，默认属性集名称包括 DefaultDisplayProperty、 DefaultDisplayPropertySet 和 DefaultKeyPropertySet。 您将添加到 PSStandardMembers 成员集的任何其他属性集将被忽略。

在以下示例中，DefaultDisplayPropertySet 属性集添加到 PSStandardMembers 成员集的[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)类型。 [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188)元素定义的属性组。 [名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的属性集的名称。 并且， [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786)元素指定集的属性。 (您还可以添加[PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188)元素的成员[类型](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe)元素。)

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

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
