---
title: Cmdlet 属性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058022"
---
# <a name="cmdlet-attribute-declaration"></a><span data-ttu-id="5f23e-102">Cmdlet 属性声明</span><span class="sxs-lookup"><span data-stu-id="5f23e-102">Cmdlet Attribute Declaration</span></span>

<span data-ttu-id="5f23e-103">Cmdlet 属性标识为 cmdlet 的 Microsoft.NET Framework 类和指定的谓词和名词用于调用该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f23e-103">The Cmdlet attribute identifies a Microsoft .NET Framework class as a cmdlet and specifies the verb and noun used to invoke the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f23e-104">语法</span><span class="sxs-lookup"><span data-stu-id="5f23e-104">Syntax</span></span>

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="5f23e-105">参数</span><span class="sxs-lookup"><span data-stu-id="5f23e-105">Parameters</span></span>

<span data-ttu-id="5f23e-106">`VerbName` ([System.String](/dotnet/api/System.String)) 所需。</span><span class="sxs-lookup"><span data-stu-id="5f23e-106">`VerbName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="5f23e-107">指定 cmdlet 动词。</span><span class="sxs-lookup"><span data-stu-id="5f23e-107">Specifies the cmdlet verb.</span></span> <span data-ttu-id="5f23e-108">此谓词指定该 cmdlet 所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="5f23e-108">This verb specifies the action taken by the cmdlet.</span></span> <span data-ttu-id="5f23e-109">有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)并[所需开发指导原则](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="5f23e-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md) and [Required Development Guidelines](./required-development-guidelines.md).</span></span>

<span data-ttu-id="5f23e-110">`NounName` ([System.String](/dotnet/api/System.String)) 所需。</span><span class="sxs-lookup"><span data-stu-id="5f23e-110">`NounName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="5f23e-111">指定 cmdlet 名词。</span><span class="sxs-lookup"><span data-stu-id="5f23e-111">Specifies the cmdlet noun.</span></span> <span data-ttu-id="5f23e-112">此名词指定 cmdlet 作用于的资源。</span><span class="sxs-lookup"><span data-stu-id="5f23e-112">This noun specifies the resource that the cmdlet acts upon.</span></span> <span data-ttu-id="5f23e-113">有关 cmdlet 名词的详细信息，请参阅[Cmdlet 声明](./cmdlet-class-declaration.md)并[强烈推荐的开发指南](./strongly-encouraged-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="5f23e-113">For more information about cmdlet nouns, see [Cmdlet Declaration](./cmdlet-class-declaration.md) and [Strongly Encouraged Development Guidelines](./strongly-encouraged-development-guidelines.md).</span></span>

<span data-ttu-id="5f23e-114">`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="5f23e-114">`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5f23e-115">`True` 指示该 cmdlet 支持调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，为该 cmdlet 提供了一种方法来执行更改系统的操作前提示用户。</span><span class="sxs-lookup"><span data-stu-id="5f23e-115">`True` indicates that the cmdlet supports calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which provides the cmdlet with a way to prompt the user before an action that changes the system is performed.</span></span> <span data-ttu-id="5f23e-116">`False`默认值，指示该 cmdlet 不支持调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。</span><span class="sxs-lookup"><span data-stu-id="5f23e-116">`False`, the default value, indicates that the cmdlet does not support calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="5f23e-117">确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="5f23e-117">For more information about confirmation requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="5f23e-118">`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="5f23e-118">`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) Optional named parameter.</span></span> <span data-ttu-id="5f23e-119">指定该 cmdlet 的操作时应通过调用确认[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。</span><span class="sxs-lookup"><span data-stu-id="5f23e-119">Specifies when the action of the cmdlet should be confirmed by a call to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="5f23e-120">[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) （默认为 Medium） cmdlet 的 ConfirmImpact 值等于或大于的值时只会调用`$ConfirmPreference`变量。</span><span class="sxs-lookup"><span data-stu-id="5f23e-120">[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) will only be called when the ConfirmImpact value of the cmdlet (by default, Medium) is equal to or greater than the value of the `$ConfirmPreference` variable.</span></span> <span data-ttu-id="5f23e-121">应指定此参数仅当`SupportsShouldProcess`指定参数。</span><span class="sxs-lookup"><span data-stu-id="5f23e-121">This parameter should be specified only when the `SupportsShouldProcess` parameter is specified.</span></span>

<span data-ttu-id="5f23e-122">`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="5f23e-122">`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="5f23e-123">指定 Windows PowerShell 运行时尝试使用时不能确定哪个参数设置为使用默认参数集。</span><span class="sxs-lookup"><span data-stu-id="5f23e-123">Specifies the default parameter set that the Windows PowerShell runtime attempts to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="5f23e-124">请注意，可以设置必需参数的唯一参数的每个参数，从而消除这种情况。</span><span class="sxs-lookup"><span data-stu-id="5f23e-124">Notice that this situation can be eliminated by making the unique parameter of each parameter set a mandatory parameter.</span></span>

<span data-ttu-id="5f23e-125">没有一种情况下，Windows PowerShell 不能使用的默认参数集，即使指定默认参数集名称。</span><span class="sxs-lookup"><span data-stu-id="5f23e-125">There is one case where Windows PowerShell cannot use the default parameter set even if a default parameter set name is specified.</span></span> <span data-ttu-id="5f23e-126">Windows PowerShell 运行时无法区分仅根据对象类型的参数集。</span><span class="sxs-lookup"><span data-stu-id="5f23e-126">The Windows PowerShell runtime cannot distinguish between parameter sets based solely on object type.</span></span> <span data-ttu-id="5f23e-127">例如，如果有一个参数集的文件路径，以及另一组采用一个字符串，采用**FileInfo**对象直接，Windows PowerShell 不能确定哪个参数设置为使用基于传递给的值cmdlet，也不会使用默认参数集。</span><span class="sxs-lookup"><span data-stu-id="5f23e-127">For example, if you have one parameter set that takes a string as the file path, and another set that takes a **FileInfo** object directly, Windows PowerShell cannot determine which parameter set to use based on the values passed to the cmdlet, nor does it use the default parameter set.</span></span> <span data-ttu-id="5f23e-128">在这种情况下，即使指定默认参数集名称，Windows PowerShell 将引发不明确的参数集错误消息。</span><span class="sxs-lookup"><span data-stu-id="5f23e-128">In this case, even if you specify a default parameter set name, Windows PowerShell throws an ambiguous parameter set error message.</span></span>

<span data-ttu-id="5f23e-129">`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="5f23e-129">`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5f23e-130">`True` 指示可以在一个事务内使用此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f23e-130">`True` indicates that the cmdlet can be used within a transaction.</span></span> <span data-ttu-id="5f23e-131">当`True`未指定，则 Windows PowerShell 运行时添加`UseTransaction`到该 cmdlet 的参数列表的参数。</span><span class="sxs-lookup"><span data-stu-id="5f23e-131">When `True` is specified, the Windows PowerShell runtime adds the `UseTransaction` parameter to the parameter list of the cmdlet.</span></span> <span data-ttu-id="5f23e-132">`False`默认值，指示不能在事务中使用此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f23e-132">`False`, the default value, indicates that the cmdlet cannot be used within a transaction.</span></span>

## <a name="remarks"></a><span data-ttu-id="5f23e-133">备注</span><span class="sxs-lookup"><span data-stu-id="5f23e-133">Remarks</span></span>

- <span data-ttu-id="5f23e-134">在一起，动词和名词可用来识别你已注册的 cmdlet 并调用你在脚本中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f23e-134">Together, the verb and noun are used to identify your registered cmdlet and to invoke your cmdlet within a script.</span></span>

- <span data-ttu-id="5f23e-135">从 Windows PowerShell 控制台中调用 cmdlet 时，该命令类似于以下命令：</span><span class="sxs-lookup"><span data-stu-id="5f23e-135">When the cmdlet is invoked from the Windows PowerShell console, the command resembles the following command:</span></span>

<span data-ttu-id="5f23e-136">**VerbName-NounName**</span><span class="sxs-lookup"><span data-stu-id="5f23e-136">**VerbName-NounName**</span></span>

- <span data-ttu-id="5f23e-137">更改资源在 Windows PowerShell 之外的所有 cmdlet 应都包括`SupportsShouldProcess`关键字声明 Cmdlet 属性，它允许该 cmdlet 将调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前该 cmdlet 将执行其操作。</span><span class="sxs-lookup"><span data-stu-id="5f23e-137">All cmdlets that change resources outside of Windows PowerShell should include the `SupportsShouldProcess` keyword when the Cmdlet attribute is declared, which allows the cmdlet to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the cmdlet performs its action.</span></span> <span data-ttu-id="5f23e-138">如果[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用返回`false`，不应执行操作。</span><span class="sxs-lookup"><span data-stu-id="5f23e-138">If the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call returns `false`, the action should not be taken.</span></span> <span data-ttu-id="5f23e-139">有关生成的确认请求的详细信息[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="5f23e-139">For more information about the confirmation requests generated by the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="5f23e-140">`Confirm`并`WhatIf`cmdlet 参数是仅适用于支持的 cmdlet [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用。</span><span class="sxs-lookup"><span data-stu-id="5f23e-140">The `Confirm` and `WhatIf` cmdlet parameters are available only for cmdlets that support [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) calls.</span></span>

## <a name="example"></a><span data-ttu-id="5f23e-141">示例</span><span class="sxs-lookup"><span data-stu-id="5f23e-141">Example</span></span>

<span data-ttu-id="5f23e-142">以下类定义使用 Cmdlet 属性标识的.NET Framework 类**Get-proc** cmdlet 检索有关本地计算机上运行的进程的信息。</span><span class="sxs-lookup"><span data-stu-id="5f23e-142">The following class definition uses the Cmdlet attribute to identify the .NET Framework class for a **Get-Proc** cmdlet that retrieves information about the processes running on the local computer.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="5f23e-143">有关详细信息**Get-proc** cmdlet，请参阅[GetProc 教程](./getproc-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="5f23e-143">For more information about the **Get-Proc** cmdlet, see [GetProc Tutorial](./getproc-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f23e-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f23e-144">See Also</span></span>

[<span data-ttu-id="5f23e-145">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f23e-145">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
