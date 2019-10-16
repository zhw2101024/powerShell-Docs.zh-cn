---
title: 扩展输出对象 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369716"
---
# <a name="extending-output-objects"></a><span data-ttu-id="3f7da-102">扩展输出对象</span><span class="sxs-lookup"><span data-stu-id="3f7da-102">Extending Output Objects</span></span>

<span data-ttu-id="3f7da-103">你可以使用类型文件（. types.ps1xml）扩展由 cmdlet、函数和脚本返回的 .NET Framework 对象。</span><span class="sxs-lookup"><span data-stu-id="3f7da-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="3f7da-104">类型文件是基于 XML 的文件，可用于向现有对象添加属性和方法。</span><span class="sxs-lookup"><span data-stu-id="3f7da-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="3f7da-105">例如，Windows PowerShell 提供 types.ps1xml 文件，该文件将元素添加到多个现有的 .NET Framework 对象。</span><span class="sxs-lookup"><span data-stu-id="3f7da-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="3f7da-106">Types.ps1xml 文件位于 Windows PowerShell 安装目录（`$pshome`）中。</span><span class="sxs-lookup"><span data-stu-id="3f7da-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="3f7da-107">您可以创建自己的类型文件，以便进一步扩展这些对象或扩展其他对象。</span><span class="sxs-lookup"><span data-stu-id="3f7da-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="3f7da-108">使用类型文件扩展对象时，会使用新元素扩展对象的任何实例。</span><span class="sxs-lookup"><span data-stu-id="3f7da-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="3f7da-109">扩展 System.object 对象</span><span class="sxs-lookup"><span data-stu-id="3f7da-109">Extending the System.Array Object</span></span>

<span data-ttu-id="3f7da-110">下面的示例演示 Windows PowerShell 如何在 types.ps1xml 文件中扩展[system.object](/dotnet/api/System.Array)对象。</span><span class="sxs-lookup"><span data-stu-id="3f7da-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="3f7da-111">默认情况下， [system.object](/dotnet/api/System.Array)对象有一个 `Length` 属性，该属性列出数组中对象的数量。</span><span class="sxs-lookup"><span data-stu-id="3f7da-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="3f7da-112">但是，由于名称 "length" 未清楚地描述属性，因此 Windows PowerShell 将添加 `Count` alias 属性，该属性显示与 @no__t 1 属性相同的值。</span><span class="sxs-lookup"><span data-stu-id="3f7da-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="3f7da-113">下面的 XML 将 `Count` 属性添加到[system.object](/dotnet/api/System.Array)类型。</span><span class="sxs-lookup"><span data-stu-id="3f7da-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="3f7da-114">若要查看此新的别名属性，请在任何数组上使用[Get 成员](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)命令，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="3f7da-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="3f7da-115">该命令将返回以下结果。</span><span class="sxs-lookup"><span data-stu-id="3f7da-115">The command returns the following results.</span></span>
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
<span data-ttu-id="3f7da-116">您可以使用 `Count` 属性或 @no__t 属性来确定数组中有多少个对象。</span><span class="sxs-lookup"><span data-stu-id="3f7da-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="3f7da-117">例如：</span><span class="sxs-lookup"><span data-stu-id="3f7da-117">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="3f7da-118">自定义类型文件</span><span class="sxs-lookup"><span data-stu-id="3f7da-118">Custom Types Files</span></span>

<span data-ttu-id="3f7da-119">若要创建自定义类型文件，请首先复制现有的类型文件。</span><span class="sxs-lookup"><span data-stu-id="3f7da-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="3f7da-120">新文件可以具有任何名称，但它必须具有 types.ps1xml 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="3f7da-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="3f7da-121">复制文件时，您可以将新文件放置在可供 Windows PowerShell 访问的任何目录中，但将文件放在 Windows PowerShell 安装目录（`$pshome`）或安装目录的子目录中会很有用。</span><span class="sxs-lookup"><span data-stu-id="3f7da-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="3f7da-122">若要将自己的扩展类型添加到文件中，请为要扩展的每个对象添加类型元素。</span><span class="sxs-lookup"><span data-stu-id="3f7da-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="3f7da-123">以下主题提供了示例。</span><span class="sxs-lookup"><span data-stu-id="3f7da-123">The following topics provide examples.</span></span>

- <span data-ttu-id="3f7da-124">有关添加属性和属性集的详细信息，请参阅[扩展属性](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="3f7da-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="3f7da-125">有关添加方法的详细信息，请参阅[扩展方法](./defining-default-methods-for-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="3f7da-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="3f7da-126">有关添加成员集的详细信息，请参阅[扩展成员集](./defining-default-member-sets-for-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="3f7da-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="3f7da-127">定义自己的扩展类型后，请使用以下方法之一来使扩展对象可用：</span><span class="sxs-lookup"><span data-stu-id="3f7da-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="3f7da-128">若要使扩展类型文件可用于当前会话，请使用[update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet 添加新的文件。</span><span class="sxs-lookup"><span data-stu-id="3f7da-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="3f7da-129">如果你希望你的类型优先于其他类型文件（包括 types.ps1xml 文件）中定义的类型，请使用[update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet 的 `PrependData` 参数。</span><span class="sxs-lookup"><span data-stu-id="3f7da-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="3f7da-130">若要使扩展类型文件可供所有未来会话使用，请将类型文件添加到模块，导出当前会话，或将[update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData)命令添加到 Windows PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="3f7da-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="3f7da-131">签名类型文件</span><span class="sxs-lookup"><span data-stu-id="3f7da-131">Signing Types Files</span></span>

<span data-ttu-id="3f7da-132">应对类型文件进行数字签名以防止篡改，因为 XML 可以包含脚本块。</span><span class="sxs-lookup"><span data-stu-id="3f7da-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="3f7da-133">有关添加数字签名的详细信息，请参阅[about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="3f7da-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="3f7da-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f7da-134">See Also</span></span>

[<span data-ttu-id="3f7da-135">定义对象的默认属性</span><span class="sxs-lookup"><span data-stu-id="3f7da-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="3f7da-136">定义对象的默认方法</span><span class="sxs-lookup"><span data-stu-id="3f7da-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="3f7da-137">定义对象的默认成员集</span><span class="sxs-lookup"><span data-stu-id="3f7da-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="3f7da-138">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3f7da-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
