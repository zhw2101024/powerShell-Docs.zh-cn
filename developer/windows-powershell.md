---
title: Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 7627ab336ddc40ab47c3017eed77c78bbdac4e7f
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470809"
---
# <a name="windows-powershell"></a><span data-ttu-id="2ff85-102">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ff85-102">Windows PowerShell</span></span>

<span data-ttu-id="2ff85-103">更新时间：2013 年 7 月 8日日</span><span class="sxs-lookup"><span data-stu-id="2ff85-103">Updated: July 8, 2013</span></span>

<span data-ttu-id="2ff85-104">Windows PowerShell® 是基于任务的命令行管理程序和脚本语言，专为进行系统管理而设计。</span><span class="sxs-lookup"><span data-stu-id="2ff85-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="2ff85-105">.NET Framework 上构建，Windows PowerShell® 可帮助 IT 专业人员和高级用户控制和自动进行管理的 Windows 操作系统和在 Windows 运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="2ff85-105">Built on the .NET Framework, Windows PowerShell® helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="2ff85-106">此处发布的文档主要面向 cmdlet、 提供商和主机应用程序开发人员需要有关 Windows PowerShell 提供的 Api 的参考信息。</span><span class="sxs-lookup"><span data-stu-id="2ff85-106">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="2ff85-107">但是，系统管理员可能还会发现这些有用的文档提供的信息。</span><span class="sxs-lookup"><span data-stu-id="2ff85-107">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="2ff85-108">开始使用 Windows PowerShell 所需的基本信息，请参阅 Windows PowerShell 入门。</span><span class="sxs-lookup"><span data-stu-id="2ff85-108">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents-on-msdn"></a><span data-ttu-id="2ff85-109">MSDN 上的 Windows PowerShell 文档</span><span class="sxs-lookup"><span data-stu-id="2ff85-109">Windows PowerShell Documents on MSDN</span></span>

- <span data-ttu-id="2ff85-110">[安装 Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md)提供有关如何安装 Windows PowerShell SDK 的信息。</span><span class="sxs-lookup"><span data-stu-id="2ff85-110">[Installing the Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="2ff85-111">[编写 Windows PowerShell 模块](./module/writing-a-windows-powershell-module.md)管理员、 脚本开发人员和 cmdlet 的开发人员需要打包并分发其 Windows PowerShell 解决方案提供的信息。</span><span class="sxs-lookup"><span data-stu-id="2ff85-111">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="2ff85-112">[编写 Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md)提供设计和实现 cmdlet 的信息。</span><span class="sxs-lookup"><span data-stu-id="2ff85-112">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="2ff85-113">[编写 Windows PowerShell 提供程序](./provider/writing-a-windows-powershell-provider.md)提供设计和实现 Windows PowerShell 提供程序的信息。</span><span class="sxs-lookup"><span data-stu-id="2ff85-113">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="2ff85-114">它将帮助你了解 Windows PowerShell 提供程序的工作，并且它提供了可用于启动设计或编写自己的提供程序的示例代码。</span><span class="sxs-lookup"><span data-stu-id="2ff85-114">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="2ff85-115">[编写一个 Windows PowerShell 主机应用程序](./hosting/writing-a-windows-powershell-host-application.md)提供可以通过设计主机应用程序的程序经理和开发人员实现其使用的信息。</span><span class="sxs-lookup"><span data-stu-id="2ff85-115">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="2ff85-116">主机应用程序可以、 定义命令所在的本地或远程计算机上，运行，请打开会话的运行空间和调用以同步方式还是以异步方式取决于应用程序需要的命令。</span><span class="sxs-lookup"><span data-stu-id="2ff85-116">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="2ff85-117">[编写 PowerShell 格式设置文件](./format/writing-a-powershell-formatting-file.md)提供用于控制返回的命令 （cmdlet、 函数和脚本） 的对象的显示格式的格式设置文件的创作的信息。</span><span class="sxs-lookup"><span data-stu-id="2ff85-117">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="2ff85-118">[Windows PowerShell 参考](./windows-powershell-reference.md)提供中编写 cmdlet、 提供商和托管应用程序，使用的 Api，以及其他支持的 Api 的参考内容。</span><span class="sxs-lookup"><span data-stu-id="2ff85-118">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>
