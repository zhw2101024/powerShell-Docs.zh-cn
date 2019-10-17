---
title: Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 7627ab336ddc40ab47c3017eed77c78bbdac4e7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366056"
---
# <a name="windows-powershell"></a><span data-ttu-id="97115-102">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="97115-102">Windows PowerShell</span></span>

<span data-ttu-id="97115-103">更新日期：2013年7月8日</span><span class="sxs-lookup"><span data-stu-id="97115-103">Updated: July 8, 2013</span></span>

<span data-ttu-id="97115-104">Windows PowerShell® 是基于任务的命令行管理程序和脚本语言，专为进行系统管理而设计。</span><span class="sxs-lookup"><span data-stu-id="97115-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="97115-105">Windows PowerShell®在 .NET Framework 的基础上构建，可帮助 IT 专业人员和高级用户控制和自动执行 windows 操作系统以及在 Windows 上运行的应用程序的管理。</span><span class="sxs-lookup"><span data-stu-id="97115-105">Built on the .NET Framework, Windows PowerShell® helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="97115-106">此处发布的文档主要针对需要有关 Windows PowerShell 提供的 Api 的参考信息的 cmdlet、提供程序和主机应用程序开发人员编写。</span><span class="sxs-lookup"><span data-stu-id="97115-106">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="97115-107">不过，系统管理员还可能会发现这些文档所提供的信息很有用。</span><span class="sxs-lookup"><span data-stu-id="97115-107">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="97115-108">有关开始使用 Windows PowerShell 所需的基本信息，请参阅使用 Windows PowerShell 入门。</span><span class="sxs-lookup"><span data-stu-id="97115-108">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents-on-msdn"></a><span data-ttu-id="97115-109">MSDN 上的 Windows PowerShell 文档</span><span class="sxs-lookup"><span data-stu-id="97115-109">Windows PowerShell Documents on MSDN</span></span>

- <span data-ttu-id="97115-110">[安装 Windows POWERSHELL SDK](./installing-the-windows-powershell-sdk.md)提供有关如何安装 Windows PowerShell SDK 的信息。</span><span class="sxs-lookup"><span data-stu-id="97115-110">[Installing the Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="97115-111">[编写 Windows PowerShell 模块](./module/writing-a-windows-powershell-module.md)为需要打包和分发其 Windows PowerShell 解决方案的管理员、脚本开发人员和 cmdlet 开发人员提供信息。</span><span class="sxs-lookup"><span data-stu-id="97115-111">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="97115-112">[编写 Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md)提供有关设计和实现 cmdlet 的信息。</span><span class="sxs-lookup"><span data-stu-id="97115-112">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="97115-113">[编写 Windows PowerShell 提供程序](./provider/writing-a-windows-powershell-provider.md)提供有关设计和实现 Windows PowerShell 提供程序的信息。</span><span class="sxs-lookup"><span data-stu-id="97115-113">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="97115-114">它将帮助你了解 Windows PowerShell 提供程序的工作原理，并提供可用于开始设计或编写你自己的提供程序的示例代码。</span><span class="sxs-lookup"><span data-stu-id="97115-114">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="97115-115">[编写 Windows PowerShell 主机应用程序](./hosting/writing-a-windows-powershell-host-application.md)提供可由程序管理员使用的信息，这些程序管理器正在设计宿主应用程序，并由实现它们的开发人员使用。</span><span class="sxs-lookup"><span data-stu-id="97115-115">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="97115-116">主机应用程序可以定义运行命令的运行空间，打开本地或远程计算机上的会话，并根据应用程序的需要以同步或异步方式调用命令。</span><span class="sxs-lookup"><span data-stu-id="97115-116">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="97115-117">[编写 PowerShell 格式化文件](./format/writing-a-powershell-formatting-file.md)提供有关创作格式化文件的信息，这些文件控制由命令返回的对象的显示格式（cmdlet、函数和脚本）。</span><span class="sxs-lookup"><span data-stu-id="97115-117">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="97115-118">[Windows PowerShell 参考](./windows-powershell-reference.md)提供用于编写 cmdlet、提供程序和主机应用程序以及其他支持 Api 的 Api 的参考内容。</span><span class="sxs-lookup"><span data-stu-id="97115-118">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>
