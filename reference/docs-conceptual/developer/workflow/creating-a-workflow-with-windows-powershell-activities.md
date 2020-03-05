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
ms.openlocfilehash: 7d399786b9b43ee302493359d9702981045212e9
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78277452"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="efdff-102">创建具有 Windows PowerShell 活动的工作流</span><span class="sxs-lookup"><span data-stu-id="efdff-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="efdff-103">可以通过从 Visual Studio "工具箱" 中选择 "活动" 并将其拖到 "工作流设计器" 窗口中来创建 Windows PowerShell 工作流。</span><span class="sxs-lookup"><span data-stu-id="efdff-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="efdff-104">有关将 Windows PowerShell 活动添加到 Visual Studio 工具箱中的信息，请参阅[将 Windows Powershell 活动添加到 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="efdff-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="efdff-105">下面的过程介绍如何创建一个工作流，用于检查一组用户指定计算机的域状态，将这些计算机加入域（如果尚未加入域），然后再次检查状态。</span><span class="sxs-lookup"><span data-stu-id="efdff-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="efdff-106">设置项目</span><span class="sxs-lookup"><span data-stu-id="efdff-106">Setting up the Project</span></span>

1. <span data-ttu-id="efdff-107">按照[将 Windows PowerShell 活动添加到 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)中的过程，创建一个工作流项目，并将这些活动从 " [microsoft](/dotnet/api/Microsoft.PowerShell.Activities) " 和 " [microsoft. 管理](/dotnet/api/Microsoft.PowerShell.Management.Activities)" 程序集添加到 "工具箱"。</span><span class="sxs-lookup"><span data-stu-id="efdff-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="efdff-108">将 System.object 作为引用程序集添加到项目中，以作为引用程序集的作为项目的 "管理"、"microsoft"、"管理" 和 "microsoft"。</span><span class="sxs-lookup"><span data-stu-id="efdff-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="efdff-109">向工作流添加活动</span><span class="sxs-lookup"><span data-stu-id="efdff-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="efdff-110">向工作流添加**序列**活动。</span><span class="sxs-lookup"><span data-stu-id="efdff-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="efdff-111">创建一个名为 `ComputerName` 的参数，参数类型为 `String[]`。</span><span class="sxs-lookup"><span data-stu-id="efdff-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="efdff-112">此参数表示要检查和加入的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="efdff-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="efdff-113">创建一个名为的参数，该参数[的类型为 `DomainCred`。](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="efdff-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="efdff-114">此参数表示有权将计算机加入域的域帐户的域凭据。</span><span class="sxs-lookup"><span data-stu-id="efdff-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="efdff-115">创建一个名为的参数，该参数[的类型为 `MachineCred`。](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="efdff-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="efdff-116">此参数表示要检查和加入计算机上的管理员的凭据。</span><span class="sxs-lookup"><span data-stu-id="efdff-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="efdff-117">添加 "**序列**" 活动中的**ParallelForEach**活动。</span><span class="sxs-lookup"><span data-stu-id="efdff-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="efdff-118">在文本框中输入 `comp` 和 `ComputerName`，以便循环遍历 `ComputerName` 数组的元素。</span><span class="sxs-lookup"><span data-stu-id="efdff-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="efdff-119">将 "**序列**" 活动添加到 " **ParallelForEach** " 活动的正文中。</span><span class="sxs-lookup"><span data-stu-id="efdff-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="efdff-120">将序列的**DisplayName**属性设置为 `JoinDomain`。</span><span class="sxs-lookup"><span data-stu-id="efdff-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="efdff-121">将**GetWmiObject**活动添加到**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="efdff-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="efdff-122">按如下所示编辑 " **GetWmiObject** " 活动的属性。</span><span class="sxs-lookup"><span data-stu-id="efdff-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="efdff-123">属性</span><span class="sxs-lookup"><span data-stu-id="efdff-123">Property</span></span>|<span data-ttu-id="efdff-124">值</span><span class="sxs-lookup"><span data-stu-id="efdff-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="efdff-125">**类**</span><span class="sxs-lookup"><span data-stu-id="efdff-125">**Class**</span></span>|<span data-ttu-id="efdff-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="efdff-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="efdff-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="efdff-127">**PSComputerName**</span></span>|<span data-ttu-id="efdff-128">压缩</span><span class="sxs-lookup"><span data-stu-id="efdff-128">{comp}</span></span>|
   |<span data-ttu-id="efdff-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="efdff-129">**PSCredential**</span></span>|<span data-ttu-id="efdff-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="efdff-130">MachineCred</span></span>|

9. <span data-ttu-id="efdff-131">在**GetWmiObject**活动后，将**AddComputer**活动添加到**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="efdff-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="efdff-132">按如下所示编辑 " **AddComputer** " 活动的属性。</span><span class="sxs-lookup"><span data-stu-id="efdff-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="efdff-133">属性</span><span class="sxs-lookup"><span data-stu-id="efdff-133">Property</span></span>|<span data-ttu-id="efdff-134">值</span><span class="sxs-lookup"><span data-stu-id="efdff-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="efdff-135">**计算机名**</span><span class="sxs-lookup"><span data-stu-id="efdff-135">**ComputerName**</span></span>|<span data-ttu-id="efdff-136">压缩</span><span class="sxs-lookup"><span data-stu-id="efdff-136">{comp}</span></span>|
    |<span data-ttu-id="efdff-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="efdff-137">**DomainCredential**</span></span>|<span data-ttu-id="efdff-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="efdff-138">DomainCred</span></span>|

11. <span data-ttu-id="efdff-139">在**AddComputer**活动后，将**RestartComputer**活动添加到**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="efdff-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="efdff-140">按如下所示编辑 " **RestartComputer** " 活动的属性。</span><span class="sxs-lookup"><span data-stu-id="efdff-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="efdff-141">属性</span><span class="sxs-lookup"><span data-stu-id="efdff-141">Property</span></span>|<span data-ttu-id="efdff-142">值</span><span class="sxs-lookup"><span data-stu-id="efdff-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="efdff-143">**计算机名**</span><span class="sxs-lookup"><span data-stu-id="efdff-143">**ComputerName**</span></span>|<span data-ttu-id="efdff-144">压缩</span><span class="sxs-lookup"><span data-stu-id="efdff-144">{comp}</span></span>|
    |<span data-ttu-id="efdff-145">**凭据**</span><span class="sxs-lookup"><span data-stu-id="efdff-145">**Credential**</span></span>|<span data-ttu-id="efdff-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="efdff-146">MachineCred</span></span>|
    |<span data-ttu-id="efdff-147">**进行**</span><span class="sxs-lookup"><span data-stu-id="efdff-147">**For**</span></span>|<span data-ttu-id="efdff-148">WaitForServiceTypes （PowerShell）</span><span class="sxs-lookup"><span data-stu-id="efdff-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="efdff-149">**团队**</span><span class="sxs-lookup"><span data-stu-id="efdff-149">**Force**</span></span>|<span data-ttu-id="efdff-150">True</span><span class="sxs-lookup"><span data-stu-id="efdff-150">True</span></span>|
    |<span data-ttu-id="efdff-151">Wait</span><span class="sxs-lookup"><span data-stu-id="efdff-151">Wait</span></span>|<span data-ttu-id="efdff-152">True</span><span class="sxs-lookup"><span data-stu-id="efdff-152">True</span></span>|
    |<span data-ttu-id="efdff-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="efdff-153">PSComputerName</span></span>|<span data-ttu-id="efdff-154">{""}</span><span class="sxs-lookup"><span data-stu-id="efdff-154">{""}</span></span>|

13. <span data-ttu-id="efdff-155">在**RestartComputer**活动后，将**GetWmiObject**活动添加到**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="efdff-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="efdff-156">编辑其属性，使其与之前的**GetWmiObject**活动相同。</span><span class="sxs-lookup"><span data-stu-id="efdff-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="efdff-157">完成这些过程后，工作流设计窗口应如下所示。</span><span class="sxs-lookup"><span data-stu-id="efdff-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="efdff-158">![工作流设计器中的 JoinDomain XAML](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
    ![工作流设计器中的 JOINDOMAIN xaml](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="efdff-158">![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span></span>