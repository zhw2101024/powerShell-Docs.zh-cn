---
title: Cmdlet 特性声明 |Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363536"
---
# <a name="cmdlet-attribute-declaration"></a><span data-ttu-id="a41c5-102">Cmdlet 属性声明</span><span class="sxs-lookup"><span data-stu-id="a41c5-102">Cmdlet Attribute Declaration</span></span>

<span data-ttu-id="a41c5-103">Cmdlet 属性将 Microsoft .NET 框架类标识为 Cmdlet，并指定用于调用 cmdlet 的动词和名词。</span><span class="sxs-lookup"><span data-stu-id="a41c5-103">The Cmdlet attribute identifies a Microsoft .NET Framework class as a cmdlet and specifies the verb and noun used to invoke the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="a41c5-104">语法</span><span class="sxs-lookup"><span data-stu-id="a41c5-104">Syntax</span></span>

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="a41c5-105">参数</span><span class="sxs-lookup"><span data-stu-id="a41c5-105">Parameters</span></span>

<span data-ttu-id="a41c5-106">需要 `VerbName` （[system.string](/dotnet/api/System.String)）。</span><span class="sxs-lookup"><span data-stu-id="a41c5-106">`VerbName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="a41c5-107">指定 cmdlet 谓词。</span><span class="sxs-lookup"><span data-stu-id="a41c5-107">Specifies the cmdlet verb.</span></span> <span data-ttu-id="a41c5-108">此谓词指定 cmdlet 执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a41c5-108">This verb specifies the action taken by the cmdlet.</span></span> <span data-ttu-id="a41c5-109">有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)和[所需的开发指南](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="a41c5-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md) and [Required Development Guidelines](./required-development-guidelines.md).</span></span>

<span data-ttu-id="a41c5-110">需要 `NounName` （[system.string](/dotnet/api/System.String)）。</span><span class="sxs-lookup"><span data-stu-id="a41c5-110">`NounName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="a41c5-111">指定 cmdlet 名词。</span><span class="sxs-lookup"><span data-stu-id="a41c5-111">Specifies the cmdlet noun.</span></span> <span data-ttu-id="a41c5-112">此名词指定该 cmdlet 作用于的资源。</span><span class="sxs-lookup"><span data-stu-id="a41c5-112">This noun specifies the resource that the cmdlet acts upon.</span></span> <span data-ttu-id="a41c5-113">有关 cmdlet 名词的详细信息，请参阅[Cmdlet 声明](./cmdlet-class-declaration.md)和[强烈建议开发指南](./strongly-encouraged-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="a41c5-113">For more information about cmdlet nouns, see [Cmdlet Declaration](./cmdlet-class-declaration.md) and [Strongly Encouraged Development Guidelines](./strongly-encouraged-development-guidelines.md).</span></span>

<span data-ttu-id="a41c5-114">`SupportsShouldProcess` （[system.string](/dotnet/api/System.Boolean)）可选命名参数。</span><span class="sxs-lookup"><span data-stu-id="a41c5-114">`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a41c5-115">`True` 指示 cmdlet 支持对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的调用，该方法为 cmdlet 提供了一种在执行更改系统的操作之前提示用户的方法。</span><span class="sxs-lookup"><span data-stu-id="a41c5-115">`True` indicates that the cmdlet supports calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which provides the cmdlet with a way to prompt the user before an action that changes the system is performed.</span></span> <span data-ttu-id="a41c5-116">`False`（默认值），则指示该 cmdlet 不支持对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的调用。</span><span class="sxs-lookup"><span data-stu-id="a41c5-116">`False`, the default value, indicates that the cmdlet does not support calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="a41c5-117">有关确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="a41c5-117">For more information about confirmation requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="a41c5-118">`ConfirmImpact` （[Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)）可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="a41c5-118">`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) Optional named parameter.</span></span> <span data-ttu-id="a41c5-119">指定应通过对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的调用来确认 cmdlet 的操作的时间的。</span><span class="sxs-lookup"><span data-stu-id="a41c5-119">Specifies when the action of the cmdlet should be confirmed by a call to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="a41c5-120">仅当 Cmdlet 的 ConfirmImpact 值（默认情况下，Medium）等于或大于 `$ConfirmPreference` 变量的值时，才会调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)变量。</span><span class="sxs-lookup"><span data-stu-id="a41c5-120">[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) will only be called when the ConfirmImpact value of the cmdlet (by default, Medium) is equal to or greater than the value of the `$ConfirmPreference` variable.</span></span> <span data-ttu-id="a41c5-121">仅当指定了 `SupportsShouldProcess` 参数时，才应指定此参数。</span><span class="sxs-lookup"><span data-stu-id="a41c5-121">This parameter should be specified only when the `SupportsShouldProcess` parameter is specified.</span></span>

