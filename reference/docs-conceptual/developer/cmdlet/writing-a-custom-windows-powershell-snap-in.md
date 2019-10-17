---
title: 编写自定义 Windows PowerShell 管理单元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364246"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>编写自定义 Windows PowerShell 管理单元

此示例演示如何编写用于注册特定 cmdlet 的 Windows PowerShell 管理单元。

利用这种类型的管理单元，你可以指定要注册的 cmdlet、提供程序、类型或格式。 有关如何编写用于在程序集中注册所有 cmdlet 和提供程序的管理单元的详细信息，请参阅[编写 Windows PowerShell 管理单元](./writing-a-windows-powershell-snap-in.md)。

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>编写用于注册特定 cmdlet 的 Windows PowerShell 管理单元。

1. 添加 RunInstallerAttribute 特性。

2. 创建一个派生自[Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)类的公共类。

   在此示例中，类名为 "CustomPSSnapinTest"。

3. 为管理单元的名称添加一个公共属性（必需）。 命名管理单元时，请不要使用以下任何字符： #。 ，（） {} [] &-/\ $;： "" \< > &#124; ？ @ ` *

   在此示例中，管理单元的名称为 "CustomPSSnapInTest"。

4. 添加管理单元供应商的公共属性（必需）。

   在此示例中，供应商为 "Microsoft"。

5. 添加管理单元的供应商资源的公共属性（可选）。

   在此示例中，供应商资源为 "CustomPSSnapInTest，Microsoft"。

6. 添加管理单元说明的公共属性（必需）。

   在此示例中，说明为： "这是包含 HelloWorld 和 CustomSnapinTest cmdlet 的自定义 Windows PowerShell 管理单元"。

7. 为管理单元的 "说明" 资源添加公共属性（可选）。

   在此示例中，供应商资源为 "CustomPSSnapInTest"，这是一个自定义的 Windows PowerShell 管理单元，其中包括 HelloWorld 和 CustomSnapinTest cmdlet。

8. 使用[Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry)类指定属于 "自定义管理单元" （可选）的 cmdlet （可选）。 此处添加的信息包括该 cmdlet 的名称、其 .NET 类型和 cmdlet 帮助文件名（cmdlet 帮助文件名的格式应为 dll-help）。

   此示例将添加 HelloWorld 和 TestCustomSnapinTest cmdlet。

9. 指定属于自定义管理单元的提供程序（可选）。

   此示例未指定任何提供程序。

10. 指定属于自定义管理单元的类型（可选）。

    此示例未指定任何类型。

11. 指定属于自定义管理单元的格式（可选）。

    此示例未指定任何格式。

## <a name="example"></a>示例

此示例演示如何编写可用于注册 HelloWorld 和 CustomSnapinTest cmdlet 的自定义 Windows PowerShell 管理单元。 请注意，在此示例中，完整的程序集可能包含不会由此管理单元注册的其他 cmdlet 和提供程序。

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

有关注册管理单元的详细信息，请参阅[Windows PowerShell 程序员指南](../prog-guide/windows-powershell-programmer-s-guide.md)中的[如何注册 Cmdlet、提供程序和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="see-also"></a>另请参阅

[如何注册 Cmdlet、提供程序和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
