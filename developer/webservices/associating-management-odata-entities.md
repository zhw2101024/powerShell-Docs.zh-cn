---
title: 将管理 OData 实体相关联 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080741"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="444e9-102">关联管理 OData 实体</span><span class="sxs-lookup"><span data-stu-id="444e9-102">Associating Management OData Entities</span></span>

<span data-ttu-id="444e9-103">通常它可用于创建两个不同的管理 OData 实体之间的关联。</span><span class="sxs-lookup"><span data-stu-id="444e9-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="444e9-104">例如，管理 OData 服务可能具有管理产品按类别进行组织的目录的实体和定义实体`Product`和`Category`。</span><span class="sxs-lookup"><span data-stu-id="444e9-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="444e9-105">通过将这两个实体相关联，则客户端可以对 web 服务的单个请求与某个类别中获得有关的所有产品的信息。</span><span class="sxs-lookup"><span data-stu-id="444e9-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="444e9-106">可以在下载此示例展示了如何创建实体之间的关联[关联示例](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)。</span><span class="sxs-lookup"><span data-stu-id="444e9-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="444e9-107">在资源架构文件中创建关联</span><span class="sxs-lookup"><span data-stu-id="444e9-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="444e9-108">以下 MOF 定义两个实体。</span><span class="sxs-lookup"><span data-stu-id="444e9-108">The following MOF defines two entities.</span></span> <span data-ttu-id="444e9-109">我们将创建它们之间的关联。</span><span class="sxs-lookup"><span data-stu-id="444e9-109">We will create an association between them.</span></span>

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

<span data-ttu-id="444e9-110">`Category`类定义的属性，则属于该类别的产品名称的数组。</span><span class="sxs-lookup"><span data-stu-id="444e9-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="444e9-111">若要将两个实体相关联，必须定义与类`Association`服务的资源架构 MOF 文件中的属性。</span><span class="sxs-lookup"><span data-stu-id="444e9-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="444e9-112">类必须定义两个实体相关联，名为`ends`的关联。</span><span class="sxs-lookup"><span data-stu-id="444e9-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="444e9-113">下面的示例演示一个定义类别和产品实体之间的关联类的定义。</span><span class="sxs-lookup"><span data-stu-id="444e9-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="444e9-114">此外必须更改类别类中的 Products 属性的声明。</span><span class="sxs-lookup"><span data-stu-id="444e9-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="444e9-115">您使用`AssociationClass`关键字来指定该属性是关联的一端。</span><span class="sxs-lookup"><span data-stu-id="444e9-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="444e9-116">属性还必须定义为一个单独的实体，而不是一个字符串数组的引用。</span><span class="sxs-lookup"><span data-stu-id="444e9-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="444e9-117">执行此操作通过使用`ref`关键字。</span><span class="sxs-lookup"><span data-stu-id="444e9-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="444e9-118">下面的示例显示了关联的属性定义。</span><span class="sxs-lookup"><span data-stu-id="444e9-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="444e9-119">最后，必须通过添加到属性定义声明关联另一端`Product`类。</span><span class="sxs-lookup"><span data-stu-id="444e9-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="444e9-120">这是数组或单个实体的引用。</span><span class="sxs-lookup"><span data-stu-id="444e9-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="444e9-121">假定每个产品属于只有一个类别，定义将如下所示。</span><span class="sxs-lookup"><span data-stu-id="444e9-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="444e9-122">表示关联的两个端点的属性称为导航属性。</span><span class="sxs-lookup"><span data-stu-id="444e9-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="444e9-123">用于将资源架构文件中的实体相关联的步骤</span><span class="sxs-lookup"><span data-stu-id="444e9-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="444e9-124">通过使用作为类定义的关联`Association`关键字。</span><span class="sxs-lookup"><span data-stu-id="444e9-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="444e9-125">使用关联类关键字来限定关联的实体的属性定义的关联端。</span><span class="sxs-lookup"><span data-stu-id="444e9-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="444e9-126">资源映射 XML 文件中创建关联</span><span class="sxs-lookup"><span data-stu-id="444e9-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="444e9-127">有三个不同的情况下，要考虑映射资源映射 XML 文件中的关联时。</span><span class="sxs-lookup"><span data-stu-id="444e9-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="444e9-128">确定如何将资源映射文件中的实体相关联</span><span class="sxs-lookup"><span data-stu-id="444e9-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="444e9-129">如果导航属性中不存在的基础。</span><span class="sxs-lookup"><span data-stu-id="444e9-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="444e9-130">.NET framework 类型和属性包含外键，没有显式映射是必需的。</span><span class="sxs-lookup"><span data-stu-id="444e9-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="444e9-131">如果基础的.NET Framework 类型中不存在的导航属性，则必须指定一个 cmdlet 检索的键关联的实例的列表。</span><span class="sxs-lookup"><span data-stu-id="444e9-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="444e9-132">执行此操作通过添加`Association`元素下嵌套`CmdletImplementation`元素中，以下定义的元素`cmdlets`对于其他 CRUD 命令。</span><span class="sxs-lookup"><span data-stu-id="444e9-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="444e9-133">如果导航属性中的基础的.NET Framework 类型，存在，但它包含对象实例，而不是外键，则必须创建一个 cmdlet （通过编写 Windows PowerShell 函数或脚本） 来检索的外键。</span><span class="sxs-lookup"><span data-stu-id="444e9-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="444e9-134">然后资源映射文件中指定该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="444e9-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="444e9-135">例如，要检索的密钥的脚本将如下所示。</span><span class="sxs-lookup"><span data-stu-id="444e9-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="444e9-136">和资源映射文件中的 XML 将如下所示。</span><span class="sxs-lookup"><span data-stu-id="444e9-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="444e9-137">除了指定用于检索关联的实体的 cmdlet，还可以指定用于添加和删除引用集合中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="444e9-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="444e9-138">下面的示例假定存在 ProductToCategory 添加和删除 ProductFromCategory cmdlet （它们也可以定义脚本或函数与前面的示例中）。</span><span class="sxs-lookup"><span data-stu-id="444e9-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="444e9-139">查询关联的实体</span><span class="sxs-lookup"><span data-stu-id="444e9-139">Querying associated entities</span></span>

<span data-ttu-id="444e9-140">客户端可以检索通过创建特定的查询来与实体相关联的实例的列表。</span><span class="sxs-lookup"><span data-stu-id="444e9-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="444e9-141">构造关联的实体的查询</span><span class="sxs-lookup"><span data-stu-id="444e9-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="444e9-142">客户端可以请求类别的详细信息，而无需检索其关联的产品。</span><span class="sxs-lookup"><span data-stu-id="444e9-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="444e9-143">例如，以下请求将获取的详细信息`food`类别。</span><span class="sxs-lookup"><span data-stu-id="444e9-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="444e9-144">若要获取的类别的相关联的产品 （但未类别本身，而客户端的详细信息的请求中指定的导航属性。</span><span class="sxs-lookup"><span data-stu-id="444e9-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="444e9-145">若要检索的产品的 Url，请使用`$links`请求中的限定符。</span><span class="sxs-lookup"><span data-stu-id="444e9-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="444e9-146">客户端可以通过获取类别详细信息和其关联的产品`$expand`限定符。</span><span class="sxs-lookup"><span data-stu-id="444e9-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="444e9-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="444e9-147">See Also</span></span>

[<span data-ttu-id="444e9-148">创建管理 OData IIS 扩展 Web 服务</span><span class="sxs-lookup"><span data-stu-id="444e9-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)