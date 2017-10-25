---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
title: "WMF 5.1 发行说明"
ms.openlocfilehash: ce9bc7791facfcc2cce9468689e88a26154bda7d
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="691b4-103">Windows Management Framework (WMF) 5.1 发行说明</span><span class="sxs-lookup"><span data-stu-id="691b4-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="691b4-104">WMF 5.1 包括与 Windows Server 2016 一起发行的 PowerShell、WMI、WinRM 以及软件清单日志记录 (SIL) 组件。</span><span class="sxs-lookup"><span data-stu-id="691b4-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="691b4-105">WMF 5.1 可安装在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 和 2012 R2 上，并提供了对 WMF 5.0 RTM 的大量改进，其中包括：</span><span class="sxs-lookup"><span data-stu-id="691b4-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="691b4-106">新 cmdlet：本地用户和组；Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="691b4-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="691b4-107">PowerShellGet 改进包括强制签名模块和安装 JEA 模块</span><span class="sxs-lookup"><span data-stu-id="691b4-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="691b4-108">PackageManagement 增加了对容器、CBS 安装程序、基于 EXE 的安装程序、CAB 包的支持</span><span class="sxs-lookup"><span data-stu-id="691b4-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="691b4-109">DSC 和 PowerShell 类的调试改进</span><span class="sxs-lookup"><span data-stu-id="691b4-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="691b4-110">安全增强包括强制执行来自请求服务器和使用 PowerShellGet cmdlet 时的目录签名模块</span><span class="sxs-lookup"><span data-stu-id="691b4-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="691b4-111">响应大量的用户请求和问题</span><span class="sxs-lookup"><span data-stu-id="691b4-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="691b4-112">**重要说明：**</span><span class="sxs-lookup"><span data-stu-id="691b4-112">**Important notes:**</span></span>

- <span data-ttu-id="691b4-113">WMF 5.1 需要 .NET Framework 4.5.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="691b4-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="691b4-114">安装将成功，但如果未安装 .NET 4.5.2 或更高版本，将无法使用主要功能。</span><span class="sxs-lookup"><span data-stu-id="691b4-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="691b4-115">相关说明请参见[安装和配置 WMF 5.1](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) 主题。</span><span class="sxs-lookup"><span data-stu-id="691b4-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="691b4-116">安装 WMF 5.1 RTM 之前，必须先卸载 WMF 5.1 预览版。</span><span class="sxs-lookup"><span data-stu-id="691b4-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="691b4-117">可在 WMF 5.0 或 WMF 4.0 上直接安装 WMF 5.1。</span><span class="sxs-lookup"><span data-stu-id="691b4-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="691b4-118">在 Windows 7 和 Windows Server 2008 R2 上安装 WMF 5.1 前，无需安装 WMF 4.0。</span><span class="sxs-lookup"><span data-stu-id="691b4-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="691b4-119">它只对 WMF 5.1 预览版本有影响，但已得到解决。</span><span class="sxs-lookup"><span data-stu-id="691b4-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


