---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "在早期版本的 Windows 上启动 Windows PowerShell"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="80038-103">在早期版本的 Windows 上启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="80038-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="80038-104">本部分介绍了如何在 Windows® 7、Windows Server® 2008 R2 和 Windows Server® 2008 上启动 Windows PowerShell 和 Windows PowerShell 集成脚本环境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="80038-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="80038-105">还介绍了如何在 Windows Server® 2008 R2 和 Windows Server® 2008 上的 Windows PowerShell 2.0 中启用 Windows PowerShell ISE 的可选功能。</span><span class="sxs-lookup"><span data-stu-id="80038-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="80038-106">若要在支持的系统上安装 Windows PowerShell 4.0，请下载并安装 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)。</span><span class="sxs-lookup"><span data-stu-id="80038-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="80038-107">有关详细信息，请参阅[安装 Windows PowerShell](Installing-Windows-PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="80038-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="80038-108">若要在支持的系统上安装 Windows PowerShell 3.0，请下载并安装 [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290)。</span><span class="sxs-lookup"><span data-stu-id="80038-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="80038-109">有关详细信息，请参阅[安装 Windows PowerShell](Installing-Windows-PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="80038-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="80038-110">如何在早期版本的 Windows 上启动 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="80038-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="80038-111">使用以下任一方法来启动已安装的 Windows PowerShell 3.0 或 Windows PowerShell 4.0 版本（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="80038-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="80038-112">在“开始”菜单中</span><span class="sxs-lookup"><span data-stu-id="80038-112">From the Start Menu</span></span>

-   <span data-ttu-id="80038-113">单击“开始”，键入 **PowerShell**，然后单击“Windows PowerShell”。</span><span class="sxs-lookup"><span data-stu-id="80038-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

-   <span data-ttu-id="80038-114">在“开始”菜单中，依次单击“开始”、“所有程序”、“附件”、“Windows PowerShell”文件夹，然后单击“Windows PowerShell”。</span><span class="sxs-lookup"><span data-stu-id="80038-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="80038-115">在命令提示符处</span><span class="sxs-lookup"><span data-stu-id="80038-115">At the Command Prompt</span></span>

-   <span data-ttu-id="80038-116">在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入：</span><span class="sxs-lookup"><span data-stu-id="80038-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="80038-117">你还可以使用 PowerShell.exe 程序的参数来自定义会话。</span><span class="sxs-lookup"><span data-stu-id="80038-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="80038-118">有关详细信息，请参阅 [PowerShell.exe 命令行帮助](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)。</span><span class="sxs-lookup"><span data-stu-id="80038-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="80038-119">使用管理权限（“以管理员身份运行”）</span><span class="sxs-lookup"><span data-stu-id="80038-119">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="80038-120">单击“**开始**”，键入 **PowerShell**，右键单击“**Windows PowerShell**”，然后单击“**以管理员身份运行**”。</span><span class="sxs-lookup"><span data-stu-id="80038-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="80038-121">如何在早期版本的 Windows 上启动 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="80038-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="80038-122">使用以下任一方法启动 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="80038-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="80038-123">在“开始”菜单中</span><span class="sxs-lookup"><span data-stu-id="80038-123">From the Start Menu</span></span>

-   <span data-ttu-id="80038-124">单击“开始”，键入 **ISE**，然后单击“Windows PowerShell ISE”。</span><span class="sxs-lookup"><span data-stu-id="80038-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

-   <span data-ttu-id="80038-125">在“开始”菜单中，依次单击“开始”、“所有程序”、“附件”、“Windows PowerShell”文件夹，然后单击“Windows PowerShell ISE”。</span><span class="sxs-lookup"><span data-stu-id="80038-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="80038-126">在命令提示符处</span><span class="sxs-lookup"><span data-stu-id="80038-126">At the Command Prompt</span></span>

-   <span data-ttu-id="80038-127">在 Cmd.exe、Windows PowerShell 或 Windows PowerShell ISE 中，若要启动 Windows PowerShell，请键入：</span><span class="sxs-lookup"><span data-stu-id="80038-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="80038-128">或</span><span class="sxs-lookup"><span data-stu-id="80038-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="80038-129">使用管理权限（“以管理员身份运行”）</span><span class="sxs-lookup"><span data-stu-id="80038-129">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="80038-130">单击“**开始**”，键入 **ISE**，右键单击“**Windows PowerShell ISE**”，然后单击“**以管理员身份运行**”。</span><span class="sxs-lookup"><span data-stu-id="80038-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="80038-131">如何在早期版本的 Windows 上启用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="80038-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="80038-132">在 Windows PowerShell 4.0 和 Windows PowerShell 3.0 中，默认情况下，所有版本的 Windows 上都启用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="80038-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="80038-133">如果尚未启用，则 Windows Management Framework 4.0 或 Windows Management Framework 3.0 会启用它。</span><span class="sxs-lookup"><span data-stu-id="80038-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="80038-134">在 Windows PowerShell 2.0 中，默认情况下，在 Windows 7 上启用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="80038-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="80038-135">但是，在 Windows Server 2008 R2 和 Windows Server 2008 上，它是一项可选功能。</span><span class="sxs-lookup"><span data-stu-id="80038-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="80038-136">若要启用 Windows Server 2008 R2 或 Windows Server 2008 上的 Windows PowerShell 2.0 中的 Windows PowerShell ISE，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="80038-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="80038-137">启用 Windows PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="80038-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1.  <span data-ttu-id="80038-138">启动“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="80038-138">Start Server Manager.</span></span>

2.  <span data-ttu-id="80038-139">单击“功能”，然后单击“添加功能”。</span><span class="sxs-lookup"><span data-stu-id="80038-139">Click **Features** and then click **Add Features**.</span></span>

3.  <span data-ttu-id="80038-140">在“选择功能”中，单击“Windows PowerShell 集成脚本环境 (ISE)”</span><span class="sxs-lookup"><span data-stu-id="80038-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

