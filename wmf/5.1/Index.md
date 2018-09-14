---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.1 发行说明
ms.openlocfilehash: 3081d200f0c6aac6074719bb1c204900aabf96c2
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522899"
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="ae209-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="ae209-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="ae209-104">WMF 使用户能够将现有的 Windows 系统更新至随 Windows Server 2016 一起发行的 PowerShell、WMI、WinRM 和软件清单日志记录 (SIL) 组件的版本。</span><span class="sxs-lookup"><span data-stu-id="ae209-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="ae209-105">WMF 5.1 可安装在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 和 2012 R2 上，并提供了对 WMF 5.0 RTM 的大量改进，其中包括：</span><span class="sxs-lookup"><span data-stu-id="ae209-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="ae209-106">新 cmdlet：本地用户和组；Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="ae209-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="ae209-107">PowerShellGet 改进包括强制签名模块和安装 JEA 模块</span><span class="sxs-lookup"><span data-stu-id="ae209-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="ae209-108">PackageManagement 增加了对容器、CBS 安装程序、基于 EXE 的安装程序、CAB 包的支持</span><span class="sxs-lookup"><span data-stu-id="ae209-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="ae209-109">DSC 和 PowerShell 类的调试改进</span><span class="sxs-lookup"><span data-stu-id="ae209-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="ae209-110">安全增强包括强制执行来自请求服务器和使用 PowerShellGet cmdlet 时的目录签名模块</span><span class="sxs-lookup"><span data-stu-id="ae209-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="ae209-111">响应大量的用户请求和问题</span><span class="sxs-lookup"><span data-stu-id="ae209-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="ae209-112">若要了解此版本中的新增功能，请浏览[新方案和功能](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features)下列出的主题。</span><span class="sxs-lookup"><span data-stu-id="ae209-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="ae209-113">[安装和配置](https://docs.microsoft.com/powershell/wmf/5.1/install-configure)主题列出了安装和配置的相关要求，并提供 WMF 的安装说明。</span><span class="sxs-lookup"><span data-stu-id="ae209-113">The [Install and Configure](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="ae209-114">[兼容性](https://docs.microsoft.com/powershell/wmf/5.1/compatibility)主题列出了可以在哪些 Windows 版本上安装哪些版本的 WMF。</span><span class="sxs-lookup"><span data-stu-id="ae209-114">The [Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="ae209-115">[产品兼容性](https://docs.microsoft.com/powershell/wmf/5.1/productincompat)主题列出了目前尚未兼容 WMF 5.1 的 Microsoft 应用程序。</span><span class="sxs-lookup"><span data-stu-id="ae209-115">[Product Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="ae209-116">可以在 MSDN 文档中找到 WMF 组件的详细信息：</span><span class="sxs-lookup"><span data-stu-id="ae209-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="ae209-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="ae209-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/powershell/)
- <span data-ttu-id="ae209-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="ae209-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="ae209-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="ae209-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="ae209-120">[软件清单日志记录](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="ae209-120">[Software Inventory Logging](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span></span>
