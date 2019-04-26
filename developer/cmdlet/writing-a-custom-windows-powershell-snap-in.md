---
title: 编写一个自定义 Windows PowerShell 管理单元 |Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067019"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="6f9a7-102">编写自定义 Windows PowerShell 管理单元</span><span class="sxs-lookup"><span data-stu-id="6f9a7-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="6f9a7-103">此示例演示如何编写 Windows PowerShell 管理单元中注册特定的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="6f9a7-104">使用此类型的管理单元中，可以指定哪些 cmdlet、 提供程序、 类型或格式进行注册。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="6f9a7-105">有关如何编写在程序集中注册所有 cmdlet 和提供程序管理单元的详细信息，请参阅[编写一个 Windows PowerShell 管理单元](./writing-a-windows-powershell-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="6f9a7-106">若要编写 Windows PowerShell 管理单元中注册特定的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="6f9a7-107">添加 RunInstallerAttribute 属性。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="6f9a7-108">创建一个公共类派生自[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)类。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="6f9a7-109">在此示例中，类名称为"CustomPSSnapinTest"。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="6f9a7-110">添加的 （必需） 管理单元中的名称的公共属性。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="6f9a7-111">当命名单元时，请不要使用任何以下字符: #。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="6f9a7-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="6f9a7-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="6f9a7-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="6f9a7-113">@ \` \*</span></span>

   <span data-ttu-id="6f9a7-114">在此示例中，管理单元的名称为"CustomPSSnapInTest"。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="6f9a7-115">（必需） 管理单元中的供应商添加的公共属性。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="6f9a7-116">在此示例中，供应商为"Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="6f9a7-117">添加管理单元 （可选） 的供应商资源的公共属性。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="6f9a7-118">在此示例中，供应商资源是"CustomPSSnapInTest，Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="6f9a7-119">添加一个公共属性 （必需） 管理单元中的说明。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="6f9a7-120">在此示例中，说明是："这是自定义 Windows PowerShell 管理单元，包括测试 HelloWorld 和测试 CustomSnapinTest cmdlet 值"。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="6f9a7-121">添加管理单元的 （可选） 说明资源的公共属性。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="6f9a7-122">在此示例中，供应商资源是"CustomPSSnapInTest，这是自定义 Windows PowerShell 管理单元，包括测试 HelloWorld 和测试 CustomSnapinTest cmdlet"。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="6f9a7-123">指定属于自定义管理单元中 （可选） 使用的 cmdlet [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry)类。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="6f9a7-124">在此处添加的信息包括 cmdlet、 其.NET 类型和 （cmdlet 帮助文件名称的格式应为 name.dll help.xml） 的 cmdlet 帮助文件名称的名称。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="6f9a7-125">此示例将添加的测试 HelloWorld 和 TestCustomSnapinTest cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="6f9a7-126">指定属于自定义的管理单元 （可选） 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="6f9a7-127">此示例未指定任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="6f9a7-128">指定属于自定义的管理单元 （可选） 的类型。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="6f9a7-129">此示例中未指定任何类型。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="6f9a7-130">指定属于自定义的管理单元 （可选） 的格式。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="6f9a7-131">此示例未指定任何格式。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="6f9a7-132">示例</span><span class="sxs-lookup"><span data-stu-id="6f9a7-132">Example</span></span>

<span data-ttu-id="6f9a7-133">此示例演示如何编写自定义 Windows PowerShell 管理单元可以用来注册该测试 HelloWorld 和测试 CustomSnapinTest cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="6f9a7-134">请注意，在此示例中，完整的程序集可能包含其他 cmdlet 和提供程序不会通过此管理单元中注册的。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="6f9a7-135">有关注册管理单元的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)中[Windows PowerShell 程序员指南](../prog-guide/windows-powershell-programmer-s-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="6f9a7-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f9a7-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f9a7-136">See Also</span></span>

[<span data-ttu-id="6f9a7-137">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="6f9a7-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="6f9a7-138">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="6f9a7-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
