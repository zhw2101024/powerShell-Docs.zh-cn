---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 卸载 Windows PowerShell Web 访问
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058129"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="42bb6-103">卸载 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="42bb6-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="42bb6-104">更新时间：2013 年 6 月 24 日</span><span class="sxs-lookup"><span data-stu-id="42bb6-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="42bb6-105">适用于：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="42bb6-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="42bb6-106">本主题中的步骤说明了如何从已安装 Windows PowerShell Web 访问网站的网关服务器中删除该网站及其应用程序。</span><span class="sxs-lookup"><span data-stu-id="42bb6-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="42bb6-107">通知用户</span><span class="sxs-lookup"><span data-stu-id="42bb6-107">Notify users</span></span>

<span data-ttu-id="42bb6-108">开始前，先通知基于 Web 控制台的用户，你准备删除网站。</span><span class="sxs-lookup"><span data-stu-id="42bb6-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="42bb6-109">卸载 Windows PowerShell Web 访问并不卸载 IIS 或任何其他自动安装的功能，因为 Windows PowerShell Web 访问需要它们处于运行状态。</span><span class="sxs-lookup"><span data-stu-id="42bb6-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="42bb6-110">卸载过程保留了依赖 Windows PowerShell Web 访问的功能；必要时你可以单独卸载那些功能。</span><span class="sxs-lookup"><span data-stu-id="42bb6-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="42bb6-111">建议（快速）卸载</span><span class="sxs-lookup"><span data-stu-id="42bb6-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="42bb6-112">本部分内容可帮助你卸载以下内容：</span><span class="sxs-lookup"><span data-stu-id="42bb6-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="42bb6-113">Windows PowerShell Web 访问 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="42bb6-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="42bb6-114">Windows PowerShell Web 访问功能</span><span class="sxs-lookup"><span data-stu-id="42bb6-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="42bb6-115">方法是使用 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="42bb6-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="42bb6-116">步骤 1：使用 cmdlet 删除 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="42bb6-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="42bb6-117">执行以下操作之一，打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="42bb6-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="42bb6-118">在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="42bb6-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="42bb6-119">在 Windows **开始**屏幕上，单击**Windows PowerShell**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="42bb6-120">键入 `Uninstall-PswaWebApplication`，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="42bb6-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="42bb6-121">如果指定了自己的自定义网站名称，请将 `-WebsiteName` 参数添加到命令中，并指定网站名称。</span><span class="sxs-lookup"><span data-stu-id="42bb6-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="42bb6-122">如果使用了自定义 Web 应用程序（不是默认应用程序 pswa），请将 `-WebApplicationName` 参数添加到命令中，并指定 Web 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="42bb6-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="42bb6-123">如果你使用的是测试证书，则将 `DeleteTestCertificate` 参数添加到 cmdlet（如以下示例所述）。</span><span class="sxs-lookup"><span data-stu-id="42bb6-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="42bb6-124">步骤 2：使用 cmdlet 卸载 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="42bb6-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="42bb6-125">使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="42bb6-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="42bb6-126">如果会话已经打开，则继续执行下一步。</span><span class="sxs-lookup"><span data-stu-id="42bb6-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="42bb6-127">在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="42bb6-128">在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="42bb6-129">键入以下内容，然后按 **Enter**，其中的 *computer_name* 代表要从中删除 Windows PowerShell Web 访问的远程服务器。</span><span class="sxs-lookup"><span data-stu-id="42bb6-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="42bb6-130">如果在删除过程中有必要，则 `-Restart` 参数将自动重新启动目标服务器。</span><span class="sxs-lookup"><span data-stu-id="42bb6-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="42bb6-131">若要在离线的 VHD 上删除角色和功能，你必须添加 `-ComputerName` 参数和 `-VHD` 参数。</span><span class="sxs-lookup"><span data-stu-id="42bb6-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="42bb6-132">`-ComputerName` 参数含有安装 VHD 的服务器名称， `-VHD` 参数含有 VHD 在指定服务器上的路径。</span><span class="sxs-lookup"><span data-stu-id="42bb6-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="42bb6-133">删除完成后，验证你已删除 Windows PowerShell Web 访问，方法是打开服务管理器中的“所有服务器”页面，选择要删除其功能的服务器，然后在选定服务器的页面上查看“角色和功能”磁贴。</span><span class="sxs-lookup"><span data-stu-id="42bb6-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="42bb6-134">也可针对选定的服务器运行 `Get-WindowsFeature` cmdlet (Get-WindowsFeature -ComputerName &lt;computer_name&gt;)，以查看该服务器上安装的角色和功能的列表。</span><span class="sxs-lookup"><span data-stu-id="42bb6-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="42bb6-135">自定义卸载</span><span class="sxs-lookup"><span data-stu-id="42bb6-135">Custom uninstallation</span></span>

