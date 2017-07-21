---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "安装 Windows PowerShell"
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
ms.openlocfilehash: 2b4cdec52dfc98649a81ab2265a204fcdb0bd8d7
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="71c78-103">安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-103">Installing Windows PowerShell</span></span>
<span data-ttu-id="71c78-104">Windows® 8 和 Windows Server® 2012 包括 Windows PowerShell 3.0 及其所有先决条件。</span><span class="sxs-lookup"><span data-stu-id="71c78-104">Windows® 8 and Windows Server® 2012 include Windows PowerShell 3.0 and all of its prerequisites.</span></span> <span data-ttu-id="71c78-105">系统还包括 Windows PowerShell 2.0 引擎，以实现与不能使用 Windows PowerShell 3.0 的主机程序的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="71c78-105">The system also includes the Windows PowerShell 2.0 engine for backward compatibility with host programs that cannot use Windows PowerShell 3.0.</span></span>

<span data-ttu-id="71c78-106">本主题说明如何在早期系统上安装 Windows PowerShell 3.0，以及安装和启用所需的功能。</span><span class="sxs-lookup"><span data-stu-id="71c78-106">This topic explains how to install Windows PowerShell 3.0 on earlier systems and install and enable the required features.</span></span>

<span data-ttu-id="71c78-107">本主题包含下列部分：</span><span class="sxs-lookup"><span data-stu-id="71c78-107">This topic includes the following sections:</span></span>

