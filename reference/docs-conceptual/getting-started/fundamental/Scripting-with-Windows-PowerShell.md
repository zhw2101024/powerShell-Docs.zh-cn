---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用 Windows PowerShell 编写脚本"
ms.assetid: c425d27a-bb41-4947-8d73-ba5480bc8ee0
ms.openlocfilehash: 693d1bb9329dbb280453fc16738eda63c466e156
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="scripting-with-windows-powershell"></a><span data-ttu-id="cb8df-103">使用 Windows PowerShell 编写脚本</span><span class="sxs-lookup"><span data-stu-id="cb8df-103">Scripting with Windows PowerShell</span></span>

<span data-ttu-id="cb8df-104">Windows PowerShell® 是基于任务的命令行管理程序和脚本语言，专为进行系统管理而设计。</span><span class="sxs-lookup"><span data-stu-id="cb8df-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="cb8df-105">在 .NET Framework 的基础上构建的 Windows PowerShell 可帮助 IT 专业人士和高级用户控制和自动执行 Windows 操作系统以及在 Windows 上运行的应用程序的管理。</span><span class="sxs-lookup"><span data-stu-id="cb8df-105">Built on the .NET Framework, Windows PowerShell helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="cb8df-106">Windows PowerShell 命令（称为 *cmdlets*）使你可以从命令行管理计算机。</span><span class="sxs-lookup"><span data-stu-id="cb8df-106">Windows PowerShell commands, called *cmdlets*, let you manage the computers from the command line.</span></span> <span data-ttu-id="cb8df-107">Windows PowerShell *提供程序*可让你访问数据存储，如注册表和证书存储，与你访问文件系统一样方便。</span><span class="sxs-lookup"><span data-stu-id="cb8df-107">Windows PowerShell *providers* let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="cb8df-108">此外，Windows PowerShell 还具有丰富的表达式分析器和完全开发的脚本语言。</span><span class="sxs-lookup"><span data-stu-id="cb8df-108">In addition, Windows PowerShell has a rich expression parser and a fully developed scripting language.</span></span>

<span data-ttu-id="cb8df-109">Windows PowerShell 包括以下功能：</span><span class="sxs-lookup"><span data-stu-id="cb8df-109">Windows PowerShell includes the following features:</span></span>

- <span data-ttu-id="cb8df-110">用于执行常见系统管理任务（例如管理注册表、服务、进程和事件日志）和使用 Windows Management Instrumentation (WMI) 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cb8df-110">Cmdlets for performing common system administration tasks, such as managing the registry, services, processes, and event logs, and using Windows Management Instrumentation (WMI).</span></span>
- <span data-ttu-id="cb8df-111">基于任务的脚本语言以及对现有脚本和命令行工具的支持。</span><span class="sxs-lookup"><span data-stu-id="cb8df-111">A task-based scripting language and support for existing scripts and command-line tools.</span></span>
- <span data-ttu-id="cb8df-112">一致的设计。</span><span class="sxs-lookup"><span data-stu-id="cb8df-112">Consistent design.</span></span> <span data-ttu-id="cb8df-113">由于 cmdlet 和系统数据存储使用常见语法和命名约定，因此可以轻松地共享数据并将来自一个 cmdlet 的输出用作对另一个 cmdlet 的输入，而无需重新设置格式或执行操作。</span><span class="sxs-lookup"><span data-stu-id="cb8df-113">Because cmdlets and system data stores use common syntax and naming conventions, data can be shared easily and the output from one cmdlet can be used as the input to another cmdlet without reformatting or manipulation.</span></span>
- <span data-ttu-id="cb8df-114">简化的基于命令的操作系统导航，使用户可以通过使用用于导航文件系统的相同技术来导航注册表和其他数据存储。</span><span class="sxs-lookup"><span data-stu-id="cb8df-114">Simplified, command-based navigation of the operating system, which lets users navigate the registry and other data stores by using the same techniques that they use to navigate the file system.</span></span>
- <span data-ttu-id="cb8df-115">强大的对象操作功能。</span><span class="sxs-lookup"><span data-stu-id="cb8df-115">Powerful object manipulation capabilities.</span></span> <span data-ttu-id="cb8df-116">可直接执行对象操作或将这些对象发送到其他工具或数据库。</span><span class="sxs-lookup"><span data-stu-id="cb8df-116">Objects can be directly manipulated or sent to other tools or databases.</span></span>
- <span data-ttu-id="cb8df-117">可扩展接口。</span><span class="sxs-lookup"><span data-stu-id="cb8df-117">Extensible interface.</span></span> <span data-ttu-id="cb8df-118">独立软件供应商和企业开发人员可以构建用于管理其软件的自定义工具和实用工具。</span><span class="sxs-lookup"><span data-stu-id="cb8df-118">Independent software vendors and enterprise developers can build custom tools and utilities to administer their software.</span></span>

