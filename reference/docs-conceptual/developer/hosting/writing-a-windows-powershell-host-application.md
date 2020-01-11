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
ms.openlocfilehash: fe0393634a1e5bb1a3d4a98ccf245e199beb0f16
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869905"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="e9ab5-102">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="e9ab5-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="e9ab5-103">可以在应用程序中托管 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="e9ab5-104">主机应用程序可以定义运行命令的运行空间，打开本地或远程计算机上的会话，并根据应用程序的需要以同步或异步方式调用命令。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="e9ab5-105">以下主题介绍如何创建托管 Windows PowerShell 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e9ab5-106">本部分内容</span><span class="sxs-lookup"><span data-stu-id="e9ab5-106">In This Section</span></span>

<span data-ttu-id="e9ab5-107">[Windows PowerShell 主机快速入门](./windows-powershell-host-quickstart.md)提供用于帮助您开始创建宿主应用程序的说明和代码示例。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="e9ab5-108">[正在创建运行空间](./creating-runspaces.md)介绍如何在主机应用程序中创建运行 Windows PowerShell 命令的运行空间的一组主题。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="e9ab5-109">[添加和调用命令](./adding-and-invoking-commands.md)说明如何在主机应用程序中创建和运行命令管道。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="e9ab5-110">[创建远程运行空间](./creating-remote-runspaces.md)说明如何将运行空间连接到远程计算机。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="e9ab5-111">[创建自定义用户界面](./creating-a-custom-user-interface.md)介绍自定义用户界面并提供指向示例的链接。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="e9ab5-112">[主机应用程序示例](./host-application-samples.md)本部分包含完整主机应用程序的示例。</span><span class="sxs-lookup"><span data-stu-id="e9ab5-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>
