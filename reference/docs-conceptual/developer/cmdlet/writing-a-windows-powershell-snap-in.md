---
title: 编写 Windows PowerShell 管理单元 |Microsoft Docs
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
ms.openlocfilehash: d12a66e354a23041fffb0f8fa286c849849ec2b0
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870466"
---
# <a name="writing-a-windows-powershell-snap-in"></a>编写 Windows PowerShell 管理单元

此示例演示如何编写可用于在程序集中注册所有 cmdlet 和 Windows PowerShell 提供程序的 Windows PowerShell 管理单元。

对于这种类型的管理单元，不选择要注册的 cmdlet 和提供程序。 若要编写允许您选择注册内容的管理单元，请参阅[编写自定义 Windows PowerShell 管理单元](./writing-a-custom-windows-powershell-snap-in.md)。

### <a name="writing-a-windows-powershell-snap-in"></a>编写 Windows PowerShell 管理单元

1. 添加 RunInstallerAttribute 特性。

2. 创建一个派生自[add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)类的公共类。

    在此示例中，类名为 "GetProcPSSnapIn01"。

3. 为管理单元的名称添加一个公共属性（必需）。 命名管理单元时，请不要使用以下任何字符： `#`、`.`、`,`、`(`、`)`、`{`、`}`、`[`、`]`、`&`、`-`、`/`、`\`、`$`、`;`、`:`、`"`、`'`、`<`、`>`、`|`

    在此示例中，管理单元的名称为 "GetProcPSSnapIn01"。

4. 添加管理单元供应商的公共属性（必需）。

    在此示例中，供应商为 "Microsoft"。

5. 添加管理单元的供应商资源的公共属性（可选）。

    在此示例中，供应商资源为 "GetProcPSSnapIn01，Microsoft"。

6. 添加管理单元说明的公共属性（必需）。

    在此示例中，说明为 "这是一个用于注册 get-help cmdlet 的 Windows PowerShell 管理单元"。

7. 为管理单元的 "说明" 资源添加公共属性（可选）。

    在此示例中，供应商资源为 "GetProcPSSnapIn01，这是一个用于注册 get-help cmdlet 的 Windows PowerShell 管理单元"。

## <a name="example"></a>示例

此示例演示如何编写可用于在 Windows PowerShell shell 中注册 Get-help cmdlet 的 Windows PowerShell 管理单元。 请注意，在此示例中，完整的程序集只包含 GetProcPSSnapIn01 管理单元类和 `Get-Proc` cmdlet 类。

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

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
