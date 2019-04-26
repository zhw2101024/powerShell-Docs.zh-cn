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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080469"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="72749-102">向 Visual Studio 工具箱添加 Windows PowerShell 活动</span><span class="sxs-lookup"><span data-stu-id="72749-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="72749-103">创作使用工作流设计器的 PowerShell 工作流之前，首先必须将 PowerShell 活动添加到 Visual Studio 工作流控制台应用程序项目中的工具箱中。</span><span class="sxs-lookup"><span data-stu-id="72749-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="72749-104">以下过程说明如何将活动从 Microsoft.PowerShell.Core.Activities 程序集添加到 Visual Studio 工具箱。</span><span class="sxs-lookup"><span data-stu-id="72749-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="72749-105">将 Windows PowerShell 活动添加到工具箱</span><span class="sxs-lookup"><span data-stu-id="72749-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="72749-106">在 Visual Studio 中创建新的工作流控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="72749-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="72749-107">上**视图**菜单上，单击**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="72749-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="72749-108">通过在此工具箱内右键单击并单击工具箱中添加一个新选项卡**添加选项卡**，并提供一个名称，例如"PowerShell 活动"的新选项卡。</span><span class="sxs-lookup"><span data-stu-id="72749-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="72749-109">添加选项卡可以分组 PowerShell 活动单独从工具箱中的其他工具。</span><span class="sxs-lookup"><span data-stu-id="72749-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="72749-110">在新的工具箱选项卡上，单击**选择项...**.**选择工具箱项**此时将显示对话框。</span><span class="sxs-lookup"><span data-stu-id="72749-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="72749-111">在中**选择工具箱项**对话框中，单击**System.Activities**选项卡。</span><span class="sxs-lookup"><span data-stu-id="72749-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="72749-112">单击**浏览**。</span><span class="sxs-lookup"><span data-stu-id="72749-112">Click **Browse**.</span></span>

7. <span data-ttu-id="72749-113">导航到 %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e 文件夹并双击 Microsoft.PowerShell.Core.Activities.dll。</span><span class="sxs-lookup"><span data-stu-id="72749-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="72749-114">单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="72749-114">Click **OK**.</span></span> <span data-ttu-id="72749-115">定义由 Microsoft.PowerShell.Core.Activities 程序集的活动现可在工具箱中。</span><span class="sxs-lookup"><span data-stu-id="72749-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="72749-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72749-116">See Also</span></span>

[<span data-ttu-id="72749-117">编写 Windows PowerShell 工作流</span><span class="sxs-lookup"><span data-stu-id="72749-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="72749-118">使用 Windows PowerShell 活动创建工作流</span><span class="sxs-lookup"><span data-stu-id="72749-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)