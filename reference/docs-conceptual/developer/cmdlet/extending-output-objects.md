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
# <a name="extending-output-objects"></a>扩展输出对象

你可以使用类型文件（. types.ps1xml）扩展由 cmdlet、函数和脚本返回的 .NET Framework 对象。 类型文件是基于 XML 的文件，可用于向现有对象添加属性和方法。 例如，Windows PowerShell 提供 types.ps1xml 文件，该文件将元素添加到多个现有的 .NET Framework 对象。 Types.ps1xml 文件位于 Windows PowerShell 安装目录（`$pshome`）中。 您可以创建自己的类型文件，以便进一步扩展这些对象或扩展其他对象。 使用类型文件扩展对象时，会使用新元素扩展对象的任何实例。

## <a name="extending-the-systemarray-object"></a>扩展 System.object 对象

下面的示例演示 Windows PowerShell 如何在 types.ps1xml 文件中扩展[system.object](/dotnet/api/System.Array)对象。 默认情况下， [system.object](/dotnet/api/System.Array)对象具有一个 `Length` 属性，该属性列出数组中对象的数量。 但是，由于名称 "length" 未清楚地描述属性，因此 Windows PowerShell 将添加 `Count` alias 属性，该属性与 `Length` 属性显示相同的值。 下面的 XML 将 `Count` 属性添加到[system.object](/dotnet/api/System.Array)类型。

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

若要查看此新的别名属性，请在任何数组上使用[Get 成员](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)命令，如以下示例中所示。

```powershell
Get-Member -InputObject (1,2,3,4)
```

该命令将返回以下结果。
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
您可以使用 `Count` 属性或 `Length` 属性来确定数组中有多少个对象。 例如：

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

## <a name="custom-types-files"></a>自定义类型文件

若要创建自定义类型文件，请首先复制现有的类型文件。 新文件可以具有任何名称，但它必须具有 types.ps1xml 文件扩展名。 复制文件时，您可以将新文件放置在可供 Windows PowerShell 访问的任何目录中，但将这些文件放在 Windows PowerShell 安装目录（`$pshome`）或安装目录的子目录中会很有用。

若要将自己的扩展类型添加到文件中，请为要扩展的每个对象添加类型元素。 以下主题提供了示例。

- 有关添加属性和属性集的详细信息，请参阅[扩展属性](./extending-properties-for-objects.md)

- 有关添加方法的详细信息，请参阅[扩展方法](./defining-default-methods-for-objects.md)。

- 有关添加成员集的详细信息，请参阅[扩展成员集](./defining-default-member-sets-for-objects.md)。

定义自己的扩展类型后，请使用以下方法之一来使扩展对象可用：

- 若要使扩展类型文件可用于当前会话，请使用[update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet 添加新的文件。 如果你希望你的类型优先于其他类型文件（包括 types.ps1xml 文件）中定义的类型，请使用[update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet 的 `PrependData` 参数。
- 若要使扩展类型文件可供所有未来会话使用，请将类型文件添加到模块，导出当前会话，或将[update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData)命令添加到 Windows PowerShell 配置文件。

## <a name="signing-types-files"></a>签名类型文件

应对类型文件进行数字签名以防止篡改，因为 XML 可以包含脚本块。 有关添加数字签名的详细信息，请参阅[about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>另请参阅

[定义对象的默认属性](./extending-properties-for-objects.md)

[定义对象的默认方法](./defining-default-methods-for-objects.md)

[定义对象的默认成员集](./defining-default-member-sets-for-objects.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
