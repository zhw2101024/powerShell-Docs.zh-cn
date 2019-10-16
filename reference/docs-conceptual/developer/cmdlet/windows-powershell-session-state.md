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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369096"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="fd479-102">Windows PowerShell 会话状态</span><span class="sxs-lookup"><span data-stu-id="fd479-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="fd479-103">会话状态是指 Windows PowerShell 会话或模块的当前配置。</span><span class="sxs-lookup"><span data-stu-id="fd479-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="fd479-104">Windows PowerShell 会话是命令行用户以交互方式或通过主机应用程序以编程方式使用的操作环境。</span><span class="sxs-lookup"><span data-stu-id="fd479-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="fd479-105">会话的会话状态称为全局会话状态。</span><span class="sxs-lookup"><span data-stu-id="fd479-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="fd479-106">从开发人员的角度来看，Windows PowerShell 会话是指主机应用程序打开 Windows PowerShell 运行空间和关闭运行空间之间的时间。</span><span class="sxs-lookup"><span data-stu-id="fd479-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="fd479-107">作为另一种方法，会话是运行空间存在时调用的 Windows PowerShell 引擎实例的生存期。</span><span class="sxs-lookup"><span data-stu-id="fd479-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="fd479-108">模块会话状态</span><span class="sxs-lookup"><span data-stu-id="fd479-108">Module Session State</span></span>

<span data-ttu-id="fd479-109">只要模块或其一个嵌套模块导入到会话中，就会创建模块会话状态。</span><span class="sxs-lookup"><span data-stu-id="fd479-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="fd479-110">模块导出元素（如 cmdlet、函数或脚本）时，会将对该元素的引用添加到该会话的全局会话状态。</span><span class="sxs-lookup"><span data-stu-id="fd479-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="fd479-111">但是，当元素运行时，它将在模块的会话状态中执行。</span><span class="sxs-lookup"><span data-stu-id="fd479-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="fd479-112">会话状态数据</span><span class="sxs-lookup"><span data-stu-id="fd479-112">Session-State Data</span></span>

<span data-ttu-id="fd479-113">会话状态数据可以是公共或私有。</span><span class="sxs-lookup"><span data-stu-id="fd479-113">Session state data can be public or private.</span></span> <span data-ttu-id="fd479-114">公共数据可用于从会话状态外调用，而专用数据仅可用于从会话状态中调用。</span><span class="sxs-lookup"><span data-stu-id="fd479-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="fd479-115">例如，模块可以具有私有函数，该函数只能由模块调用，或仅由已导出的公共元素在内部调用。</span><span class="sxs-lookup"><span data-stu-id="fd479-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="fd479-116">这类似于 .NET Framework 类型的私有和公共成员。</span><span class="sxs-lookup"><span data-stu-id="fd479-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="fd479-117">会话状态数据由当前 Windows PowerShell 会话上下文中的当前执行引擎实例存储。</span><span class="sxs-lookup"><span data-stu-id="fd479-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="fd479-118">会话状态数据由以下项组成：</span><span class="sxs-lookup"><span data-stu-id="fd479-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="fd479-119">路径信息</span><span class="sxs-lookup"><span data-stu-id="fd479-119">Path information</span></span>

- <span data-ttu-id="fd479-120">驱动器信息</span><span class="sxs-lookup"><span data-stu-id="fd479-120">Drive information</span></span>

- <span data-ttu-id="fd479-121">Windows PowerShell 提供程序信息</span><span class="sxs-lookup"><span data-stu-id="fd479-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="fd479-122">有关已导入的模块以及模块导出的模块元素（如 cmdlet、函数和脚本）的引用的信息。</span><span class="sxs-lookup"><span data-stu-id="fd479-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="fd479-123">此信息和这些引用仅适用于全局会话状态。</span><span class="sxs-lookup"><span data-stu-id="fd479-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="fd479-124">会话状态变量信息</span><span class="sxs-lookup"><span data-stu-id="fd479-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="fd479-125">访问 Cmdlet 内的会话状态数据</span><span class="sxs-lookup"><span data-stu-id="fd479-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="fd479-126">Cmdlet 可以通过 cmdlet 类的[PSCmdlet. Sessionstate \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)属性间接访问会话状态数据，也可以直接通过[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)类访问会话状态数据。</span><span class="sxs-lookup"><span data-stu-id="fd479-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="fd479-127">[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)类提供属性，这些属性可用于调查不同类型的会话状态数据。</span><span class="sxs-lookup"><span data-stu-id="fd479-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd479-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd479-128">See Also</span></span>

[<span data-ttu-id="fd479-129">PSCmdlet. Sessionstate。</span><span class="sxs-lookup"><span data-stu-id="fd479-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="fd479-130">Sessionstate 吗？Displayproperty = Fullname</span><span class="sxs-lookup"><span data-stu-id="fd479-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="fd479-131">Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fd479-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="fd479-132">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fd479-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="fd479-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="fd479-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
