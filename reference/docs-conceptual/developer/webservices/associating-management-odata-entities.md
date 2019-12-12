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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359806"
---
# <a name="associating-management-odata-entities"></a>关联管理 OData 实体

在两个不同的管理 OData 实体之间创建关联通常是很有用的。 例如，管理 OData 服务可以具有管理类别中组织的产品目录的实体，并 `Product` 和 `Category`定义实体。 通过将这两个实体关联，客户端可以获取类别中所有产品的相关信息，其中包含对 web 服务的单个请求。

一个示例，演示如何在[关联示例](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)中下载实体之间的关联。

## <a name="creating-the-association-in-the-resource-schema-file"></a>在资源架构文件中创建关联

以下 MOF 定义了两个实体。 我们将在它们之间创建关联。

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

`Category` 类定义一个属性，该属性是属于该类别的产品的名称数组。

若要关联两个实体，必须使用服务的资源架构 MOF 文件中的 `Association` 特性来定义类。 类必须定义要关联的两个实体，称为关联的 `ends`。 下面的示例演示定义类别和产品实体之间的关联的类的定义。

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

还必须在 Category 类中更改 Products 属性的声明。 使用 `AssociationClass` 关键字指定属性是关联的一端。 还必须将属性定义为对单独实体的引用，而不是定义为字符串数组。 可以通过使用 `ref` 关键字实现此目的。 下面的示例演示关联的属性定义。

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

最后，必须通过将属性定义添加到 `Product` 类来声明关联的另一端。 这是对数组或单个实体的引用。 假设每个产品仅属于一个类别，定义如下所示。

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

表示关联的两个端的属性称为导航属性。

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>关联资源架构文件中的实体的步骤

- 使用 `Association` 关键字将关联定义为类。

- 通过使用 AssociationClass 关键字限定关联实体的属性，定义关联的两端。

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>在资源映射 XML 文件中创建关联

在资源映射 XML 文件中映射关联时，需要考虑三个不同的情况。

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>确定如何关联资源映射文件中的实体

- 如果导航属性存在于基础中，则为。 .NET Framework 类型，并且该属性包含外键，则无需显式映射。

- 如果基础 .NET Framework 类型中不存在导航属性，则必须指定一个 cmdlet 来检索关联实例的密钥列表。 为此，请在定义了其他 CRUD 命令的 `cmdlets` 的元素后面添加嵌套在 `CmdletImplementation` 元素下的 `Association` 元素。

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

- 如果导航属性存在于基础 .NET Framework 类型中，但它包含对象实例而不是外键，则必须创建一个 cmdlet （通过编写 Windows PowerShell 函数或脚本）来检索外键。 然后，在资源映射文件中指定该 cmdlet。 例如，用于检索密钥的脚本将如下所示。

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  资源映射文件中的 XML 如下所示。

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

- 除了指定 cmdlet 来检索关联的实体以外，还可以指定 cmdlet 来添加和删除集合中的引用。 下面的示例假定 ProductToCategory 和 ProductFromCategory cmdlet 存在（也可以在脚本或函数中定义，如前面的示例所示）。

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

## <a name="querying-associated-entities"></a>查询关联实体

客户端可以通过创建特定查询来检索与实体关联的实例的列表。

#### <a name="constructing-queries-for-associated-entities"></a>构造关联实体的查询

- 客户端可以请求类别的详细信息，而无需检索其关联的产品。 例如，以下请求将获取 `food` 类别的详细信息。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  若要获取类别的关联产品（但不是类别自身的详细信息），客户端将在请求中指定导航属性。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- 若要仅检索产品的 Url，请使用请求中的 `$links` 限定符。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- 客户端可以使用 `$expand` 限定符获取类别详细信息及其关联的产品。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>另请参阅

[创建管理 OData IIS 扩展 Web 服务](./creating-a-management-odata-web-service.md)