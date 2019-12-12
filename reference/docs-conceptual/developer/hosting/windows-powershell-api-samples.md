---
title: Windows PowerShell API 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360836"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="80bfc-102">Windows PowerShell API 示例</span><span class="sxs-lookup"><span data-stu-id="80bfc-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="80bfc-103">本部分包含的示例代码演示如何创建可限制功能的运行空间，以及如何使用运行空间池来提供运行空间来异步运行命令。</span><span class="sxs-lookup"><span data-stu-id="80bfc-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="80bfc-104">你可以使用 Microsoft Visual Studio 来创建控制台应用程序，然后将此部分中的主题中的代码复制到主机应用程序中。</span><span class="sxs-lookup"><span data-stu-id="80bfc-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="80bfc-105">本部分内容</span><span class="sxs-lookup"><span data-stu-id="80bfc-105">In This Section</span></span>

<span data-ttu-id="80bfc-106">[PowerShell01 示例](./windows-powershell01-sample.md)此示例显示了如何使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象来限制运行空间的功能的。</span><span class="sxs-lookup"><span data-stu-id="80bfc-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="80bfc-107">此示例的输出演示如何限制运行空间的语言模式，如何将 cmdlet 标记为私有，如何添加和删除 cmdlet 和提供程序，如何添加代理命令等。</span><span class="sxs-lookup"><span data-stu-id="80bfc-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="80bfc-108">[PowerShell02 示例](./windows-powershell02-sample.md)此示例演示如何使用运行空间池的运行空间以异步方式运行命令。</span><span class="sxs-lookup"><span data-stu-id="80bfc-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="80bfc-109">此示例生成命令列表，然后运行这些命令，而 Windows PowerShell 引擎在需要时从池中打开运行空间。</span><span class="sxs-lookup"><span data-stu-id="80bfc-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>