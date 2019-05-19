---
title: 编写 Windows PowerShell 主机应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 1aaf936aa22af5c4a4b8c2fa4e6b3bbd2cff6d20
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855082"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="ac96b-102">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="ac96b-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="ac96b-103">你可以在应用程序中托管 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ac96b-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="ac96b-104">主机应用程序可以定义命令的运行，打开会话的本地或远程计算机上，并调用以同步方式还是以异步方式取决于应用程序需要的命令的运行空间。</span><span class="sxs-lookup"><span data-stu-id="ac96b-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="ac96b-105">以下主题介绍如何创建托管 Windows PowerShell 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ac96b-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ac96b-106">本部分内容</span><span class="sxs-lookup"><span data-stu-id="ac96b-106">In This Section</span></span>

<span data-ttu-id="ac96b-107">[Windows PowerShell 主机快速入门](./windows-powershell-host-quickstart.md)提供说明和代码示例来帮助你开始创建托管应用程序。</span><span class="sxs-lookup"><span data-stu-id="ac96b-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="ac96b-108">[创建运行空间](./creating-runspaces.md)的主题说明了如何创建主机应用程序中运行 Windows PowerShell 命令的运行空间的一组。</span><span class="sxs-lookup"><span data-stu-id="ac96b-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="ac96b-109">[添加和调用命令](./adding-and-invoking-commands.md)介绍了如何创建和运行命令管道中在主机应用程序...</span><span class="sxs-lookup"><span data-stu-id="ac96b-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="ac96b-110">[创建远程运行空间](./creating-remote-runspaces.md)介绍了如何连接到远程计算机的运行空间。</span><span class="sxs-lookup"><span data-stu-id="ac96b-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="ac96b-111">[创建自定义用户界面](./creating-a-custom-user-interface.md)介绍自定义用户接口，并提供了指向示例。</span><span class="sxs-lookup"><span data-stu-id="ac96b-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="ac96b-112">[主机应用程序示例](./host-application-samples.md)本部分包含的整个主机应用程序示例。</span><span class="sxs-lookup"><span data-stu-id="ac96b-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac96b-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac96b-113">See Also</span></span>

[<span data-ttu-id="ac96b-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac96b-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
