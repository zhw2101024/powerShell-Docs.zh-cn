---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "卸载 Windows PowerShell Web 访问"
ms.openlocfilehash: 7231d5eadceda8e3b28d9a81c2b5dcbe43680ff2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="ff579-103">卸载 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="ff579-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="ff579-104">更新时间：2013年 6 月 24日</span><span class="sxs-lookup"><span data-stu-id="ff579-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="ff579-105">适用于：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ff579-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="ff579-106">按照本主题中的步骤从运行 Windows Server 2012 R2 或 Windows Server 2012 的网关服务器删除 Windows PowerShell Web 访问网站和应用程序。</span><span class="sxs-lookup"><span data-stu-id="ff579-106">Follow steps in this topic to delete the Windows PowerShell Web Access website and application from the gateway server that is running either Windows Server 2012 R2 or Windows Server 2012.</span></span> <span data-ttu-id="ff579-107">开始前，先通知基于 Web 控制台的用户，你准备删除网站。</span><span class="sxs-lookup"><span data-stu-id="ff579-107">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

<span data-ttu-id="ff579-108">从网关服务器中卸载 Windows PowerShell Web 访问之前，运行 <span class="code">Uninstall-PswaWebApplication</span> cmdlet 删除网站和 Windows PowerShell Web 访问 Web 应用程序，或使用 IIS Manager 程序，即[通过使用 IIS Manager 删除 Windows PowerShell Web 访问网站和 Web 应用程序](#BKMK_delsite)。</span><span class="sxs-lookup"><span data-stu-id="ff579-108">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the <span class="code">Uninstall-PswaWebApplication</span> cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [To delete the Windows PowerShell Web Access website and web applications by using IIS Manager](#BKMK_delsite).</span></span>

<span data-ttu-id="ff579-109">卸载 Windows PowerShell Web 访问并不卸载 IIS 或任何其他自动安装的功能，因为 Windows PowerShell Web 访问需要它们处于运行状态。</span><span class="sxs-lookup"><span data-stu-id="ff579-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="ff579-110">卸载过程保留了依赖 Windows PowerShell Web 访问的功能；必要时你可以单独卸载那些功能。</span><span class="sxs-lookup"><span data-stu-id="ff579-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

<span data-ttu-id="ff579-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">建议（快速）卸载</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ff579-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ff579-112">本部分中的过程帮助你通过使用 Windows PowerShell cmdlet 卸载 Windows PowerShell Web 访问 Web 应用程序和 Windows PowerShell Web 访问功能。</span><span class="sxs-lookup"><span data-stu-id="ff579-112">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using Windows PowerShell cmdlets.</span></span>

###

<span data-ttu-id="ff579-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 1：删除 Web 应用程序</span></a></span><span class="sxs-lookup"><span data-stu-id="ff579-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ff579-114">如果指定了自己的自定义网站名称，请将 <span class="code">WebsiteName</span> 参数添加到命令中，并指定网站名称。</span><span class="sxs-lookup"><span data-stu-id="ff579-114">If you have specified your own, custom website name, add the <span class="code">WebsiteName</span> parameter to your command, and specify the website name.</span></span> <span data-ttu-id="ff579-115">如果使用了自定义 Web 应用程序（不是默认应用程序 **pswa**)，请将 <span class="code">WebApplicationName</span> 参数添加到命令中，并指定 Web 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="ff579-115">If you have used a custom web application (not the default application, **pswa**, add the <span class="code">WebApplicationName</span> parameter to your command, and specify the name of the web application.</span></span>

#### <a name="to-delete-the-website-and-web-applications-by-using-the-uninstall-pswawebapplication-cmdlet"></a><span data-ttu-id="ff579-116">使用 Uninstall-PswaWebApplication cmdlet 删除网站和 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="ff579-116">To delete the website and web applications by using the Uninstall-PswaWebApplication cmdlet</span></span>

1.  <span data-ttu-id="ff579-117">执行以下操作之一，打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="ff579-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="ff579-118">在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ff579-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="ff579-119">在 Windows **开始**屏幕上，单击**Windows PowerShell**。</span><span class="sxs-lookup"><span data-stu-id="ff579-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="ff579-120">键入**Uninstall-PswaWebApplication**，然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="ff579-120">Type **Uninstall-PswaWebApplication**, and then press **Enter**.</span></span>

3.  <span data-ttu-id="ff579-121">如果你使用的是测试证书，则将 <span class="code">DeleteTestCertificate</span> 参数添加到 cmdlet（如以下示例所述）。</span><span class="sxs-lookup"><span data-stu-id="ff579-121">If you are using a test certificate, add the <span class="code">DeleteTestCertificate</span> parameter to the cmdlet, as shown in the following example.</span></span>

    [<span data-ttu-id="ff579-122">Copy</span><span class="sxs-lookup"><span data-stu-id="ff579-122">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copy to clipboard.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<span data-ttu-id="ff579-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 2：卸载 Windows PowerShell Web 访问</span></a></span><span class="sxs-lookup"><span data-stu-id="ff579-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="ff579-124">使用 Windows PowerShell cmdlet 卸载 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="ff579-124">To uninstall Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="ff579-125">使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="ff579-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="ff579-126">如果会话已经打开，则继续执行下一步。</span><span class="sxs-lookup"><span data-stu-id="ff579-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="ff579-127">在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="ff579-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="ff579-128">在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。</span><span class="sxs-lookup"><span data-stu-id="ff579-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="ff579-129">键入以下内容，然后按 **Enter**，其中的 *computer_name* 代表要从中删除 Windows PowerShell Web 访问的远程服务器。</span><span class="sxs-lookup"><span data-stu-id="ff579-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="ff579-130">如果在删除过程中有必要，<span class="code">-Restart</span> 参数将自动重启目标服务器。</span><span class="sxs-lookup"><span data-stu-id="ff579-130">The <span class="code">-Restart</span> parameter automatically restarts destination servers if required by the removal.</span></span>

    [<span data-ttu-id="ff579-131">Copy</span><span class="sxs-lookup"><span data-stu-id="ff579-131">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copy to clipboard.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="ff579-132">若要在离线的 VHD 上删除角色和功能，你必须添加 <span class="code">-ComputerName</span> 参数和 <span class="code">-VHD</span> 参数。</span><span class="sxs-lookup"><span data-stu-id="ff579-132">To remove roles and features from an offline VHD, you must add both the <span class="code">-ComputerName</span> parameter and the <span class="code">-VHD</span> parameter.</span></span> <span data-ttu-id="ff579-133"><span class="code">-ComputerName</span> 参数含有安装 VHD 的服务器的名称，<span class="code">-VHD</span> 参数含有 VHD 文件在指定服务器上的路径。</span><span class="sxs-lookup"><span data-stu-id="ff579-133">The <span class="code">-ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">-VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="ff579-134">Copy</span><span class="sxs-lookup"><span data-stu-id="ff579-134">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copy to clipboard.")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

3.  <span data-ttu-id="ff579-135">删除完成后，验证你已删除 Windows PowerShell Web 访问，方法是打开服务管理器中的“所有服务器”页面，选择要删除其功能的服务器，然后在选定服务器的页面上查看“角色和功能”磁贴。</span><span class="sxs-lookup"><span data-stu-id="ff579-135">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span> <span data-ttu-id="ff579-136">你也可以将选定的服务器作为目标运行 <span class="code">Get-WindowsFeature</span> cmdlet (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;)，以查看该服务器上安装的角色和功能的列表。</span><span class="sxs-lookup"><span data-stu-id="ff579-136">You can also run the <span class="code">Get-WindowsFeature</span> cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

<span data-ttu-id="ff579-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">自定义卸载</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ff579-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ff579-138">本部分中的过程帮助你通过使用服务管理器中的“删除角色和功能向导”和 IIS 管理器卸载 Windows PowerShell Web 访问 Web 应用程序和 Windows PowerShell Web 访问功能。</span><span class="sxs-lookup"><span data-stu-id="ff579-138">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

###

<span data-ttu-id="ff579-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 1：删除 Web 应用程序</span></a></span><span class="sxs-lookup"><span data-stu-id="ff579-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-delete-the-windows-powershell-web-access-website-and-web-applications-by-using-iis-manager"></a><span data-ttu-id="ff579-140">使用 IIS 管理器删除 Windows PowerShell Web 访问网站和 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="ff579-140">To delete the Windows PowerShell Web Access website and web applications by using IIS Manager</span></span>

1.  <span data-ttu-id="ff579-141">通过执行以下操作之一，打开 IIS 管理器控制台。</span><span class="sxs-lookup"><span data-stu-id="ff579-141">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="ff579-142">如果该控制台已经打开，则继续执行下一步。</span><span class="sxs-lookup"><span data-stu-id="ff579-142">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="ff579-143">在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="ff579-143">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="ff579-144">在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。</span><span class="sxs-lookup"><span data-stu-id="ff579-144">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="ff579-145">在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。</span><span class="sxs-lookup"><span data-stu-id="ff579-145">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="ff579-146">当快捷方式在“应用程序”结果中显示时，单击它。</span><span class="sxs-lookup"><span data-stu-id="ff579-146">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="ff579-147">在 IIS 管理器树窗格中，选择运行 Windows PowerShell Web 访问 Web 应用程序的网站。</span><span class="sxs-lookup"><span data-stu-id="ff579-147">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

3.  <span data-ttu-id="ff579-148">在**操作**窗格中，在**管理网站**下，单击**停止**。</span><span class="sxs-lookup"><span data-stu-id="ff579-148">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

4.  <span data-ttu-id="ff579-149">在树窗格中，右键单击运行 Windows PowerShell Web 访问 Web 应用程序的网站中的 Web 应用程序，然后单击**删除**。</span><span class="sxs-lookup"><span data-stu-id="ff579-149">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

5.  <span data-ttu-id="ff579-150">在树窗格中，选择“应用程序池”，并选择 Windows PowerShell Web 访问应用程序池文件夹，单击“操作”窗格中的“停止”，然后单击内容窗格中的“删除”。</span><span class="sxs-lookup"><span data-stu-id="ff579-150">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

6.  <span data-ttu-id="ff579-151">关闭 IIS 管理器。</span><span class="sxs-lookup"><span data-stu-id="ff579-151">Close IIS Manager.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="ff579-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意</span></span><span class="sxs-lookup"><span data-stu-id="ff579-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="ff579-153">在卸载过程中未删除证书。</span><span class="sxs-lookup"><span data-stu-id="ff579-153">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="ff579-154">如果你创建了自签名的证书或使用测试证书，现想将它删除，则可在 IIS 管理器中删除该证书。</span><span class="sxs-lookup"><span data-stu-id="ff579-154">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="ff579-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 2：卸载 Windows PowerShell Web 访问</span></a></span><span class="sxs-lookup"><span data-stu-id="ff579-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="ff579-156">使用“删除角色和功能向导”卸载 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="ff579-156">To uninstall Windows PowerShell Web Access by using the Remove Roles and Features Wizard</span></span>

1.  <span data-ttu-id="ff579-157">如果服务管理器已经打开，则继续执行下一步。</span><span class="sxs-lookup"><span data-stu-id="ff579-157">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="ff579-158">如果服务器管理器尚未打开，请执行以下任一操作打开它。</span><span class="sxs-lookup"><span data-stu-id="ff579-158">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="ff579-159">在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。</span><span class="sxs-lookup"><span data-stu-id="ff579-159">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="ff579-160">在 Windows **开始**屏幕上，单击**服务器管理器**。</span><span class="sxs-lookup"><span data-stu-id="ff579-160">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="ff579-161">在**管理**菜单上，单击**删除角色和功能**。</span><span class="sxs-lookup"><span data-stu-id="ff579-161">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

3.  <span data-ttu-id="ff579-162">在“选择目标服务器”页面上，选择你想删除其功能的服务器或离线 VHD。</span><span class="sxs-lookup"><span data-stu-id="ff579-162">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="ff579-163">若要选择离线的 VHD，请选择安装 VHD 的服务器，然后选择 VHD 文件。</span><span class="sxs-lookup"><span data-stu-id="ff579-163">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="ff579-164">选择目标服务器后，单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="ff579-164">After you have selected the destination server, click **Next**.</span></span>

4.  <span data-ttu-id="ff579-165">再次单击“下一步”，跳到“删除功能”页面。</span><span class="sxs-lookup"><span data-stu-id="ff579-165">Click **Next** again to skip to the **Remove features** page.</span></span>

5.  <span data-ttu-id="ff579-166">清除**Windows PowerShell Web 访问**复选框，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="ff579-166">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

6.  <span data-ttu-id="ff579-167">在**确认删除选择**页面上，单击**删除**。</span><span class="sxs-lookup"><span data-stu-id="ff579-167">On the **Confirm removal selections** page, click **Remove**.</span></span>

<span data-ttu-id="ff579-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="ff579-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="ff579-169">[安装和使用 Windows PowerShell Web 访问](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 帮助](https://technet.microsoft.com/library/cc732664.aspx)</span><span class="sxs-lookup"><span data-stu-id="ff579-169">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)</span></span>

<span data-ttu-id="ff579-170"><span>显示：</span>继承内容受保护</span><span class="sxs-lookup"><span data-stu-id="ff579-170"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="ff579-171"><span class="stdr-votetitle">此页面是否有所帮助？</span></span><span class="sxs-lookup"><span data-stu-id="ff579-171"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="ff579-172">是 否</span><span class="sxs-lookup"><span data-stu-id="ff579-172">Yes No</span></span>

<span data-ttu-id="ff579-173">更多反馈？</span><span class="sxs-lookup"><span data-stu-id="ff579-173">Additional feedback?</span></span>

<span data-ttu-id="ff579-174">剩余 <span class="stdr-count"><span class="stdr-charcnt">1500</span> 个字符</span>提交，跳过此部分</span><span class="sxs-lookup"><span data-stu-id="ff579-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="ff579-175"><span class="stdr-thankyou">谢谢！</span></span><span class="sxs-lookup"><span data-stu-id="ff579-175"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="ff579-176"><span class="stdr-appreciate">我们非常感谢你的反馈意见。</span></span><span class="sxs-lookup"><span data-stu-id="ff579-176"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="ff579-177">管理个人资料</span><span class="sxs-lookup"><span data-stu-id="ff579-177">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="ff579-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span>站点反馈</a>站点反馈</span><span class="sxs-lookup"><span data-stu-id="ff579-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="ff579-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="ff579-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="ff579-180">告诉我们你的体验...</span><span class="sxs-lookup"><span data-stu-id="ff579-180">Tell us about your experience...</span></span>

<span data-ttu-id="ff579-181">页面加载速度快吗？</span><span class="sxs-lookup"><span data-stu-id="ff579-181">Did the page load quickly?</span></span>

<span data-ttu-id="ff579-182"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="ff579-182"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="ff579-183">你喜欢页面设计吗？</span><span class="sxs-lookup"><span data-stu-id="ff579-183">Do you like the page design?</span></span>

<span data-ttu-id="ff579-184"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="ff579-184"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="ff579-185">告诉我们更多内容</span><span class="sxs-lookup"><span data-stu-id="ff579-185">Tell us more</span></span>

-   [<span data-ttu-id="ff579-186">快讯</span><span class="sxs-lookup"><span data-stu-id="ff579-186">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="ff579-187">联系我们</span><span class="sxs-lookup"><span data-stu-id="ff579-187">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="ff579-188">隐私声明</span><span class="sxs-lookup"><span data-stu-id="ff579-188">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="ff579-189">使用条款</span><span class="sxs-lookup"><span data-stu-id="ff579-189">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="ff579-190">商标</span><span class="sxs-lookup"><span data-stu-id="ff579-190">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="ff579-191">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff579-191">© 2016 Microsoft</span></span>

<span data-ttu-id="ff579-192">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff579-192">© 2016 Microsoft</span></span>

<span data-ttu-id="ff579-193">链接到此站点或从中引用的第三方脚本或代码由拥有此类代码的第三方（而非 Microsoft）授权给你。</span><span class="sxs-lookup"><span data-stu-id="ff579-193">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="ff579-194">请参阅 ASP.NET Ajax CDN 使用条款，网址为 http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="ff579-194">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

