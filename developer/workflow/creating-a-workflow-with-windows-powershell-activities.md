---
title: 使用 Windows PowerShell 活动创建工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853463"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="0460b-102">创建具有 Windows PowerShell 活动的工作流</span><span class="sxs-lookup"><span data-stu-id="0460b-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="0460b-103">通过从 Visual Studio 工具箱中选择活动并将其拖动到工作流设计器窗口，可以创建 Windows PowerShell 工作流。</span><span class="sxs-lookup"><span data-stu-id="0460b-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="0460b-104">有关将 Windows PowerShell 活动添加到 Visual Studio 工具箱的信息，请参阅[到 Visual Studio 工具箱中添加 Windows PowerShell 活动](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="0460b-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="0460b-105">以下过程描述如何创建检查一组用户指定计算机的域状态，将它们加入到域中，如果它们已未联接，然后再次检查状态的工作流。</span><span class="sxs-lookup"><span data-stu-id="0460b-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="0460b-106">设置项目</span><span class="sxs-lookup"><span data-stu-id="0460b-106">Setting up the Project</span></span>

1. <span data-ttu-id="0460b-107">按照中的过程[到 Visual Studio 工具箱中添加 Windows PowerShell 活动](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)若要创建工作流项目并添加从活动[Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)并[Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)到工具箱的程序集。</span><span class="sxs-lookup"><span data-stu-id="0460b-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="0460b-108">将 System.Management.Automation、 Microsoft.PowerShell.Activities、 System.Management、 Microsoft.PowerShell.Management.Activities 和 Microsoft.PowerShell.Commands.Management 关于项目添加为引用程序集。</span><span class="sxs-lookup"><span data-stu-id="0460b-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="0460b-109">将活动添加到工作流</span><span class="sxs-lookup"><span data-stu-id="0460b-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="0460b-110">添加**序列**到工作流活动。</span><span class="sxs-lookup"><span data-stu-id="0460b-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="0460b-111">创建名为的参数`ComputerName`使用的参数类型为`String[]`。</span><span class="sxs-lookup"><span data-stu-id="0460b-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="0460b-112">此参数表示要检查并加入的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="0460b-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="0460b-113">创建名为的参数`DomainCred`类型的[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)。</span><span class="sxs-lookup"><span data-stu-id="0460b-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="0460b-114">此参数表示有权将计算机加入到域的域帐户的域凭据。</span><span class="sxs-lookup"><span data-stu-id="0460b-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="0460b-115">创建名为的参数`MachineCred`类型的[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)。</span><span class="sxs-lookup"><span data-stu-id="0460b-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="0460b-116">此参数表示要检查并加入的计算机上管理员的凭据。</span><span class="sxs-lookup"><span data-stu-id="0460b-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="0460b-117">添加**ParallelForEach**内的活动**序列**活动。</span><span class="sxs-lookup"><span data-stu-id="0460b-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="0460b-118">输入`comp`并`ComputerName`中的文本框，以便循环，循环访问的元素`ComputerName`数组。</span><span class="sxs-lookup"><span data-stu-id="0460b-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="0460b-119">添加**序列**活动的正文**ParallelForEach**活动。</span><span class="sxs-lookup"><span data-stu-id="0460b-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="0460b-120">设置**DisplayName**到序列的属性`JoinDomain`。</span><span class="sxs-lookup"><span data-stu-id="0460b-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="0460b-121">添加**GetWmiObject**活动**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="0460b-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="0460b-122">编辑的属性**GetWmiObject**活动，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0460b-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="0460b-123">属性</span><span class="sxs-lookup"><span data-stu-id="0460b-123">Property</span></span>|<span data-ttu-id="0460b-124">值</span><span class="sxs-lookup"><span data-stu-id="0460b-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="0460b-125">**类**</span><span class="sxs-lookup"><span data-stu-id="0460b-125">**Class**</span></span>|<span data-ttu-id="0460b-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="0460b-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="0460b-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="0460b-127">**PSComputerName**</span></span>|<span data-ttu-id="0460b-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="0460b-128">{comp}</span></span>|
   |<span data-ttu-id="0460b-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="0460b-129">**PSCredential**</span></span>|<span data-ttu-id="0460b-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="0460b-130">MachineCred</span></span>|

9. <span data-ttu-id="0460b-131">添加**AddComputer**活动**JoinDomain**序列后**GetWmiObject**活动。</span><span class="sxs-lookup"><span data-stu-id="0460b-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="0460b-132">编辑的属性**AddComputer**活动，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0460b-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="0460b-133">属性</span><span class="sxs-lookup"><span data-stu-id="0460b-133">Property</span></span>|<span data-ttu-id="0460b-134">值</span><span class="sxs-lookup"><span data-stu-id="0460b-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="0460b-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="0460b-135">**ComputerName**</span></span>|<span data-ttu-id="0460b-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="0460b-136">{comp}</span></span>|
    |<span data-ttu-id="0460b-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="0460b-137">**DomainCredential**</span></span>|<span data-ttu-id="0460b-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="0460b-138">DomainCred</span></span>|

11. <span data-ttu-id="0460b-139">添加**RestartComputer**活动**JoinDomain**序列后**AddComputer**活动。</span><span class="sxs-lookup"><span data-stu-id="0460b-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="0460b-140">编辑的属性**RestartComputer**活动，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0460b-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="0460b-141">属性</span><span class="sxs-lookup"><span data-stu-id="0460b-141">Property</span></span>|<span data-ttu-id="0460b-142">值</span><span class="sxs-lookup"><span data-stu-id="0460b-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="0460b-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="0460b-143">**ComputerName**</span></span>|<span data-ttu-id="0460b-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="0460b-144">{comp}</span></span>|
    |<span data-ttu-id="0460b-145">**凭据**</span><span class="sxs-lookup"><span data-stu-id="0460b-145">**Credential**</span></span>|<span data-ttu-id="0460b-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="0460b-146">MachineCred</span></span>|
    |<span data-ttu-id="0460b-147">**For**</span><span class="sxs-lookup"><span data-stu-id="0460b-147">**For**</span></span>|<span data-ttu-id="0460b-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="0460b-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="0460b-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="0460b-149">**Force**</span></span>|<span data-ttu-id="0460b-150">True</span><span class="sxs-lookup"><span data-stu-id="0460b-150">True</span></span>|
    |<span data-ttu-id="0460b-151">Wait</span><span class="sxs-lookup"><span data-stu-id="0460b-151">Wait</span></span>|<span data-ttu-id="0460b-152">True</span><span class="sxs-lookup"><span data-stu-id="0460b-152">True</span></span>|
    |<span data-ttu-id="0460b-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="0460b-153">PSComputerName</span></span>|<span data-ttu-id="0460b-154">{""}</span><span class="sxs-lookup"><span data-stu-id="0460b-154">{""}</span></span>|

13. <span data-ttu-id="0460b-155">添加**GetWmiObject**活动**JoinDomain**序列后**RestartComputer**活动。</span><span class="sxs-lookup"><span data-stu-id="0460b-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="0460b-156">编辑其属性与以前相同**GetWmiObject**活动。</span><span class="sxs-lookup"><span data-stu-id="0460b-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="0460b-157">完成这些过程后，工作流设计窗口应如下所示。</span><span class="sxs-lookup"><span data-stu-id="0460b-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="0460b-158">![在工作流设计器中的 JoinDomain XAML](../media/joindomainworkflow.png)
    ![工作流设计器中的 JoinDomain XAML](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="0460b-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>