-   [<span data-ttu-id="71c78-108">在 Windows 8 和 Windows Server 2012 上安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-108">Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [<span data-ttu-id="71c78-109">在 Windows 7 和 Windows Server 2008 R2 上安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-109">Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [<span data-ttu-id="71c78-110">在 Windows Server 2008 上安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-110">Installing Windows PowerShell on Windows Server 2008</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [<span data-ttu-id="71c78-111">在 Server Core 上安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-111">Installing Windows PowerShell on Server Core</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [<span data-ttu-id="71c78-112">部署 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="71c78-112">Deploying Windows PowerShell Web Access</span></span>](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [<span data-ttu-id="71c78-113">安装 Windows PowerShell 2.0 引擎</span><span class="sxs-lookup"><span data-stu-id="71c78-113">Installing the Windows PowerShell 2.0 Engine</span></span>](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <span data-ttu-id="71c78-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>在 Windows 8 和 Windows Server 2012 上安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>
<span data-ttu-id="71c78-115">Windows PowerShell 3.0 已安装和配置，并可供使用。</span><span class="sxs-lookup"><span data-stu-id="71c78-115">Windows PowerShell 3.0 arrives installed, configured, and ready to use.</span></span> <span data-ttu-id="71c78-116">Windows PowerShell 集成脚本环境 (ISE) 已安装并已启用。</span><span class="sxs-lookup"><span data-stu-id="71c78-116">Windows PowerShell Integrated Scripting Environment (ISE) is installed and enabled.</span></span> <span data-ttu-id="71c78-117">有关启动 Windows PowerShell 的信息，请参阅 [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3)（在 Windows 8 上启动 Windows PowerShell）和 [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell)（在 Windows Server 2012 上启动 Windows PowerShell）。</span><span class="sxs-lookup"><span data-stu-id="71c78-117">For information about starting Windows PowerShell, see [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) and [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell).</span></span>

## <span data-ttu-id="71c78-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>在 Windows 7 和 Windows Server 2008 R2 上安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>
<span data-ttu-id="71c78-119">这些说明解释了如何在运行 Windows 7 Service Pack 1 和 Windows Server 2008 R2 Service Pack 1 的计算机上安装 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-119">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows 7 with Service Pack 1 and Windows Server 2008 R2 with Service Pack 1.</span></span> <span data-ttu-id="71c78-120">下面是适用于运行 Windows Server 2008 R2 的 Server Core 安装选项的计算机的单独安装说明。</span><span class="sxs-lookup"><span data-stu-id="71c78-120">There are separate installation instructions below for computers running with the Server Core installation option of Windows Server 2008 R2.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="71c78-121">正在准备安装</span><span class="sxs-lookup"><span data-stu-id="71c78-121">Getting ready to install</span></span>

-   <span data-ttu-id="71c78-122">安装 Windows Management Framework 3.0 之前，请卸载所有早期版本的 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-122">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="71c78-123">安装 Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="71c78-123">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="71c78-124">从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安装 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完全安装版。</span><span class="sxs-lookup"><span data-stu-id="71c78-124">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="71c78-125">或者，从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安装 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="71c78-125">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

2.  <span data-ttu-id="71c78-126">从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-126">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

<span data-ttu-id="71c78-127">有关启动 Windows PowerShell 3.0 的信息，请参阅[在早期版本的 Windows 上启动 Windows PowerShell](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md)。</span><span class="sxs-lookup"><span data-stu-id="71c78-127">For information about starting Windows PowerShell 3.0, see [Starting Windows PowerShell on Earlier Versions of Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).</span></span>

## <span data-ttu-id="71c78-128"><a name="BKMK_InstallingOnServerCore"></a>在 Server Core 上安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-128"><a name="BKMK_InstallingOnServerCore"></a>Installing Windows PowerShell on Server Core</span></span>
<span data-ttu-id="71c78-129">这些说明解释了如何在运行 Windows Server 2008 R2 Service Pack 1 的 Server Core 安装选项的计算机上安装 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-129">These instructions explain how to install Windows PowerShell 3.0 on computers running the Server Core installation option of Windows Server 2008 R2 with Service Pack 1.</span></span>

<span data-ttu-id="71c78-130">该过程的第一步使用部署映像服务和管理 (DISM) 命令来为 Server Core 和 Windows PowerShell 2.0 安装 Microsoft .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-130">The first steps in the procedure use Deployment Image Servicing and Management (DISM) commands to install Microsoft .NET Framework 2.0 for Server Core and Windows PowerShell 2.0.</span></span> <span data-ttu-id="71c78-131">这些程序是在后续步骤中安装的 Windows Management Framework 3.0 的先决条件。</span><span class="sxs-lookup"><span data-stu-id="71c78-131">These programs are prerequisites for Windows Management Framework 3.0, which is installed in a subsequent step.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="71c78-132">正在准备安装</span><span class="sxs-lookup"><span data-stu-id="71c78-132">Getting ready to install</span></span>

-   <span data-ttu-id="71c78-133">安装 Windows Management Framework 3.0 之前，请卸载所有早期版本的 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-133">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="71c78-134">安装 Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="71c78-134">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="71c78-135">启动 Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="71c78-135">Start Cmd.exe</span></span>

2.  <span data-ttu-id="71c78-136">运行以下 DISM 命令。</span><span class="sxs-lookup"><span data-stu-id="71c78-136">Run the following DISM commands.</span></span> <span data-ttu-id="71c78-137">这些命令用于安装 .NET Framework 2.0 和 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-137">These commands install .NET Framework 2.0 and Windows PowerShell 2.0.</span></span>

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  <span data-ttu-id="71c78-138">从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450) 为服务器核心安装 Microsoft .NET Framework 4.0 的完全安装版。</span><span class="sxs-lookup"><span data-stu-id="71c78-138">Install Microsoft .NET Framework 4.0 full installation for Server Core from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).</span></span>

4.  <span data-ttu-id="71c78-139">从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-139">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <span data-ttu-id="71c78-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>在 Windows Server 2008 上安装 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installing Windows PowerShell on Windows Server 2008</span></span>
<span data-ttu-id="71c78-141">这些说明解释了如何在运行 Windows Server 2008 Service Pack 2 的计算机上安装 Windows PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-141">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows Server 2008 with Service Pack 2.</span></span>

<span data-ttu-id="71c78-142">在 Windows Server 2008 系统上，Windows Management Framework（Windows PowerShell 2.0，KB 968930）是 Windows Management Framework 3.0 的先决条件。</span><span class="sxs-lookup"><span data-stu-id="71c78-142">On Windows Server 2008 systems, Windows Management Framework (Windows PowerShell 2.0, KB 968930) is a prerequisite for Windows Management Framework 3.0.</span></span> <span data-ttu-id="71c78-143">“扩展的身份验证保护”功能可使计算机免受身份验证转发攻击，并允许你在创建远程会话时，使用 **UseSSL** 参数</span><span class="sxs-lookup"><span data-stu-id="71c78-143">The "Extended Protection for Authentication" feature protects the computer from authentication forwarding attacks and allows you to use the **UseSSL** parameter when creating remote sessions.</span></span> <span data-ttu-id="71c78-144">若要安装 Windows PowerShell 3.0 和 Windows PowerShell 2.0 引擎，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="71c78-144">To install Windows PowerShell 3.0 and the Windows PowerShell 2.0 Engine, use the following procedure.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="71c78-145">正在准备安装</span><span class="sxs-lookup"><span data-stu-id="71c78-145">Getting ready to install</span></span>

-   <span data-ttu-id="71c78-146">安装 Windows Management Framework 3.0 之前，请卸载所有早期版本的 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-146">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="71c78-147">安装 Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="71c78-147">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="71c78-148">从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910) 安装具有 Service Pack 1 的 Microsoft .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="71c78-148">Install Microsoft .NET Framework 3.5 with Service Pack 1 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).</span></span>

2.  <span data-ttu-id="71c78-149">从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035) 安装 Windows Management Framework （Windows PowerShell 2.0，KB 968930）。</span><span class="sxs-lookup"><span data-stu-id="71c78-149">Install Windows Management Framework (Windows PowerShell 2.0, KB 968930) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).</span></span>

3.  <span data-ttu-id="71c78-150">从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安装 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完全安装版。</span><span class="sxs-lookup"><span data-stu-id="71c78-150">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="71c78-151">或者，从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安装 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="71c78-151">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

4.  <span data-ttu-id="71c78-152">从 [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398) 安装“扩展的身份验证保护”(KB 968389)。</span><span class="sxs-lookup"><span data-stu-id="71c78-152">Install "Extended Protection for Authentication" (KB 968389) from [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).</span></span>

5.  <span data-ttu-id="71c78-153">从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 Windows Management Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="71c78-153">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <a name="see-also"></a><span data-ttu-id="71c78-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71c78-154">See Also</span></span>
- [<span data-ttu-id="71c78-155">Windows PowerShell 系统要求</span><span class="sxs-lookup"><span data-stu-id="71c78-155">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="71c78-156">启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="71c78-156">Starting Windows PowerShell</span></span>](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

