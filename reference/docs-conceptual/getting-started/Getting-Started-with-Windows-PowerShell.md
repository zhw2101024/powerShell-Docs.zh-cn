---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 入门
ms.assetid: b0e2ad92-875f-421d-b612-f624e644aa69
ms.openlocfilehash: d8f1a416c1618040311ec0ea3b98b28aa432bcf1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="getting-started-with-windows-powershell"></a><span data-ttu-id="0d70e-103">Windows PowerShell 入门</span><span class="sxs-lookup"><span data-stu-id="0d70e-103">Getting Started with Windows PowerShell</span></span>
<span data-ttu-id="0d70e-104">Windows PowerShell 是专门为系统管理员设计的 Windows 命令行 Shell。</span><span class="sxs-lookup"><span data-stu-id="0d70e-104">Windows PowerShell is a Windows command-line shell designed especially for system administrators.</span></span> <span data-ttu-id="0d70e-105">Windows PowerShell 包括可以单独或组合使用的交互提示和脚本编写环境。</span><span class="sxs-lookup"><span data-stu-id="0d70e-105">Windows PowerShell includes an interactive prompt and a scripting environment that can be used independently or in combination.</span></span>

<span data-ttu-id="0d70e-106">与大多数 Shell（它们接受和返回文本）不同，Windows PowerShell 是在 .NET Framework 公共语言运行时 (CLR) 和.NET Framework 的基础上生成的，它将接受和返回 .NET Framework 对象。</span><span class="sxs-lookup"><span data-stu-id="0d70e-106">Unlike most shells, which accept and return text, Windows PowerShell is built on top of the .NET Framework common language runtime (CLR) and the .NET Framework, and accepts and returns .NET Framework objects.</span></span> <span data-ttu-id="0d70e-107">环境中的这一基本更改为 Windows 的管理和配置带来了全新的工具和方法。</span><span class="sxs-lookup"><span data-stu-id="0d70e-107">This fundamental change in the environment brings entirely new tools and methods to the management and configuration of Windows.</span></span>

<span data-ttu-id="0d70e-108">Windows PowerShell 引入了 cmdlet（读作“command-let”）的概念，它是内置于 Shell 的简单的单一函数命令行工具。</span><span class="sxs-lookup"><span data-stu-id="0d70e-108">Windows PowerShell introduces the concept of a cmdlet (pronounced "command-let"), a simple, single-function command-line tool built into the shell.</span></span> <span data-ttu-id="0d70e-109">可以分别使用每个 cmdlet，但只有组合使用这些简单的工具来执行复杂的任务时，你才会意识到它们的强大功能。</span><span class="sxs-lookup"><span data-stu-id="0d70e-109">You can use each cmdlet separately, but their power is realized when you use these simple tools in combination to perform complex tasks.</span></span> <span data-ttu-id="0d70e-110">Windows PowerShell 包括一百多个基本核心 cmdlet，你可以编写自己的 cmdlet 并与其他用户共享。</span><span class="sxs-lookup"><span data-stu-id="0d70e-110">Windows PowerShell includes more than one hundred basic core cmdlets, and you can write your own cmdlets and share them with other users.</span></span>

<span data-ttu-id="0d70e-111">与许多 Shell 类似，Windows PowerShell 允许你访问计算机上的文件系统。</span><span class="sxs-lookup"><span data-stu-id="0d70e-111">Like many shells, Windows PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="0d70e-112">此外，Windows PowerShell *提供程序*使你能够像访问文件系统一样方便地访问其他数据存储（例如注册表和数字签名证书存储）。</span><span class="sxs-lookup"><span data-stu-id="0d70e-112">In addition, Windows PowerShell *providers* enable you to access other data stores, such as the registry and the digital signature certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="0d70e-113">本入门指南提供对 Windows PowerShell 的介绍：包括语言、cmdlet、提供程序，以及对象的使用。</span><span class="sxs-lookup"><span data-stu-id="0d70e-113">This Getting Started guide provides an introduction to Windows PowerShell: the language, the cmdlets, the providers, and the use of objects.</span></span>

<span data-ttu-id="0d70e-114">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="0d70e-114">In this topic:</span></span>

- [<span data-ttu-id="0d70e-115">Windows PowerShell 系统要求</span><span class="sxs-lookup"><span data-stu-id="0d70e-115">Windows PowerShell System Requirements</span></span>](../setup/Windows-PowerShell-System-Requirements.md)

- [<span data-ttu-id="0d70e-116">安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d70e-116">Installing Windows PowerShell</span></span>](../setup/Installing-Windows-PowerShell.md)

- [<span data-ttu-id="0d70e-117">启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d70e-117">Starting Windows PowerShell</span></span>](../setup/Starting-Windows-PowerShell.md)

- [<span data-ttu-id="0d70e-118">准备好使用 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d70e-118">Getting Ready to Use Windows PowerShell</span></span>](Getting-Ready-to-Use-Windows-PowerShell.md)