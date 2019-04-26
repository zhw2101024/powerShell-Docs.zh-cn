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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068158"
---
# <a name="extending-output-objects"></a>扩展输出对象

您可以扩展的.NET Framework 对象使用的类型文件 (.ps1xml) 返回的 cmdlet、 函数和脚本。 类型文件是基于 XML 的文件，可将属性和方法添加到现有对象。 例如，Windows PowerShell 提供了将元素添加到多个现有的.NET Framework 对象的 Types.ps1xml 文件。 Types.ps1xml 文件位于 Windows PowerShell 安装目录 (`$pshome`)。 可以创建自己的类型文件来进一步扩展这些对象或将扩展的其他对象。 时使用的类型文件扩展对象，该对象的任何实例进行扩展的新元素。

## <a name="extending-the-systemarray-object"></a>扩展 System.Array 对象

下面的示例演示如何扩展 Windows PowerShell [System.Array](/dotnet/api/System.Array) Types.ps1xml 文件中的对象。 默认情况下[System.Array](/dotnet/api/System.Array)对象具有`Length`列出的数组中对象的属性。 但是，由于名称"长度"不清楚地描述该属性，因此 Windows PowerShell 添加`Count`别名属性，其中显示了相同的值`Length`属性。 下面的 XML 将添加`Count`属性设置为[System.Array](/dotnet/api/System.Array)类型。

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

若要查看这个新的别名属性，请使用[Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)命令任何阵列上，在下面的示例所示。

```powershell
Get-Member -InputObject (1,2,3,4)
```

该命令返回以下结果。
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
你可以使用`Count`属性或`Length`属性来确定数组中的对象数。 例如：

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

## <a name="custom-types-files"></a>自定义类型的文件

若要创建自定义类型文件，请首先复制现有类型文件。 新的文件可以具有任何名称，但是它必须具有.ps1xml 文件扩展名。 将文件复制，你可以在 Windows PowerShell 中，可以访问任何目录中放置新文件，但可用于将文件放在 Windows PowerShell 安装目录 (`$pshome`) 或安装目录的子目录中。

若要将你自己的扩展的类型添加到该文件，添加你想要扩展的每个对象的类型元素。 以下主题提供的示例。

- 有关添加属性和属性集的详细信息，请参阅[扩展属性](./extending-properties-for-objects.md)

- 有关添加方法的详细信息，请参阅[扩展方法](./defining-default-methods-for-objects.md)。

- 有关添加成员集的详细信息，请参阅[扩展成员设置](./defining-default-member-sets-for-objects.md)。

定义你自己的扩展的类型后，使用以下方法之一使扩展的对象可用：

- 若要使你扩展的类型的文件可用于当前会话，请使用[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet 以添加新文件。 如果希望在类型中定义的类型的优先级高于其他类型文件 （包括 Types.ps1xml 文件），请使用`PrependData`的参数[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet。
- 若要使你扩展的类型的文件可用于所有将来的会话，将类型文件添加到模块、 导出当前会话中，或添加[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData)命令到 Windows PowerShell 配置文件。

## <a name="signing-types-files"></a>对类型文件进行签名

类型的文件应进行数字签名以防止篡改因为 XML 可以包括脚本块。 有关添加数字签名的详细信息，请参阅[about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>另请参阅

[为对象定义默认属性](./extending-properties-for-objects.md)

[为对象定义的默认方法](./defining-default-methods-for-objects.md)

[为对象定义默认成员集](./defining-default-member-sets-for-objects.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
