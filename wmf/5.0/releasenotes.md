---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: a6366e18b4b6478bfab89475bc6975e6491da9f7
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482856"
---
# <a name="windows-management-framework-wmf-50-rtm-release-notes-overview"></a><span data-ttu-id="a7151-102">Windows Management Framework (WMF) 5.0 RTM 发行说明概述</span><span class="sxs-lookup"><span data-stu-id="a7151-102">Windows Management Framework (WMF) 5.0 RTM Release Notes Overview</span></span>

<span data-ttu-id="a7151-103">**WMF 5.0 已被 WMF 5.1 取代。使用 WMF 5.0 的用户必须升级到 WMF 5.1 才能接受支持。请按照 [WMF 5.1 安装说明](../5.1/install-configure.md)** 进行操作</span><span class="sxs-lookup"><span data-stu-id="a7151-103">**WMF 5.0 is superceeded by WMF 5.1. Users with WMF 5.0 must upgrade to WMF 5.1 to receive support. Please follow the [installation intructions of WMF 5.1](../5.1/install-configure.md)**</span></span>

<span data-ttu-id="a7151-104">Windows Management Framework (WMF) 5.0 RTM 包含已从 WMF 4.0 中更新的功能。</span><span class="sxs-lookup"><span data-stu-id="a7151-104">Windows Management Framework (WMF) 5.0 RTM brings functionality that has been updated from WMF 4.0.</span></span> <span data-ttu-id="a7151-105">WMF 5.0 RTM 仅可在 **Windows Server 2012 R2**、**Windows Server 2012**、**Windows Server 2008 R2**、**Windows 8.1** 和 **Windows 7 SP1** 上进行安装，并包含以下功能的更新版本或说明：</span><span class="sxs-lookup"><span data-stu-id="a7151-105">WMF 5.0 RTM is available for installation only on **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, and **Windows 7 SP1** and contains updated versions or introduction of the following features:</span></span>

- <span data-ttu-id="a7151-106">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7151-106">Windows PowerShell</span></span>
- <span data-ttu-id="a7151-107">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="a7151-107">Just Enough Administration (JEA)</span></span>
- <span data-ttu-id="a7151-108">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="a7151-108">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="a7151-109">Windows PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="a7151-109">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
- <span data-ttu-id="a7151-110">Windows PowerShell Web 服务（Management OData IIS 扩展）</span><span class="sxs-lookup"><span data-stu-id="a7151-110">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="a7151-111">Windows 远程管理 (WinRM)</span><span class="sxs-lookup"><span data-stu-id="a7151-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="a7151-112">Windows 管理规范 (WMI)</span><span class="sxs-lookup"><span data-stu-id="a7151-112">Windows Management Instrumentation (WMI)</span></span>

<span data-ttu-id="a7151-113">WMF 5.0 RTM 替换 [WMF 5.0 产品预览版](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a7151-113">WMF 5.0 RTM replaces the [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span></span> <span data-ttu-id="a7151-114">不必卸载 WMF 5.0 产品预览版便可安装 WMF 5.0 RTM，但在安装 WMF 5.0 RTM 之前你必须卸载所有其他旧版本的 WMF 5.0 预览版。</span><span class="sxs-lookup"><span data-stu-id="a7151-114">You can install WMF 5.0 RTM without uninstalling WMF 5.0 Production Preview, but you must uninstall all other older releases of WMF 5.0 previews before installing the WMF 5.0 RTM.</span></span>

<span data-ttu-id="a7151-115">*注意：* 如果你正在运行 Windows 10，你可以通过更新 Windows 10 的十一月更新版（1511 版本）获取 WMF 5.0 RTM 中可用的相同功能集。</span><span class="sxs-lookup"><span data-stu-id="a7151-115">*Note:* If you are running Windows 10, you can get the same set of functionality available in WMF 5.0 RTM by updating to the November update of Windows 10 (Version 1511).</span></span> <span data-ttu-id="a7151-116">如果你尚未更新 Windows 10 系统，选择“开始”按钮，然后选择“设置”>“更新和安全”>“Windows 更新”>“检查更新”。</span><span class="sxs-lookup"><span data-stu-id="a7151-116">If you have not already updated your Windows 10 system, select the Start button, then select Settings > Update & security > Windows Update > Check for updates.</span></span>
