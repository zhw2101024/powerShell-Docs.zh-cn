---
title: Windows PowerShell 概念 |Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366676"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="4e993-102">Windows PowerShell 概念</span><span class="sxs-lookup"><span data-stu-id="4e993-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="4e993-103">本部分包含有助于从开发人员的角度了解 PowerShell 的概念信息。</span><span class="sxs-lookup"><span data-stu-id="4e993-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="4e993-104">主题名称</span><span class="sxs-lookup"><span data-stu-id="4e993-104">Topic Name</span></span>|<span data-ttu-id="4e993-105">描述</span><span class="sxs-lookup"><span data-stu-id="4e993-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="4e993-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="4e993-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="4e993-107">PowerShell 对象的说明。</span><span class="sxs-lookup"><span data-stu-id="4e993-107">Description of PowerShell objects.</span></span> <span data-ttu-id="4e993-108">有关详细信息，请参阅[关于对象创建](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="4e993-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="4e993-109">正在创建运行空间</span><span class="sxs-lookup"><span data-stu-id="4e993-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="4e993-110">处理命令的操作环境。</span><span class="sxs-lookup"><span data-stu-id="4e993-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="4e993-111">有关详细信息，请参阅[运行空间类](/dotnet/api/system.management.automation.runspaces.runspace)。</span><span class="sxs-lookup"><span data-stu-id="4e993-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="4e993-112">扩展输出对象</span><span class="sxs-lookup"><span data-stu-id="4e993-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="4e993-113">如何扩展 PowerShell 对象。</span><span class="sxs-lookup"><span data-stu-id="4e993-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="4e993-114">有关详细信息，请参阅[关于类型。 types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="4e993-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="4e993-115">注册 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e993-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="4e993-116">如何在 PowerShell 中提供模块和管理单元。</span><span class="sxs-lookup"><span data-stu-id="4e993-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="4e993-117">有关详细信息，请参阅[模块和管理单元](../cmdlet/modules-and-snap-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="4e993-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="4e993-118">从 Cmdlet 请求确认</span><span class="sxs-lookup"><span data-stu-id="4e993-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="4e993-119">在采取操作之前，cmdlet 和提供程序如何请求用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="4e993-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="4e993-120">RuntimeDefinedParameter 类</span><span class="sxs-lookup"><span data-stu-id="4e993-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="4e993-121">运行时参数声明。</span><span class="sxs-lookup"><span data-stu-id="4e993-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="4e993-122">System.web 命名空间</span><span class="sxs-lookup"><span data-stu-id="4e993-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="4e993-123">PowerShell API 命名空间的概述。</span><span class="sxs-lookup"><span data-stu-id="4e993-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="4e993-124">Windows PowerShell 提供程序概述</span><span class="sxs-lookup"><span data-stu-id="4e993-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="4e993-125">有关用于访问数据存储区的 PowerShell 提供程序的概述。</span><span class="sxs-lookup"><span data-stu-id="4e993-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="4e993-126">编写 PowerShell Cmdlet 的帮助</span><span class="sxs-lookup"><span data-stu-id="4e993-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="4e993-127">如何编写 PowerShell cmdlet 帮助。</span><span class="sxs-lookup"><span data-stu-id="4e993-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4e993-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e993-128">See also</span></span>

[<span data-ttu-id="4e993-129">PowerShell 类</span><span class="sxs-lookup"><span data-stu-id="4e993-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="4e993-130">PowerShell Core API 参考</span><span class="sxs-lookup"><span data-stu-id="4e993-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="4e993-131">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="4e993-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4e993-132">为 Windows PowerShell 模块编写帮助</span><span class="sxs-lookup"><span data-stu-id="4e993-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="4e993-133">编写 Windows Powershell 提供程序</span><span class="sxs-lookup"><span data-stu-id="4e993-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="4e993-134">Windows PowerShell API 参考</span><span class="sxs-lookup"><span data-stu-id="4e993-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="4e993-135">Windows PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="4e993-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)