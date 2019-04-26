---
title: Windows PowerShell 会话状态 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066968"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="9e451-102">Windows PowerShell 会话状态</span><span class="sxs-lookup"><span data-stu-id="9e451-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="9e451-103">会话状态是指 Windows PowerShell 会话或模块的当前配置。</span><span class="sxs-lookup"><span data-stu-id="9e451-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="9e451-104">Windows PowerShell 会话是通过命令行的用户或以编程方式通过主机应用程序以交互方式使用的操作环境。</span><span class="sxs-lookup"><span data-stu-id="9e451-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="9e451-105">会话的会话状态称为全局会话状态。</span><span class="sxs-lookup"><span data-stu-id="9e451-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="9e451-106">从开发人员的角度，Windows PowerShell 会话是指当主机应用程序打开 Windows PowerShell 运行空间和它关闭时运行空间之间的时间。</span><span class="sxs-lookup"><span data-stu-id="9e451-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="9e451-107">介绍了另一种方法，会话是实例的在运行空间存在时调用的 Windows PowerShell 引擎的生存期。</span><span class="sxs-lookup"><span data-stu-id="9e451-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="9e451-108">模块会话状态</span><span class="sxs-lookup"><span data-stu-id="9e451-108">Module Session State</span></span>

<span data-ttu-id="9e451-109">只要该模块或其嵌套模块之一导入会话就会创建模块的会话状态。</span><span class="sxs-lookup"><span data-stu-id="9e451-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="9e451-110">当模块可导出一个元素，如 cmdlet、 函数或脚本时，该元素的引用被添加到会话的全局会话状态。</span><span class="sxs-lookup"><span data-stu-id="9e451-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="9e451-111">但是，当运行时元素，它中执行该模块的会话状态。</span><span class="sxs-lookup"><span data-stu-id="9e451-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="9e451-112">会话状态数据</span><span class="sxs-lookup"><span data-stu-id="9e451-112">Session-State Data</span></span>

<span data-ttu-id="9e451-113">会话状态数据可以是公共或私有。</span><span class="sxs-lookup"><span data-stu-id="9e451-113">Session state data can be public or private.</span></span> <span data-ttu-id="9e451-114">公共数据可供外部会话状态调用专用数据可仅用于从会话状态中的调用时。</span><span class="sxs-lookup"><span data-stu-id="9e451-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="9e451-115">例如，模块可以有一个私有函数可以仅由模块或仅在内部调用的已导出的公共元素。</span><span class="sxs-lookup"><span data-stu-id="9e451-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="9e451-116">这是类似于.NET Framework 类型的私有和公共成员。</span><span class="sxs-lookup"><span data-stu-id="9e451-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="9e451-117">会话状态数据存储的当前 Windows PowerShell 会话的上下文中的执行引擎的当前实例。</span><span class="sxs-lookup"><span data-stu-id="9e451-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="9e451-118">会话状态数据包含以下各项：</span><span class="sxs-lookup"><span data-stu-id="9e451-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="9e451-119">路径信息</span><span class="sxs-lookup"><span data-stu-id="9e451-119">Path information</span></span>

- <span data-ttu-id="9e451-120">驱动器信息</span><span class="sxs-lookup"><span data-stu-id="9e451-120">Drive information</span></span>

- <span data-ttu-id="9e451-121">Windows PowerShell 提供程序信息</span><span class="sxs-lookup"><span data-stu-id="9e451-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="9e451-122">有关导入的模块和对由模块导出的模块元素 （如 cmdlet、 函数和脚本） 的引用信息。</span><span class="sxs-lookup"><span data-stu-id="9e451-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="9e451-123">此信息和这些引用，可仅全局会话状态。</span><span class="sxs-lookup"><span data-stu-id="9e451-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="9e451-124">会话状态变量信息</span><span class="sxs-lookup"><span data-stu-id="9e451-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="9e451-125">访问在 Cmdlet 中的会话状态数据</span><span class="sxs-lookup"><span data-stu-id="9e451-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="9e451-126">Cmdlet 可以访问会话状态数据可以通过间接[System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)属性的 cmdlet 类或直接通过[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)类。</span><span class="sxs-lookup"><span data-stu-id="9e451-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="9e451-127">[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)类提供了可用于调查的会话状态数据的不同类型的属性。</span><span class="sxs-lookup"><span data-stu-id="9e451-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e451-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e451-128">See Also</span></span>

[<span data-ttu-id="9e451-129">System.Management.Automation.PSCmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="9e451-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="9e451-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="9e451-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="9e451-131">Windows PowerShell Cmdlets</span><span class="sxs-lookup"><span data-stu-id="9e451-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="9e451-132">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e451-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="9e451-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="9e451-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
