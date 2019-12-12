---
title: 将 Windows PowerShell 活动添加到 Visual Studio 工具箱 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359646"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="4b1f4-102">向 Visual Studio 工具箱添加 Windows PowerShell 活动</span><span class="sxs-lookup"><span data-stu-id="4b1f4-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="4b1f4-103">使用工作流设计器创作 PowerShell 工作流之前，必须先将 PowerShell 活动添加到 Visual Studio 工作流控制台应用程序项目中的 "工具箱"。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="4b1f4-104">下面的过程演示如何将活动从 Microsoft. Core 程序集添加到 Visual Studio 工具箱。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="4b1f4-105">将 Windows PowerShell 活动添加到工具箱</span><span class="sxs-lookup"><span data-stu-id="4b1f4-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="4b1f4-106">在 Visual Studio 中创建新的工作流控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="4b1f4-107">在“视图”菜单上，单击“工具箱”。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="4b1f4-108">右键单击 "工具箱"，然后单击 "**添加选项卡**"，并为新选项卡指定一个名称，如 "PowerShell 活动"，从而在 "工具箱" 中添加新选项卡。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="4b1f4-109">通过添加选项卡，可以将 PowerShell 活动与 "工具箱" 中的其他工具进行分组。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="4b1f4-110">在 "新建工具箱" 选项卡上，单击 "**选择项 ...** "。此时将显示 "**选择工具箱项**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="4b1f4-111">在 "**选择工具箱项**" 对话框中，单击 "**系统**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="4b1f4-112">单击**浏览**。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-112">Click **Browse**.</span></span>

7. <span data-ttu-id="4b1f4-113">导航到%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0. 0__31bf3856ad364e 文件夹，然后双击 ""。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="4b1f4-114">单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-114">Click **OK**.</span></span> <span data-ttu-id="4b1f4-115">现在，"工具箱" 中提供了由 "Microsoft. Core" 程序集定义的活动。</span><span class="sxs-lookup"><span data-stu-id="4b1f4-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b1f4-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b1f4-116">See Also</span></span>

[<span data-ttu-id="4b1f4-117">编写 Windows PowerShell 工作流</span><span class="sxs-lookup"><span data-stu-id="4b1f4-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="4b1f4-118">使用 Windows PowerShell 活动创建工作流</span><span class="sxs-lookup"><span data-stu-id="4b1f4-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)