---
title: 在 Cmdlet 中调用 Cmdlet 和脚本 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364286"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="69680-102">调用 Cmdlet 中的 Cmdlet 和脚本</span><span class="sxs-lookup"><span data-stu-id="69680-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="69680-103">Cmdlet 可以从 cmdlet 的输入处理方法中调用其他 cmdlet 和脚本。</span><span class="sxs-lookup"><span data-stu-id="69680-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="69680-104">这样，便可以将现有 cmdlet 和脚本的功能添加到 cmdlet，而无需重写代码。</span><span class="sxs-lookup"><span data-stu-id="69680-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="69680-105">Invoke 方法</span><span class="sxs-lookup"><span data-stu-id="69680-105">The Invoke Method</span></span>

<span data-ttu-id="69680-106">所有 cmdlet 都可以通过从 cmdlet 重写的输入处理方法中调用[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法来调用现有的 cmdlet，例如，该 cmdlet 会重写[此方法。](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)</span><span class="sxs-lookup"><span data-stu-id="69680-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="69680-107">但是，你只能调用直接从[system.web](/dotnet/api/System.Management.Automation.Cmdlet)类派生的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="69680-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="69680-108">不能调用派生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="69680-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="69680-109">" [System.object](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) " 方法具有以下变体。</span><span class="sxs-lookup"><span data-stu-id="69680-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="69680-110">。[调用](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此变体将调用 Cmdlet 对象，并返回 "T" 类型对象的集合。</span><span class="sxs-lookup"><span data-stu-id="69680-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="69680-111">。[调用](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此变体将调用 Cmdlet 对象并返回强类型化的 emumerator。</span><span class="sxs-lookup"><span data-stu-id="69680-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="69680-112">此变体允许用户使用集合中的对象执行自定义操作。</span><span class="sxs-lookup"><span data-stu-id="69680-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="69680-113">示例</span><span class="sxs-lookup"><span data-stu-id="69680-113">Examples</span></span>

|<span data-ttu-id="69680-114">示例</span><span class="sxs-lookup"><span data-stu-id="69680-114">Example</span></span>|<span data-ttu-id="69680-115">描述</span><span class="sxs-lookup"><span data-stu-id="69680-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69680-116">在 Cmdlet 中调用 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69680-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="69680-117">此示例演示如何从另一个 cmdlet 中调用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="69680-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="69680-118">在 Cmdlet 中调用脚本</span><span class="sxs-lookup"><span data-stu-id="69680-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="69680-119">此示例演示如何从另一个 cmdlet 中调用提供给 cmdlet 的脚本。</span><span class="sxs-lookup"><span data-stu-id="69680-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="69680-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69680-120">See Also</span></span>

[<span data-ttu-id="69680-121">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69680-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
