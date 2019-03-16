---
title: 公共资源架构 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057240"
---
# <a name="public-resource-schema"></a>公共资源架构

管理 OData 使用 MOF 定义资源和它们的属性。 管理 OData 实体的属性直接对应于基础 cmdlet 返回托管类型的属性。

## <a name="defining-a-resource"></a>定义资源

每个资源对应于 Windows PowerShell cmdlet 返回一个对象。 在公共资源的 MOF 文件中，通过声明一个类来定义资源。 类包含对应于该对象的属性的属性。 例如，在以下示例中， [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)类由以下 MOF。

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

每个属性名称的前面有一种数据类型。 在此示例中的数据类型对应于.NET 框架中的基元 CLR 数据类型，但属性也可以是对其他资源或复杂类型，同时介绍这些更高版本的引用。

`Key`限定符表示属性用于唯一地标识资源实例。 资源可以有多个键。

`Required`限定符表示该属性是必需。 如果属性标记有`Key`限定符，它被视为不必需的并且`Required`限定符不需要。

### <a name="complex-data-types"></a>复杂数据类型

实体的属性可以具有复杂数据类型。 复杂数据类型是由其他类型，类似于 C 编程语言中的结构组成的类型。 复杂类型的 MOF 文件中声明为具有的类`ComplexType`限定符，如以下示例所示。

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

若要声明为复杂类型的实体属性，将其声明为`string`类型具有`EmbeddedInstance`限定符，包括复杂类型的名称。 下面的示例演示的属性声明`PswsTest_ProcessModule`上一示例中声明的类型。

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>将实体相关联

可以使用关联和关联类限定符将关联的两个实体。 有关详细信息，请参阅[相关联的管理 OData 实体](./associating-management-odata-entities.md)。

### <a name="derived-types"></a>派生的类型

可以从另一种类型派生类型。 派生的类型继承了所有衍生它除了显式派生的任何属性的类型的属性。 下面的示例演示类型声明，然后从该类型派生的两种类型的声明。

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```