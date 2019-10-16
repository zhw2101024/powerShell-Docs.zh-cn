---
title: 关联管理 OData 实体 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359806"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="f5236-102">关联管理 OData 实体</span><span class="sxs-lookup"><span data-stu-id="f5236-102">Associating Management OData Entities</span></span>

<span data-ttu-id="f5236-103">在两个不同的管理 OData 实体之间创建关联通常是很有用的。</span><span class="sxs-lookup"><span data-stu-id="f5236-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="f5236-104">例如，管理 OData 服务可以具有管理类别中组织的产品目录的实体，并定义 `Product` 和 `Category` 的实体。</span><span class="sxs-lookup"><span data-stu-id="f5236-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="f5236-105">通过将这两个实体关联，客户端可以获取类别中所有产品的相关信息，其中包含对 web 服务的单个请求。</span><span class="sxs-lookup"><span data-stu-id="f5236-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="f5236-106">一个示例，演示如何在[关联示例](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)中下载实体之间的关联。</span><span class="sxs-lookup"><span data-stu-id="f5236-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="f5236-107">在资源架构文件中创建关联</span><span class="sxs-lookup"><span data-stu-id="f5236-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="f5236-108">以下 MOF 定义了两个实体。</span><span class="sxs-lookup"><span data-stu-id="f5236-108">The following MOF defines two entities.</span></span> <span data-ttu-id="f5236-109">我们将在它们之间创建关联。</span><span class="sxs-lookup"><span data-stu-id="f5236-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="f5236-110">@No__t-0 类定义一个属性，该属性是属于该类别的产品的名称数组。</span><span class="sxs-lookup"><span data-stu-id="f5236-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="f5236-111">若要关联两个实体，必须使用服务的资源架构 MOF 文件中的 `Association` 特性来定义类。</span><span class="sxs-lookup"><span data-stu-id="f5236-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="f5236-112">类必须定义要关联的两个实体，称为关联的 @no__t 0。</span><span class="sxs-lookup"><span data-stu-id="f5236-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="f5236-113">下面的示例演示定义类别和产品实体之间的关联的类的定义。</span><span class="sxs-lookup"><span data-stu-id="f5236-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="f5236-114">还必须在 Category 类中更改 Products 属性的声明。</span><span class="sxs-lookup"><span data-stu-id="f5236-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="f5236-115">使用 @no__t 关键字来指定属性是关联的一端。</span><span class="sxs-lookup"><span data-stu-id="f5236-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="f5236-116">还必须将属性定义为对单独实体的引用，而不是定义为字符串数组。</span><span class="sxs-lookup"><span data-stu-id="f5236-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="f5236-117">为此，请使用 @no__t 关键字。</span><span class="sxs-lookup"><span data-stu-id="f5236-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="f5236-118">下面的示例演示关联的属性定义。</span><span class="sxs-lookup"><span data-stu-id="f5236-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="f5236-119">最后，必须通过将属性定义添加到 `Product` 类来声明关联的另一端。</span><span class="sxs-lookup"><span data-stu-id="f5236-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="f5236-120">这是对数组或单个实体的引用。</span><span class="sxs-lookup"><span data-stu-id="f5236-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="f5236-121">假设每个产品仅属于一个类别，定义如下所示。</span><span class="sxs-lookup"><span data-stu-id="f5236-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="f5236-122">表示关联的两个端的属性称为导航属性。</span><span class="sxs-lookup"><span data-stu-id="f5236-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="f5236-123">关联资源架构文件中的实体的步骤</span><span class="sxs-lookup"><span data-stu-id="f5236-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="f5236-124">使用 @no__t 关键字将关联定义为类。</span><span class="sxs-lookup"><span data-stu-id="f5236-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="f5236-125">通过使用 AssociationClass 关键字限定关联实体的属性，定义关联的两端。</span><span class="sxs-lookup"><span data-stu-id="f5236-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="f5236-126">在资源映射 XML 文件中创建关联</span><span class="sxs-lookup"><span data-stu-id="f5236-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="f5236-127">在资源映射 XML 文件中映射关联时，需要考虑三个不同的情况。</span><span class="sxs-lookup"><span data-stu-id="f5236-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="f5236-128">确定如何关联资源映射文件中的实体</span><span class="sxs-lookup"><span data-stu-id="f5236-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="f5236-129">如果导航属性存在于基础中，则为。</span><span class="sxs-lookup"><span data-stu-id="f5236-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="f5236-130">.NET Framework 类型，并且该属性包含外键，则无需显式映射。</span><span class="sxs-lookup"><span data-stu-id="f5236-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="f5236-131">如果基础 .NET Framework 类型中不存在导航属性，则必须指定一个 cmdlet 来检索关联实例的密钥列表。</span><span class="sxs-lookup"><span data-stu-id="f5236-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="f5236-132">要执行此操作，可将嵌套在 `CmdletImplementation` 元素下的 @no__t 0 元素添加到为其他 CRUD 命令定义 `cmdlets` 的元素之后。</span><span class="sxs-lookup"><span data-stu-id="f5236-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="f5236-133">如果导航属性存在于基础 .NET Framework 类型中，但它包含对象实例而不是外键，则必须创建一个 cmdlet （通过编写 Windows PowerShell 函数或脚本）来检索外键。</span><span class="sxs-lookup"><span data-stu-id="f5236-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="f5236-134">然后，在资源映射文件中指定该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f5236-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="f5236-135">例如，用于检索密钥的脚本将如下所示。</span><span class="sxs-lookup"><span data-stu-id="f5236-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="f5236-136">资源映射文件中的 XML 如下所示。</span><span class="sxs-lookup"><span data-stu-id="f5236-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="f5236-137">除了指定 cmdlet 来检索关联的实体以外，还可以指定 cmdlet 来添加和删除集合中的引用。</span><span class="sxs-lookup"><span data-stu-id="f5236-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="f5236-138">下面的示例假定 ProductToCategory 和 ProductFromCategory cmdlet 存在（也可以在脚本或函数中定义，如前面的示例所示）。</span><span class="sxs-lookup"><span data-stu-id="f5236-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="f5236-139">查询关联实体</span><span class="sxs-lookup"><span data-stu-id="f5236-139">Querying associated entities</span></span>

<span data-ttu-id="f5236-140">客户端可以通过创建特定查询来检索与实体关联的实例的列表。</span><span class="sxs-lookup"><span data-stu-id="f5236-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="f5236-141">构造关联实体的查询</span><span class="sxs-lookup"><span data-stu-id="f5236-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="f5236-142">客户端可以请求类别的详细信息，而无需检索其关联的产品。</span><span class="sxs-lookup"><span data-stu-id="f5236-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="f5236-143">例如，以下请求将获取 @no__t 类别的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f5236-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="f5236-144">若要获取类别的关联产品（但不是类别自身的详细信息），客户端将在请求中指定导航属性。</span><span class="sxs-lookup"><span data-stu-id="f5236-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="f5236-145">若要仅检索产品的 Url，请在请求中使用 `$links` 限定符。</span><span class="sxs-lookup"><span data-stu-id="f5236-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="f5236-146">客户端可以通过使用 `$expand` 限定符获取类别详细信息及其关联的产品。</span><span class="sxs-lookup"><span data-stu-id="f5236-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="f5236-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5236-147">See Also</span></span>

[<span data-ttu-id="f5236-148">创建管理 OData IIS 扩展 Web 服务</span><span class="sxs-lookup"><span data-stu-id="f5236-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)