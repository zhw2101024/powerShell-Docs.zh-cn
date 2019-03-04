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
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854523"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="1c191-102">扩展对象的属性</span><span class="sxs-lookup"><span data-stu-id="1c191-102">Extending Properties for Objects</span></span>

<span data-ttu-id="1c191-103">扩展.NET Framework 对象时，您可以将别名属性、 代码属性、 便笺属性、 脚本属性和属性集的对象。</span><span class="sxs-lookup"><span data-stu-id="1c191-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="1c191-104">以下各节介绍了用于定义这些属性的 XML。</span><span class="sxs-lookup"><span data-stu-id="1c191-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="1c191-105">以下各节中的示例是从 Windows PowerShell 安装目录中的默认 Types.ps1xml 类型文件 (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="1c191-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="1c191-106">别名属性</span><span class="sxs-lookup"><span data-stu-id="1c191-106">Alias Properties</span></span>

<span data-ttu-id="1c191-107">别名属性定义的现有属性的新名称。</span><span class="sxs-lookup"><span data-stu-id="1c191-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="1c191-108">在以下示例中，`Count`属性添加到[System.Array？Displayproperty =](/dotnet/api/System.Array)类型。</span><span class="sxs-lookup"><span data-stu-id="1c191-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="1c191-109">[AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1)元素定义的扩展的属性作为别名属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="1c191-110">[名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的新名称。</span><span class="sxs-lookup"><span data-stu-id="1c191-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="1c191-111">并且， [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a)元素指定由该别名引用的现有属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="1c191-112">(您还可以添加[AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1)元素的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)</span><span class="sxs-lookup"><span data-stu-id="1c191-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="1c191-113">代码属性</span><span class="sxs-lookup"><span data-stu-id="1c191-113">Code Properties</span></span>

<span data-ttu-id="1c191-114">代码属性引用的.NET Framework 对象的静态属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="1c191-115">在以下示例中，`Node`属性添加到[System.IO.Directoryinfo？Displayproperty =](/dotnet/api/System.IO.DirectoryInfo)类型。</span><span class="sxs-lookup"><span data-stu-id="1c191-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="1c191-116">[CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db)元素中定义的扩展的属性为代码属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="1c191-117">[名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="1c191-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="1c191-118">并且， [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0)元素定义引用的扩展属性的静态方法。</span><span class="sxs-lookup"><span data-stu-id="1c191-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="1c191-119">(您还可以添加[CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db)元素的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)</span><span class="sxs-lookup"><span data-stu-id="1c191-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="1c191-120">请注意属性</span><span class="sxs-lookup"><span data-stu-id="1c191-120">Note Properties</span></span>

<span data-ttu-id="1c191-121">请注意属性定义具有静态值的属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="1c191-122">在以下示例中，`Status`属性 （其值始终为"成功"） 添加到[System.IO.Directoryinfo？Displayproperty =](/dotnet/api/System.IO.DirectoryInfo)类型。</span><span class="sxs-lookup"><span data-stu-id="1c191-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="1c191-123">[NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb)元素中定义的扩展的属性的附注属性; 为[名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定名称的扩展属性; 并[值](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c)元素指定扩展属性的静态值。</span><span class="sxs-lookup"><span data-stu-id="1c191-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="1c191-124">( [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb)还可以将元素添加到的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)</span><span class="sxs-lookup"><span data-stu-id="1c191-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="1c191-125">脚本属性</span><span class="sxs-lookup"><span data-stu-id="1c191-125">Script Properties</span></span>

<span data-ttu-id="1c191-126">脚本属性定义其值为脚本的输出的属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="1c191-127">在以下示例中，`VersionInfo`属性添加到[System.IO.Fileinfo？Displayproperty =](/dotnet/api/System.IO.FileInfo)类型。</span><span class="sxs-lookup"><span data-stu-id="1c191-127">In the following example, the `VersionInfo` property is added to the [System.IO.Fileinfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="1c191-128">[ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350)元素定义的扩展的属性作为脚本属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="1c191-129">[名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="1c191-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="1c191-130">并且， [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c)元素指定生成的属性值的脚本。</span><span class="sxs-lookup"><span data-stu-id="1c191-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="1c191-131">(您还可以添加[ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350)元素的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)</span><span class="sxs-lookup"><span data-stu-id="1c191-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="1c191-132">属性集</span><span class="sxs-lookup"><span data-stu-id="1c191-132">Property Sets</span></span>

<span data-ttu-id="1c191-133">属性集定义扩展集的名称，可以引用的属性的组。</span><span class="sxs-lookup"><span data-stu-id="1c191-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="1c191-134">例如，`Property`的参数[Format-table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet 可以指定特定的属性设置为显示。</span><span class="sxs-lookup"><span data-stu-id="1c191-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="1c191-135">当指定了属性集时，显示属于集的那些属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>
<span data-ttu-id="1c191-136">属性集定义扩展集的名称，可以引用的属性的组。</span><span class="sxs-lookup"><span data-stu-id="1c191-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="1c191-137">例如，`Property`的参数[Format-table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet 可以指定特定的属性设置为显示。</span><span class="sxs-lookup"><span data-stu-id="1c191-137">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="1c191-138">当指定了属性集时，显示属于集的那些属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="1c191-139">可以为对象定义的属性集的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="1c191-139">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="1c191-140">但是，必须在 PSStandardMembers 成员组中指定用于定义对象的默认显示属性的属性集。</span><span class="sxs-lookup"><span data-stu-id="1c191-140">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="1c191-141">在 Types.ps1xml 类型文件中，默认属性集名称包括 DefaultDisplayProperty、 DefaultDisplayPropertySet 和 DefaultKeyPropertySet。</span><span class="sxs-lookup"><span data-stu-id="1c191-141">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="1c191-142">您将添加到 PSStandardMembers 成员集的任何其他属性集将被忽略。</span><span class="sxs-lookup"><span data-stu-id="1c191-142">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="1c191-143">在以下示例中，DefaultDisplayPropertySet 属性集添加到 PSStandardMembers 成员集的[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)类型。</span><span class="sxs-lookup"><span data-stu-id="1c191-143">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="1c191-144">[PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188)元素定义的属性组。</span><span class="sxs-lookup"><span data-stu-id="1c191-144">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="1c191-145">[名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的属性集的名称。</span><span class="sxs-lookup"><span data-stu-id="1c191-145">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="1c191-146">并且， [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786)元素指定集的属性。</span><span class="sxs-lookup"><span data-stu-id="1c191-146">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="1c191-147">(您还可以添加[PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188)元素的成员[类型](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe)元素。)</span><span class="sxs-lookup"><span data-stu-id="1c191-147">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1c191-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c191-148">See Also</span></span>

[<span data-ttu-id="1c191-149">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c191-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
