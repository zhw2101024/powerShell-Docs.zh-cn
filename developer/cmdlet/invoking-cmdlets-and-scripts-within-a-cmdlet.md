---
title: 调用 Cmdlet 和 Cmdlet 中的脚本 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058872"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="ab8da-102">调用 Cmdlet 中的 Cmdlet 和脚本</span><span class="sxs-lookup"><span data-stu-id="ab8da-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="ab8da-103">Cmdlet 可以调用其他 cmdlet 和脚本中的输入处理方法的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ab8da-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="ab8da-104">这可以将现有的 cmdlet 和脚本的功能添加到 cmdlet，而无需重写代码。</span><span class="sxs-lookup"><span data-stu-id="ab8da-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="ab8da-105">调用方法</span><span class="sxs-lookup"><span data-stu-id="ab8da-105">The Invoke Method</span></span>

<span data-ttu-id="ab8da-106">所有 cmdlet 可以通过调用都调用现有 cmdlet [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法的输入处理方法，如[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)，即该 cmdlet 通过重写。</span><span class="sxs-lookup"><span data-stu-id="ab8da-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="ab8da-107">但是，可以调用仅直接派生这些 cmdlet [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类。</span><span class="sxs-lookup"><span data-stu-id="ab8da-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="ab8da-108">不能调用派生的 cmdlet [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类。</span><span class="sxs-lookup"><span data-stu-id="ab8da-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="ab8da-109">[System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法具有以下变体。</span><span class="sxs-lookup"><span data-stu-id="ab8da-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="ab8da-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此变体调用 cmdlet 对象并返回"T"类型对象的集合。</span><span class="sxs-lookup"><span data-stu-id="ab8da-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="ab8da-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此变体调用 cmdlet 对象并返回强类型化的 emumerator。</span><span class="sxs-lookup"><span data-stu-id="ab8da-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="ab8da-112">此变体允许用户使用集合中的对象来执行自定义操作。</span><span class="sxs-lookup"><span data-stu-id="ab8da-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="ab8da-113">示例</span><span class="sxs-lookup"><span data-stu-id="ab8da-113">Examples</span></span>

|<span data-ttu-id="ab8da-114">示例</span><span class="sxs-lookup"><span data-stu-id="ab8da-114">Example</span></span>|<span data-ttu-id="ab8da-115">说明</span><span class="sxs-lookup"><span data-stu-id="ab8da-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab8da-116">调用某个 Cmdlet 中的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab8da-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="ab8da-117">此示例演示如何调用在另一个 cmdlet 中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ab8da-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="ab8da-118">调用某个 Cmdlet 中的脚本</span><span class="sxs-lookup"><span data-stu-id="ab8da-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="ab8da-119">此示例演示如何调用脚本提供给在另一个 cmdlet 从 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ab8da-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ab8da-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab8da-120">See Also</span></span>

[<span data-ttu-id="ab8da-121">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab8da-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
