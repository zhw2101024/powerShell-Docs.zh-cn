---
title: 如何替代输入处理方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364466"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="fe929-102">如何替代输入处理方法</span><span class="sxs-lookup"><span data-stu-id="fe929-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="fe929-103">这些示例演示如何在 cmdlet 中覆盖输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="fe929-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="fe929-104">这些方法用于执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="fe929-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="fe929-105">[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法用于执行对 Cmdlet 所处理的所有对象均有效的一次启动操作的启动操作。</span><span class="sxs-lookup"><span data-stu-id="fe929-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="fe929-106">Windows PowerShell 运行时只调用一次此方法。</span><span class="sxs-lookup"><span data-stu-id="fe929-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="fe929-107">[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法用来处理传递给 Cmdlet 的对象。）。</span><span class="sxs-lookup"><span data-stu-id="fe929-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="fe929-108">Windows PowerShell 运行时为传递到 cmdlet 的每个对象调用此方法。</span><span class="sxs-lookup"><span data-stu-id="fe929-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="fe929-109">使用的是一次后处理操作的 "[系统管理](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)程序" 方法。</span><span class="sxs-lookup"><span data-stu-id="fe929-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="fe929-110">Windows PowerShell 运行时只调用一次此方法。</span><span class="sxs-lookup"><span data-stu-id="fe929-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="fe929-111">重写 BeginProcessing 方法</span><span class="sxs-lookup"><span data-stu-id="fe929-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="fe929-112">声明一个受保护的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法重写。</span><span class="sxs-lookup"><span data-stu-id="fe929-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="fe929-113">下面的类打印示例消息。</span><span class="sxs-lookup"><span data-stu-id="fe929-113">The following class prints a sample message.</span></span> <span data-ttu-id="fe929-114">若要使用此类，请更改 Cmdlet 属性中的动词和名词，更改类的名称以反映新的动词和名词，然后将所需的功能添加到[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)的重写中。付款方式.</span><span class="sxs-lookup"><span data-stu-id="fe929-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="fe929-115">重写 ProcessRecord 方法</span><span class="sxs-lookup"><span data-stu-id="fe929-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="fe929-116">声明一个受保护的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法重写。</span><span class="sxs-lookup"><span data-stu-id="fe929-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="fe929-117">下面的类打印示例消息。</span><span class="sxs-lookup"><span data-stu-id="fe929-117">The following class prints a sample message.</span></span> <span data-ttu-id="fe929-118">若要使用此类，请更改 Cmdlet 属性中的动词和名词，更改类的名称以反映新的动词和名词，然后将所需的功能添加到[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的重写。</span><span class="sxs-lookup"><span data-stu-id="fe929-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="fe929-119">重写 EndProcessing 方法</span><span class="sxs-lookup"><span data-stu-id="fe929-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="fe929-120">声明一个受保护的[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法重写。</span><span class="sxs-lookup"><span data-stu-id="fe929-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="fe929-121">下面的类输出示例。</span><span class="sxs-lookup"><span data-stu-id="fe929-121">The following class prints a sample.</span></span> <span data-ttu-id="fe929-122">若要使用此类，请更改 Cmdlet 特性中的谓词和名词，更改类的名称以反映新的动词和名词，然后将所需的功能添加到重[写的](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)</span><span class="sxs-lookup"><span data-stu-id="fe929-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="fe929-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe929-123">See Also</span></span>

[<span data-ttu-id="fe929-124">"BeginProcessing"。</span><span class="sxs-lookup"><span data-stu-id="fe929-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="fe929-125">System.web. EndProcessing. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="fe929-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="fe929-126">"ProcessRecord"。</span><span class="sxs-lookup"><span data-stu-id="fe929-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="fe929-127">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fe929-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
