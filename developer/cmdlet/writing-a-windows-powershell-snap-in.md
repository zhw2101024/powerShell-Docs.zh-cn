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
ms.openlocfilehash: ee8a6538fa6ad4d0f480f2dac46fe0f823a38be8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853763"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="5fbff-102">编写 Windows PowerShell 管理单元</span><span class="sxs-lookup"><span data-stu-id="5fbff-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="5fbff-103">此示例演示如何编写 Windows PowerShell 管理单元，可用于注册的程序集中的所有 cmdlet 和 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="5fbff-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="5fbff-104">使用此类型的管理单元中，不选择哪些 cmdlet 和你想要注册的提供程序。</span><span class="sxs-lookup"><span data-stu-id="5fbff-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="5fbff-105">若要编写允许你选择什么注册管理单元，请参阅[编写一个自定义 Windows PowerShell 管理单元](./writing-a-custom-windows-powershell-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="5fbff-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="5fbff-106">编写 Windows PowerShell 管理单元</span><span class="sxs-lookup"><span data-stu-id="5fbff-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="5fbff-107">添加 RunInstallerAttribute 属性。</span><span class="sxs-lookup"><span data-stu-id="5fbff-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="5fbff-108">创建一个公共类派生自[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)类。</span><span class="sxs-lookup"><span data-stu-id="5fbff-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="5fbff-109">在此示例中，类名称为"GetProcPSSnapIn01"。</span><span class="sxs-lookup"><span data-stu-id="5fbff-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="5fbff-110">添加的 （必需） 管理单元中的名称的公共属性。</span><span class="sxs-lookup"><span data-stu-id="5fbff-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="5fbff-111">当命名单元时，请不要使用任何以下字符: #。</span><span class="sxs-lookup"><span data-stu-id="5fbff-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="5fbff-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="5fbff-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="5fbff-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="5fbff-113">@ \` \*</span></span>

    <span data-ttu-id="5fbff-114">在此示例中，管理单元的名称为"GetProcPSSnapIn01"。</span><span class="sxs-lookup"><span data-stu-id="5fbff-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="5fbff-115">（必需） 管理单元中的供应商添加的公共属性。</span><span class="sxs-lookup"><span data-stu-id="5fbff-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="5fbff-116">在此示例中，供应商为"Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="5fbff-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="5fbff-117">添加管理单元 （可选） 的供应商资源的公共属性。</span><span class="sxs-lookup"><span data-stu-id="5fbff-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="5fbff-118">在此示例中，供应商资源是"GetProcPSSnapIn01，Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="5fbff-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="5fbff-119">添加一个公共属性 （必需） 管理单元中的说明。</span><span class="sxs-lookup"><span data-stu-id="5fbff-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="5fbff-120">在此示例中，描述是"这是 Windows PowerShell 管理单元注册 get-proc cmdlet"。</span><span class="sxs-lookup"><span data-stu-id="5fbff-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="5fbff-121">添加管理单元的 （可选） 说明资源的公共属性。</span><span class="sxs-lookup"><span data-stu-id="5fbff-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="5fbff-122">在此示例中，供应商资源是"GetProcPSSnapIn01，这是 Windows PowerShell 管理单元注册 get-proc cmdlet"。</span><span class="sxs-lookup"><span data-stu-id="5fbff-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="5fbff-123">示例</span><span class="sxs-lookup"><span data-stu-id="5fbff-123">Example</span></span>

<span data-ttu-id="5fbff-124">此示例演示如何编写 Windows PowerShell 管理单元，可用于在 Windows PowerShell shell 中注册 Get-proc cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5fbff-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="5fbff-125">请注意，在此示例中，完整的程序集将包含仅 GetProcPSSnapIn01 管理单元中类和 Get-proc cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="5fbff-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5fbff-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5fbff-126">See Also</span></span>

[<span data-ttu-id="5fbff-127">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="5fbff-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="5fbff-128">如何注册 Cmdlet、 提供程序，和托管应用程序</span><span class="sxs-lookup"><span data-stu-id="5fbff-128">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="5fbff-129">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="5fbff-129">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
