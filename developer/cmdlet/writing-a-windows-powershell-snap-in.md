---
title: 编写一个 Windows PowerShell 管理单元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: d4f57c062fee09e85c290445082be745ab229985
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795022"
---
# <a name="writing-a-windows-powershell-snap-in"></a>编写 Windows PowerShell 管理单元

此示例演示如何编写 Windows PowerShell 管理单元，可用于注册的程序集中的所有 cmdlet 和 Windows PowerShell 提供程序。

使用此类型的管理单元中，不选择哪些 cmdlet 和你想要注册的提供程序。 若要编写允许你选择什么注册管理单元，请参阅[编写一个自定义 Windows PowerShell 管理单元](./writing-a-custom-windows-powershell-snap-in.md)。

### <a name="writing-a-windows-powershell-snap-in"></a>编写 Windows PowerShell 管理单元

1. 添加 RunInstallerAttribute 属性。

2. 创建一个公共类派生自[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)类。

    在此示例中，类名称为"GetProcPSSnapIn01"。

3. 添加的 （必需） 管理单元中的名称的公共属性。 当命名单元时，请不要使用任何以下字符: #。 , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    在此示例中，管理单元的名称为"GetProcPSSnapIn01"。

4. （必需） 管理单元中的供应商添加的公共属性。

    在此示例中，供应商为"Microsoft"。

5. 添加管理单元 （可选） 的供应商资源的公共属性。

    在此示例中，供应商资源是"GetProcPSSnapIn01，Microsoft"。

6. 添加一个公共属性 （必需） 管理单元中的说明。

    在此示例中，描述是"这是 Windows PowerShell 管理单元注册 get-proc cmdlet"。

7. 添加管理单元的 （可选） 说明资源的公共属性。

    在此示例中，供应商资源是"GetProcPSSnapIn01，这是 Windows PowerShell 管理单元注册 get-proc cmdlet"。

## <a name="example"></a>示例

此示例演示如何编写 Windows PowerShell 管理单元，可用于在 Windows PowerShell shell 中注册 Get-proc cmdlet。 请注意，在此示例中，完整的程序集将包含仅 GetProcPSSnapIn01 管理单元中类和 Get-proc cmdlet 类。

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a>另请参阅

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
