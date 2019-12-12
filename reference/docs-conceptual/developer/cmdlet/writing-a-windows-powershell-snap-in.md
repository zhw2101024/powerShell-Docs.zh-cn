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
ms.openlocfilehash: 465ab9e8fa29716ce0f46ad0dcf01d0ddd615bcd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364226"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="ce446-102">编写 Windows PowerShell 管理单元</span><span class="sxs-lookup"><span data-stu-id="ce446-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="ce446-103">此示例演示如何编写可用于在程序集中注册所有 cmdlet 和 Windows PowerShell 提供程序的 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="ce446-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="ce446-104">对于这种类型的管理单元，不选择要注册的 cmdlet 和提供程序。</span><span class="sxs-lookup"><span data-stu-id="ce446-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="ce446-105">若要编写允许您选择注册内容的管理单元，请参阅[编写自定义 Windows PowerShell 管理单元](./writing-a-custom-windows-powershell-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="ce446-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="ce446-106">编写 Windows PowerShell 管理单元</span><span class="sxs-lookup"><span data-stu-id="ce446-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="ce446-107">添加 RunInstallerAttribute 特性。</span><span class="sxs-lookup"><span data-stu-id="ce446-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="ce446-108">创建一个派生自[add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)类的公共类。</span><span class="sxs-lookup"><span data-stu-id="ce446-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="ce446-109">在此示例中，类名为 "GetProcPSSnapIn01"。</span><span class="sxs-lookup"><span data-stu-id="ce446-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="ce446-110">为管理单元的名称添加一个公共属性（必需）。</span><span class="sxs-lookup"><span data-stu-id="ce446-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="ce446-111">命名管理单元时，请不要使用以下任何字符： #。</span><span class="sxs-lookup"><span data-stu-id="ce446-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="ce446-112">，（） {} [] &-/\ $;： "" \< >;？</span><span class="sxs-lookup"><span data-stu-id="ce446-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="ce446-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="ce446-113">@ \` \*</span></span>

    <span data-ttu-id="ce446-114">在此示例中，管理单元的名称为 "GetProcPSSnapIn01"。</span><span class="sxs-lookup"><span data-stu-id="ce446-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="ce446-115">添加管理单元供应商的公共属性（必需）。</span><span class="sxs-lookup"><span data-stu-id="ce446-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="ce446-116">在此示例中，供应商为 "Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="ce446-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="ce446-117">添加管理单元的供应商资源的公共属性（可选）。</span><span class="sxs-lookup"><span data-stu-id="ce446-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="ce446-118">在此示例中，供应商资源为 "GetProcPSSnapIn01，Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="ce446-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="ce446-119">添加管理单元说明的公共属性（必需）。</span><span class="sxs-lookup"><span data-stu-id="ce446-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="ce446-120">在此示例中，说明为 "这是一个用于注册 get-help cmdlet 的 Windows PowerShell 管理单元"。</span><span class="sxs-lookup"><span data-stu-id="ce446-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="ce446-121">为管理单元的 "说明" 资源添加公共属性（可选）。</span><span class="sxs-lookup"><span data-stu-id="ce446-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="ce446-122">在此示例中，供应商资源为 "GetProcPSSnapIn01，这是一个用于注册 get-help cmdlet 的 Windows PowerShell 管理单元"。</span><span class="sxs-lookup"><span data-stu-id="ce446-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="ce446-123">示例</span><span class="sxs-lookup"><span data-stu-id="ce446-123">Example</span></span>

<span data-ttu-id="ce446-124">此示例演示如何编写可用于在 Windows PowerShell shell 中注册 Get-help cmdlet 的 Windows PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="ce446-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="ce446-125">请注意，在此示例中，完整的程序集只包含 GetProcPSSnapIn01 管理单元类和 Get-help cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="ce446-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ce446-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce446-126">See Also</span></span>

[<span data-ttu-id="ce446-127">如何注册 Cmdlet、提供程序和主机应用程序</span><span class="sxs-lookup"><span data-stu-id="ce446-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="ce446-128">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="ce446-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
