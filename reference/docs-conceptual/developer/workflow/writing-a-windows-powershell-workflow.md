---
title: 编写 Windows PowerShell 工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366006"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="046b1-102">编写 Windows PowerShell 工作流</span><span class="sxs-lookup"><span data-stu-id="046b1-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="046b1-103">可以通过将 Windows PowerShell 程序集公开的活动添加到 Visual Studio 中的工作流设计器来创建 XAML 工作流。</span><span class="sxs-lookup"><span data-stu-id="046b1-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="046b1-104">以下 Windows PowerShell 程序集公开了支持工作流的活动。</span><span class="sxs-lookup"><span data-stu-id="046b1-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="046b1-105">如果要为工作流提供帮助，则必须将 XAML 工作流打包为模块。</span><span class="sxs-lookup"><span data-stu-id="046b1-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="046b1-106">有关模块的信息，请参阅[编写 Windows PowerShell 模块](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="046b1-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="046b1-107">Microsoft Powershell. Activity</span><span class="sxs-lookup"><span data-stu-id="046b1-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="046b1-108">Microsoft. Core. Activity</span><span class="sxs-lookup"><span data-stu-id="046b1-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="046b1-109">"诊断"。活动</span><span class="sxs-lookup"><span data-stu-id="046b1-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="046b1-110">Microsoft。</span><span class="sxs-lookup"><span data-stu-id="046b1-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="046b1-111">Microsoft。</span><span class="sxs-lookup"><span data-stu-id="046b1-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="046b1-112">Microsoft。</span><span class="sxs-lookup"><span data-stu-id="046b1-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="046b1-113">以下主题介绍如何使用 Windows PowerShell 活动创建工作流。</span><span class="sxs-lookup"><span data-stu-id="046b1-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="046b1-114">将 Windows PowerShell 活动添加到 Visual Studio 工具箱</span><span class="sxs-lookup"><span data-stu-id="046b1-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="046b1-115">使用 Windows PowerShell 活动创建工作流</span><span class="sxs-lookup"><span data-stu-id="046b1-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="046b1-116">使用 Windows PowerShell 脚本创建工作流</span><span class="sxs-lookup"><span data-stu-id="046b1-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="046b1-117">导入和调用 Windows PowerShell 工作流</span><span class="sxs-lookup"><span data-stu-id="046b1-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="046b1-118">通过 Windows PowerShell Cmdlet 创建工作流活动</span><span class="sxs-lookup"><span data-stu-id="046b1-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)