<span data-ttu-id="a41c5-122">`DefaultParameterSetName` （[system.string](/dotnet/api/System.String)）可选的命名参数。</span><span class="sxs-lookup"><span data-stu-id="a41c5-122">`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="a41c5-123">指定 Windows PowerShell 运行时在无法确定要使用哪个参数时尝试使用的默认参数集。</span><span class="sxs-lookup"><span data-stu-id="a41c5-123">Specifies the default parameter set that the Windows PowerShell runtime attempts to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="a41c5-124">请注意，可以通过使每个参数的唯一参数设置一个必需的参数来消除这种情况。</span><span class="sxs-lookup"><span data-stu-id="a41c5-124">Notice that this situation can be eliminated by making the unique parameter of each parameter set a mandatory parameter.</span></span>

<span data-ttu-id="a41c5-125">在这种情况下，即使指定了默认参数集名称，Windows PowerShell 也无法使用默认参数集。</span><span class="sxs-lookup"><span data-stu-id="a41c5-125">There is one case where Windows PowerShell cannot use the default parameter set even if a default parameter set name is specified.</span></span> <span data-ttu-id="a41c5-126">Windows PowerShell 运行时无法仅基于对象类型区分参数集。</span><span class="sxs-lookup"><span data-stu-id="a41c5-126">The Windows PowerShell runtime cannot distinguish between parameter sets based solely on object type.</span></span> <span data-ttu-id="a41c5-127">例如，如果你有一个参数集，该参数集采用字符串作为文件路径，而另一个组直接采用**FileInfo**对象，则 Windows PowerShell 无法根据传递给 cmdlet 的值来确定要使用的参数集，也不会使用默认参数集。</span><span class="sxs-lookup"><span data-stu-id="a41c5-127">For example, if you have one parameter set that takes a string as the file path, and another set that takes a **FileInfo** object directly, Windows PowerShell cannot determine which parameter set to use based on the values passed to the cmdlet, nor does it use the default parameter set.</span></span> <span data-ttu-id="a41c5-128">在这种情况下，即使指定默认参数集名称，Windows PowerShell 也会引发不明确的参数集错误消息。</span><span class="sxs-lookup"><span data-stu-id="a41c5-128">In this case, even if you specify a default parameter set name, Windows PowerShell throws an ambiguous parameter set error message.</span></span>

<span data-ttu-id="a41c5-129">`SupportsTransactions` （[system.string](/dotnet/api/System.Boolean)）可选命名参数。</span><span class="sxs-lookup"><span data-stu-id="a41c5-129">`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a41c5-130">`True` 指示该 cmdlet 可以在事务中使用。</span><span class="sxs-lookup"><span data-stu-id="a41c5-130">`True` indicates that the cmdlet can be used within a transaction.</span></span> <span data-ttu-id="a41c5-131">指定 `True` 时，Windows PowerShell 运行时将 `UseTransaction` 参数添加到 cmdlet 的参数列表中。</span><span class="sxs-lookup"><span data-stu-id="a41c5-131">When `True` is specified, the Windows PowerShell runtime adds the `UseTransaction` parameter to the parameter list of the cmdlet.</span></span> <span data-ttu-id="a41c5-132">`False`（默认值）指示不能在事务中使用该 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a41c5-132">`False`, the default value, indicates that the cmdlet cannot be used within a transaction.</span></span>

## <a name="remarks"></a><span data-ttu-id="a41c5-133">备注</span><span class="sxs-lookup"><span data-stu-id="a41c5-133">Remarks</span></span>

- <span data-ttu-id="a41c5-134">同时，动词和名词用于标识已注册的 cmdlet，并在脚本中调用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a41c5-134">Together, the verb and noun are used to identify your registered cmdlet and to invoke your cmdlet within a script.</span></span>

- <span data-ttu-id="a41c5-135">当从 Windows PowerShell 控制台调用 cmdlet 时，该命令将类似于以下命令：</span><span class="sxs-lookup"><span data-stu-id="a41c5-135">When the cmdlet is invoked from the Windows PowerShell console, the command resembles the following command:</span></span>

<span data-ttu-id="a41c5-136">**VerbName-NounName**</span><span class="sxs-lookup"><span data-stu-id="a41c5-136">**VerbName-NounName**</span></span>

- <span data-ttu-id="a41c5-137">在声明 Cmdlet 属性时，更改 Windows PowerShell 外部资源的所有 cmdlet 都应包括 `SupportsShouldProcess` 关键字，这允许 cmdlet 在 cmdlet 执行操作之前调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。</span><span class="sxs-lookup"><span data-stu-id="a41c5-137">All cmdlets that change resources outside of Windows PowerShell should include the `SupportsShouldProcess` keyword when the Cmdlet attribute is declared, which allows the cmdlet to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the cmdlet performs its action.</span></span> <span data-ttu-id="a41c5-138">如果[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用返回 `false`，则不应执行该操作。</span><span class="sxs-lookup"><span data-stu-id="a41c5-138">If the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call returns `false`, the action should not be taken.</span></span> <span data-ttu-id="a41c5-139">有关[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用生成的确认请求的详细信息，请参阅[请求确认](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="a41c5-139">For more information about the confirmation requests generated by the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="a41c5-140">`Confirm` 和 `WhatIf` cmdlet 参数仅可用于支持[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用的 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a41c5-140">The `Confirm` and `WhatIf` cmdlet parameters are available only for cmdlets that support [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) calls.</span></span>

## <a name="example"></a><span data-ttu-id="a41c5-141">示例</span><span class="sxs-lookup"><span data-stu-id="a41c5-141">Example</span></span>

<span data-ttu-id="a41c5-142">下面的类定义使用 Cmdlet 特性来标识用于检索有关在本地计算机上运行的进程的信息的**get-help** Cmdlet 的 .NET Framework 类。</span><span class="sxs-lookup"><span data-stu-id="a41c5-142">The following class definition uses the Cmdlet attribute to identify the .NET Framework class for a **Get-Proc** cmdlet that retrieves information about the processes running on the local computer.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="a41c5-143">有关 GetProc **cmdlet 的**详细信息，请参阅[教程](./getproc-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="a41c5-143">For more information about the **Get-Proc** cmdlet, see [GetProc Tutorial](./getproc-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a41c5-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a41c5-144">See Also</span></span>

[<span data-ttu-id="a41c5-145">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a41c5-145">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
