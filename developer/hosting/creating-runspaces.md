---
title: 创建运行空间 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082934"
---
# <a name="creating-runspaces"></a><span data-ttu-id="d7cc7-102">创建运行空间</span><span class="sxs-lookup"><span data-stu-id="d7cc7-102">Creating Runspaces</span></span>

<span data-ttu-id="d7cc7-103">在运行空间是由主机应用程序调用的命令的操作环境。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="d7cc7-104">此环境包含命令和当前存在的数据和当前应用任何语言限制。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="d7cc7-105">主机应用程序可以使用默认的运行空间提供的 Windows PowerShell 中，其中包括所有可用的核心命令，或创建自定义的运行空间，包括可用命令的一个子集。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="d7cc7-106">若要创建的自定义的运行空间，您创建[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，并将其分配给你的运行空间。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="d7cc7-107">运行空间任务</span><span class="sxs-lookup"><span data-stu-id="d7cc7-107">Runspace tasks</span></span>

1. [<span data-ttu-id="d7cc7-108">创建 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="d7cc7-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="d7cc7-109">创建受限运行空间</span><span class="sxs-lookup"><span data-stu-id="d7cc7-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="d7cc7-110">创建多个运行空间</span><span class="sxs-lookup"><span data-stu-id="d7cc7-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="d7cc7-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7cc7-111">See Also</span></span>