<span data-ttu-id="42bb6-136">本部分中的过程帮助你通过使用服务管理器中的“删除角色和功能向导”和 IIS 管理器卸载 Windows PowerShell Web 访问 Web 应用程序和 Windows PowerShell Web 访问功能。</span><span class="sxs-lookup"><span data-stu-id="42bb6-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="42bb6-137">步骤 1：使用 IIS Manager 删除 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="42bb6-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="42bb6-138">通过执行以下操作之一，打开 IIS 管理器控制台。</span><span class="sxs-lookup"><span data-stu-id="42bb6-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="42bb6-139">如果该控制台已经打开，则继续执行下一步。</span><span class="sxs-lookup"><span data-stu-id="42bb6-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="42bb6-140">在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="42bb6-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="42bb6-141">在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="42bb6-142">在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。</span><span class="sxs-lookup"><span data-stu-id="42bb6-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="42bb6-143">当快捷方式在“应用程序”结果中显示时，单击它。</span><span class="sxs-lookup"><span data-stu-id="42bb6-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="42bb6-144">在 IIS 管理器树窗格中，选择运行 Windows PowerShell Web 访问 Web 应用程序的网站。</span><span class="sxs-lookup"><span data-stu-id="42bb6-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="42bb6-145">在**操作**窗格中，在**管理网站**下，单击**停止**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="42bb6-146">在树窗格中，右键单击运行 Windows PowerShell Web 访问 Web 应用程序的网站中的 Web 应用程序，然后单击**删除**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="42bb6-147">在树窗格中，选择“应用程序池”，并选择 Windows PowerShell Web 访问应用程序池文件夹，单击“操作”窗格中的“停止”，然后单击内容窗格中的“删除”。</span><span class="sxs-lookup"><span data-stu-id="42bb6-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="42bb6-148">关闭 IIS 管理器。</span><span class="sxs-lookup"><span data-stu-id="42bb6-148">Close IIS Manager.</span></span>

> <span data-ttu-id="42bb6-149">![警告注意](images/SecurityNote.jpeg)**注意**：</span><span class="sxs-lookup"><span data-stu-id="42bb6-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="42bb6-150">在卸载过程中未删除证书。</span><span class="sxs-lookup"><span data-stu-id="42bb6-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="42bb6-151">如果你创建了自签名的证书或使用测试证书，现想将它删除，则可在 IIS 管理器中删除该证书。</span><span class="sxs-lookup"><span data-stu-id="42bb6-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="42bb6-152">步骤 2：使用“删除角色和功能向导”卸载 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="42bb6-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="42bb6-153">如果服务器管理器已经打开，则继续执行下一步。</span><span class="sxs-lookup"><span data-stu-id="42bb6-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="42bb6-154">如果服务器管理器尚未打开，请执行以下任一操作打开它。</span><span class="sxs-lookup"><span data-stu-id="42bb6-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="42bb6-155">在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="42bb6-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="42bb6-156">在 Windows **开始**屏幕上，单击**服务器管理器**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="42bb6-157">在**管理**菜单上，单击**删除角色和功能**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="42bb6-158">在“选择目标服务器”页面上，选择你想删除其功能的服务器或离线 VHD。</span><span class="sxs-lookup"><span data-stu-id="42bb6-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="42bb6-159">若要选择离线的 VHD，请选择安装 VHD 的服务器，然后选择 VHD 文件。</span><span class="sxs-lookup"><span data-stu-id="42bb6-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="42bb6-160">选择目标服务器后，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="42bb6-161">再次单击“下一步”，跳到“删除功能”页面。</span><span class="sxs-lookup"><span data-stu-id="42bb6-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="42bb6-162">清除**Windows PowerShell Web 访问**复选框，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="42bb6-163">在**确认删除选择**页面上，单击**删除**。</span><span class="sxs-lookup"><span data-stu-id="42bb6-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="42bb6-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42bb6-164">See Also</span></span>

- [<span data-ttu-id="42bb6-165">安装和使用 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="42bb6-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="42bb6-166">IIS Manager 7.0 帮助</span><span class="sxs-lookup"><span data-stu-id="42bb6-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)