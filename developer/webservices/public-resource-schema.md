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
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859543"
---
# <a name="public-resource-schema"></a><span data-ttu-id="b3e3d-102">公共资源架构</span><span class="sxs-lookup"><span data-stu-id="b3e3d-102">Public Resource Schema</span></span>

<span data-ttu-id="b3e3d-103">管理 OData 使用 MOF 定义资源和它们的属性。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="b3e3d-104">管理 OData 实体的属性直接对应于基础 cmdlet 返回托管类型的属性。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="b3e3d-105">定义资源</span><span class="sxs-lookup"><span data-stu-id="b3e3d-105">Defining a resource</span></span>

<span data-ttu-id="b3e3d-106">每个资源对应于 Windows PowerShell cmdlet 返回一个对象。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="b3e3d-107">在 publc 资源 MOF 文件中，通过声明一个类来定义资源。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-107">In the publc resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="b3e3d-108">类包含对应于该对象的属性的属性。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="b3e3d-109">例如，在以下示例中， [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)类由以下 MOF。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="b3e3d-110">每个属性名称的前面有一种数据类型。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="b3e3d-111">在此示例中的数据类型对应于.NET 框架中的基元 CLR 数据类型，但属性也可以是对其他资源或复杂类型，同时介绍这些更高版本的引用。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="b3e3d-112">`Key`限定符表示属性用于唯一地标识资源实例。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="b3e3d-113">资源可以有多个键。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-113">A resource can have more than one key.</span></span>

<span data-ttu-id="b3e3d-114">`Required`限定符表示该属性是必需。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="b3e3d-115">如果属性标记有`Key`限定符，它被视为不必需的并且`Required`限定符不需要。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="b3e3d-116">复杂数据类型</span><span class="sxs-lookup"><span data-stu-id="b3e3d-116">Complex data types</span></span>

<span data-ttu-id="b3e3d-117">实体的属性可以具有复杂数据类型。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="b3e3d-118">复杂数据类型是由其他类型，类似于 C 编程语言中的结构组成的类型。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="b3e3d-119">复杂类型的 MOF 文件中声明为具有的类`ComplexType`限定符，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="b3e3d-120">若要声明为复杂类型的实体属性，将其声明为`string`类型具有`EmbeddedInstance`限定符，包括复杂类型的名称。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="b3e3d-121">以下示例 hshows 属性声明的`PswsTest_ProcessModule`上一示例中声明的类型。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-121">The following example hshows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="b3e3d-122">将实体相关联</span><span class="sxs-lookup"><span data-stu-id="b3e3d-122">Associating entities</span></span>

<span data-ttu-id="b3e3d-123">可以使用关联和 AssocationClass 限定符将关联的两个实体。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-123">You can associate two entities by using the Association and AssocationClass qualifiers.</span></span> <span data-ttu-id="b3e3d-124">有关详细信息，请参阅[相关联的管理 OData 实体](./associating-management-odata-entities.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="b3e3d-125">派生的类型</span><span class="sxs-lookup"><span data-stu-id="b3e3d-125">Derived types</span></span>

<span data-ttu-id="b3e3d-126">可以从另一种类型派生类型。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-126">You can derive a type from another type.</span></span> <span data-ttu-id="b3e3d-127">派生的类型继承了所有衍生它除了显式派生的任何属性的类型的属性。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="b3e3d-128">下面的示例演示类型声明，然后从该类型派生的两种类型的声明。</span><span class="sxs-lookup"><span data-stu-id="b3e3d-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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