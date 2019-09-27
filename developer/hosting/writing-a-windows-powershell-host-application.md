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
ms.openlocfilehash: b44708b3bbcb974a6178323dff2302b7da121af6
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323501"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="f2c2f-102">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="f2c2f-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="f2c2f-103">可以在应用程序中托管 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="f2c2f-104">主机应用程序可以定义运行命令的运行空间，打开本地或远程计算机上的会话，并根据应用程序的需要以同步或异步方式调用命令。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="f2c2f-105">以下主题介绍如何创建托管 Windows PowerShell 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f2c2f-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="f2c2f-106">In This Section</span></span>

<span data-ttu-id="f2c2f-107">[Windows PowerShell 主机快速入门](./windows-powershell-host-quickstart.md)提供用于帮助您开始创建宿主应用程序的说明和代码示例。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="f2c2f-108">[正在创建运行空间](./creating-runspaces.md)介绍如何在主机应用程序中创建运行 Windows PowerShell 命令的运行空间的一组主题。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="f2c2f-109">[添加和调用命令](./adding-and-invoking-commands.md)说明如何在主机应用程序中创建和运行命令管道。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="f2c2f-110">[创建远程运行空间](./creating-remote-runspaces.md)说明如何将运行空间连接到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="f2c2f-111">[创建自定义用户界面](./creating-a-custom-user-interface.md)介绍自定义用户界面并提供指向示例的链接。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="f2c2f-112">[主机应用程序示例](./host-application-samples.md)本部分包含完整主机应用程序的示例。</span><span class="sxs-lookup"><span data-stu-id="f2c2f-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2c2f-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="f2c2f-113">See Also</span></span>

[<span data-ttu-id="f2c2f-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2c2f-114">Windows PowerShell</span></span>](https://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
