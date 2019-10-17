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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364446"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="c8c6d-102">扩展对象的属性</span><span class="sxs-lookup"><span data-stu-id="c8c6d-102">Extending Properties for Objects</span></span>

<span data-ttu-id="c8c6d-103">扩展 .NET Framework 对象时，可以将别名属性、代码属性、备注属性、脚本属性和属性集添加到对象。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="c8c6d-104">以下部分介绍了定义这些属性的 XML。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="c8c6d-105">以下部分中的示例来自 PowerShell 安装目录中的默认 `Types.ps1xml` 类型文件（`$PSHOME`）。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="c8c6d-106">有关详细信息，请参阅[关于 types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="c8c6d-107">别名属性</span><span class="sxs-lookup"><span data-stu-id="c8c6d-107">Alias properties</span></span>

<span data-ttu-id="c8c6d-108">Alias 属性定义现有属性的新名称。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="c8c6d-109">在下面的示例中， **Count**属性添加到了[system.object](/dotnet/api/System.Array)类型中。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="c8c6d-110">[AliasProperty](/dotnet/api/system.management.automation.psaliasproperty)元素将扩展属性定义为别名属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="c8c6d-111">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定新名称。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="c8c6d-112">[ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername)元素指定别名引用的现有属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="c8c6d-113">你还可以将 `AliasProperty` 元素添加到[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成员。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="c8c6d-114">代码属性</span><span class="sxs-lookup"><span data-stu-id="c8c6d-114">Code properties</span></span>

<span data-ttu-id="c8c6d-115">一个代码属性引用 .NET Framework 对象的静态属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="c8c6d-116">在下面的示例中， **Mode**属性添加到[DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo)类型中。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="c8c6d-117">[CodeProperty](/dotnet/api/system.management.automation.pscodeproperty)元素将扩展属性定义为代码属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="c8c6d-118">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="c8c6d-119">[GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference)元素定义扩展属性引用的静态方法。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="c8c6d-120">你还可以将 `CodeProperty` 元素添加到[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成员。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="c8c6d-121">注释属性</span><span class="sxs-lookup"><span data-stu-id="c8c6d-121">Note properties</span></span>

<span data-ttu-id="c8c6d-122">Note 属性定义具有静态值的属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="c8c6d-123">在下面的示例中， **Status**属性（其值始终为 "**成功**"）将添加到[DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo)类型中。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="c8c6d-124">[NoteProperty](/dotnet/api/system.management.automation.psnoteproperty)元素将扩展属性定义为附注属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="c8c6d-125">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="c8c6d-126">[值](/dotnet/api/system.management.automation.psnoteproperty.value)元素指定扩展属性的静态值。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="c8c6d-127">也可以将 `NoteProperty` 元素添加到[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成员。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="c8c6d-128">脚本属性</span><span class="sxs-lookup"><span data-stu-id="c8c6d-128">Script properties</span></span>

<span data-ttu-id="c8c6d-129">脚本属性定义一个属性，其值为脚本的输出。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="c8c6d-130">在下面的示例中，将**VersionInfo**属性添加到[FileInfo](/dotnet/api/System.IO.FileInfo)类型。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="c8c6d-131">[ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty)元素将扩展属性定义为脚本属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="c8c6d-132">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="c8c6d-133">[GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript)元素指定生成属性值的脚本。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="c8c6d-134">你还可以将 `ScriptProperty` 元素添加到[MemberSets](/dotnet/api/system.management.automation.psmemberset)元素的成员。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="c8c6d-135">属性集</span><span class="sxs-lookup"><span data-stu-id="c8c6d-135">Property sets</span></span>

<span data-ttu-id="c8c6d-136">属性集定义一组可由集名称引用的扩展属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="c8c6d-137">例如，[格式表](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**属性**参数可以指定要显示的特定属性集。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="c8c6d-138">指定属性集时，仅显示属于该集的属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="c8c6d-139">对于可以为对象定义的属性集的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="c8c6d-140">但是，必须在**PSStandardMembers**成员集中指定用于定义对象的默认显示属性的属性集。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="c8c6d-141">在 `Types.ps1xml` 类型文件中，默认属性集名称包括**DefaultDisplayProperty**、**使用 defaultdisplaypropertyset**和**DefaultKeyPropertySet**。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="c8c6d-142">将忽略添加到**PSStandardMembers**成员集中的任何其他属性集。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="c8c6d-143">在下面的示例中，**使用 defaultdisplaypropertyset**属性集添加到[System.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController)类型的**PSStandardMembers**成员集中。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="c8c6d-144">[PropertySet](/dotnet/api/system.management.automation.pspropertyset)元素定义一组属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="c8c6d-145">[Name](/dotnet/api/system.management.automation.psmemberinfo.name)元素指定属性集的名称。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="c8c6d-146">和， [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames)元素指定集的属性。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="c8c6d-147">你还可以将 `PropertySet` 元素添加到[Type](/dotnet/api/system.management.automation.pstypename)元素的成员。</span><span class="sxs-lookup"><span data-stu-id="c8c6d-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c8c6d-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8c6d-148">See also</span></span>

[<span data-ttu-id="c8c6d-149">关于类型. types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="c8c6d-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="c8c6d-150">System.object</span><span class="sxs-lookup"><span data-stu-id="c8c6d-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="c8c6d-151">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c8c6d-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
