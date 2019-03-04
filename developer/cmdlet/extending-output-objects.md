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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861923"
---
# <a name="extending-output-objects"></a><span data-ttu-id="bff12-102">扩展输出对象</span><span class="sxs-lookup"><span data-stu-id="bff12-102">Extending Output Objects</span></span>

<span data-ttu-id="bff12-103">您可以扩展的.NET Framework 对象使用的类型文件 (.ps1xml) 返回的 cmdlet、 函数和脚本。</span><span class="sxs-lookup"><span data-stu-id="bff12-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="bff12-104">类型文件是基于 XML 的文件，可将属性和方法添加到现有对象。</span><span class="sxs-lookup"><span data-stu-id="bff12-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="bff12-105">例如，Windows PowerShell 提供了将元素添加到多个现有的.NET Framework 对象的 Types.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="bff12-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="bff12-106">Types.ps1xml 文件位于 Windows PowerShell 安装目录 (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="bff12-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="bff12-107">可以创建自己的类型文件来进一步扩展这些对象或将扩展的其他对象。</span><span class="sxs-lookup"><span data-stu-id="bff12-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="bff12-108">时使用的类型文件扩展对象，该对象的任何实例进行扩展的新元素。</span><span class="sxs-lookup"><span data-stu-id="bff12-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="bff12-109">扩展 System.Array 对象</span><span class="sxs-lookup"><span data-stu-id="bff12-109">Extending the System.Array Object</span></span>

<span data-ttu-id="bff12-110">下面的示例演示如何扩展 Windows PowerShell [System.Array](/dotnet/api/System.Array) Types.ps1xml 文件中的对象。</span><span class="sxs-lookup"><span data-stu-id="bff12-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="bff12-111">默认情况下[System.Array](/dotnet/api/System.Array)对象具有`Length`列出的数组中对象的属性。</span><span class="sxs-lookup"><span data-stu-id="bff12-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="bff12-112">但是，由于名称"长度"不清楚地描述该属性，因此 Windows PowerShell 添加`Count`别名属性，其中显示了相同的值`Length`属性。</span><span class="sxs-lookup"><span data-stu-id="bff12-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="bff12-113">下面的 XML 将添加`Count`属性设置为[System.Array](/dotnet/api/System.Array)类型。</span><span class="sxs-lookup"><span data-stu-id="bff12-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="bff12-114">若要查看这个新的别名属性，请使用[Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)命令任何阵列上，在下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="bff12-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="bff12-115">该命令返回以下结果。</span><span class="sxs-lookup"><span data-stu-id="bff12-115">The command returns the following results.</span></span>
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
<span data-ttu-id="bff12-116">你可以使用`Count`属性或`Length`属性来确定数组中的对象数。</span><span class="sxs-lookup"><span data-stu-id="bff12-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="bff12-117">例如：</span><span class="sxs-lookup"><span data-stu-id="bff12-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="bff12-118">自定义类型的文件</span><span class="sxs-lookup"><span data-stu-id="bff12-118">Custom Types Files</span></span>

<span data-ttu-id="bff12-119">若要创建自定义类型文件，请首先复制现有类型文件。</span><span class="sxs-lookup"><span data-stu-id="bff12-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="bff12-120">新的文件可以具有任何名称，但是它必须具有.ps1xml 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="bff12-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="bff12-121">将文件复制，你可以在 Windows PowerShell 中，可以访问任何目录中放置新文件，但可用于将文件放在 Windows PowerShell 安装目录 (`$pshome`) 或安装目录的子目录中。</span><span class="sxs-lookup"><span data-stu-id="bff12-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="bff12-122">若要将你自己的扩展的类型添加到该文件，添加你想要扩展的每个对象的类型元素。</span><span class="sxs-lookup"><span data-stu-id="bff12-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="bff12-123">以下主题提供的示例。</span><span class="sxs-lookup"><span data-stu-id="bff12-123">The following topics provide examples.</span></span>

- <span data-ttu-id="bff12-124">有关添加属性和属性集的详细信息，请参阅[扩展属性](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="bff12-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="bff12-125">有关添加方法的详细信息，请参阅[扩展方法](./defining-default-methods-for-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="bff12-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="bff12-126">有关添加成员集的详细信息，请参阅[扩展成员设置](./defining-default-member-sets-for-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="bff12-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="bff12-127">定义你自己的扩展的类型后，使用以下方法之一使扩展的对象可用：</span><span class="sxs-lookup"><span data-stu-id="bff12-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="bff12-128">若要使你扩展的类型的文件可用于当前会话，请使用[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet 以添加新文件。</span><span class="sxs-lookup"><span data-stu-id="bff12-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="bff12-129">如果希望在类型中定义的类型的优先级高于其他类型文件 （包括 Types.ps1xml 文件），请使用`PrependData`的参数[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bff12-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="bff12-130">若要使你扩展的类型的文件可用于所有将来的会话，将类型文件添加到模块、 导出当前会话中，或添加[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData)命令到 Windows PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="bff12-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="bff12-131">对类型文件进行签名</span><span class="sxs-lookup"><span data-stu-id="bff12-131">Signing Types Files</span></span>

<span data-ttu-id="bff12-132">类型的文件应进行数字签名以防止篡改因为 XML 可以包括脚本块。</span><span class="sxs-lookup"><span data-stu-id="bff12-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="bff12-133">有关添加数字签名的详细信息，请参阅[about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="bff12-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="bff12-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bff12-134">See Also</span></span>

[<span data-ttu-id="bff12-135">为对象定义默认属性</span><span class="sxs-lookup"><span data-stu-id="bff12-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="bff12-136">为对象定义的默认方法</span><span class="sxs-lookup"><span data-stu-id="bff12-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="bff12-137">为对象定义默认成员集</span><span class="sxs-lookup"><span data-stu-id="bff12-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="bff12-138">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bff12-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
