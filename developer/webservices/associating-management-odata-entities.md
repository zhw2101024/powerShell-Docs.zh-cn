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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860823"
---
# <a name="associating-management-odata-entities"></a>关联管理 OData 实体

通常它可用于创建两个不同的管理 OData 实体之间的关联。 例如，管理 OData 服务可能具有管理产品按类别进行组织的目录的实体和定义实体`Product`和`Category`。 通过将这两个实体相关联，则客户端可以对 web 服务的单个请求与某个类别中获得有关的所有产品的信息。

可以在下载此示例展示了如何创建实体之间的关联[关联示例](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)。

## <a name="creating-the-association-in-the-resource-schema-file"></a>在资源架构文件中创建关联

以下 MOF 定义两个实体。 我们将创建它们之间的关联。

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

`Category`类定义的属性，则属于该类别的产品名称的数组。

若要将两个实体相关联，必须定义与类`Association`服务的资源架构 MOF 文件中的属性。 类必须定义两个实体相关联，名为`ends`的关联。 下面的示例演示一个定义类别和产品实体之间的关联类的定义。

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

此外必须更改类别类中的 Products 属性的声明。 您使用`AssociationClass`关键字来指定该属性是关联的一端。 属性还必须定义为一个单独的实体，而不是一个字符串数组的引用。 执行此操作通过使用`ref`关键字。 下面的示例显示了关联的属性定义。

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

最后，必须通过添加到属性定义声明关联另一端`Product`类。 这是数组或单个实体的引用。 假定每个产品属于只有一个类别，定义将如下所示。

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

表示关联的两个端点的属性称为导航属性。

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>用于将资源架构文件中的实体相关联的步骤

- 通过使用作为类定义的关联`Association`关键字。

- 使用关联类关键字来限定关联的实体的属性定义的关联端。

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>资源映射 XML 文件中创建关联

有三个不同的情况下，要考虑映射资源映射 XML 文件中的关联时。

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>确定如何将资源映射文件中的实体相关联

- 如果导航属性中不存在的基础。 .NET framework 类型和属性包含外键，没有显式映射是必需的。

- 如果基础的.NET Framework 类型中不存在的导航属性，则必须指定一个 cmdlet 检索的键关联的实例的列表。 执行此操作通过添加`Association`元素下嵌套`CmdletImplementation`元素中，以下定义的元素`cmdlets`对于其他 CRUD 命令。

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

- 如果导航属性中的基础的.NET Framework 类型，存在，但它包含对象实例，而不是外键，则必须创建一个 cmdlet （通过编写 Windows PowerShell 函数或脚本） 来检索的外键。 然后资源映射文件中指定该 cmdlet。 例如，要检索的密钥的脚本将如下所示。

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  和资源映射文件中的 XML 将如下所示。

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

- 除了指定用于检索关联的实体的 cmdlet，还可以指定用于添加和删除引用集合中的 cmdlet。 下面的示例假定存在 ProductToCategory 添加和删除 ProductFromCategory cmdlet （它们也可以定义脚本或函数与前面的示例中）。

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

## <a name="querying-associated-entities"></a>查询关联的实体

客户端可以检索通过创建特定的查询来与实体相关联的实例的列表。

#### <a name="constructing-queries-for-associated-entities"></a>构造关联的实体的查询

- 客户端可以请求类别的详细信息，而无需检索其关联的产品。 例如，以下请求将获取的详细信息`food`类别。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  若要获取的类别的相关联的产品 （但未类别本身，而客户端的详细信息的请求中指定的导航属性。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- 若要检索的产品的 Url，请使用`$links`请求中的限定符。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- 客户端可以通过获取类别详细信息和其关联的产品`$expand`限定符。

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>另请参阅

[创建管理 OData IIS 扩展 Web 服务](./creating-a-management-odata-web-service.md)