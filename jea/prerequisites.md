---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: JEA 先决条件
ms.openlocfilehash: a5cf5519b30b24d44c12bdeedcf4cd763e2edbde
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189765"
---
# <a name="prerequisites"></a><span data-ttu-id="895bf-103">必备条件</span><span class="sxs-lookup"><span data-stu-id="895bf-103">Prerequisites</span></span>

> <span data-ttu-id="895bf-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="895bf-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="895bf-105">Just Enough Administration 是 Windows PowerShell 5.0 及更高版本随附的功能。</span><span class="sxs-lookup"><span data-stu-id="895bf-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="895bf-106">本主题介绍使用 JEA 必须满足的先决条件。</span><span class="sxs-lookup"><span data-stu-id="895bf-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="895bf-107">安装 JEA</span><span class="sxs-lookup"><span data-stu-id="895bf-107">Install JEA</span></span>

<span data-ttu-id="895bf-108">Windows PowerShell 5.0 及更高版本均包含 JEA 功能，但若要使用完整的功能，建议安装适用于系统的 PowerShell 最新版。</span><span class="sxs-lookup"><span data-stu-id="895bf-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="895bf-109">下表介绍了 JEA 在 Windows Server 上的可用性：</span><span class="sxs-lookup"><span data-stu-id="895bf-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="895bf-110">服务器操作系统</span><span class="sxs-lookup"><span data-stu-id="895bf-110">Server Operating System</span></span>   | <span data-ttu-id="895bf-111">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="895bf-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="895bf-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="895bf-112">Windows Server 2016</span></span>       | <span data-ttu-id="895bf-113">已预安装</span><span class="sxs-lookup"><span data-stu-id="895bf-113">Preinstalled</span></span>
<span data-ttu-id="895bf-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="895bf-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="895bf-115">包含 WMF 5.1 的完整功能</span><span class="sxs-lookup"><span data-stu-id="895bf-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="895bf-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="895bf-116">Windows Server 2012</span></span>       | <span data-ttu-id="895bf-117">包含 WMF 5.1 的完整功能</span><span class="sxs-lookup"><span data-stu-id="895bf-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="895bf-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="895bf-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="895bf-119">减少了功能<sup>1</sup>（如果 WMF 5.1 已安装）</span><span class="sxs-lookup"><span data-stu-id="895bf-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="895bf-120">此外，还可以在家庭或工作计算机上使用 JEA：</span><span class="sxs-lookup"><span data-stu-id="895bf-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="895bf-121">客户端操作系统</span><span class="sxs-lookup"><span data-stu-id="895bf-121">Client Operating System</span></span>   | <span data-ttu-id="895bf-122">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="895bf-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="895bf-123">Windows 10 1607 及更高版本</span><span class="sxs-lookup"><span data-stu-id="895bf-123">Windows 10 1607+</span></span>          | <span data-ttu-id="895bf-124">已预安装</span><span class="sxs-lookup"><span data-stu-id="895bf-124">Preinstalled</span></span>
<span data-ttu-id="895bf-125">Windows 10 1603 版、1511 版</span><span class="sxs-lookup"><span data-stu-id="895bf-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="895bf-126">已预安装，但减少了功能<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="895bf-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="895bf-127">Windows 10 1507 版</span><span class="sxs-lookup"><span data-stu-id="895bf-127">Windows 10 1507</span></span>           | <span data-ttu-id="895bf-128">不可用</span><span class="sxs-lookup"><span data-stu-id="895bf-128">Not available</span></span>
<span data-ttu-id="895bf-129">Windows 8、8.1</span><span class="sxs-lookup"><span data-stu-id="895bf-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="895bf-130">包含 WMF 5.1 的完整功能</span><span class="sxs-lookup"><span data-stu-id="895bf-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="895bf-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="895bf-131">Windows 7</span></span>                 | <span data-ttu-id="895bf-132">减少了功能<sup>1</sup>（如果 WMF 5.1 已安装）</span><span class="sxs-lookup"><span data-stu-id="895bf-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="895bf-133"><sup>1</sup>无法将 JEA 配置为在 Windows Server 2008 R2 或 Windows 7 上使用组托管服务帐户。</span><span class="sxs-lookup"><span data-stu-id="895bf-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="895bf-134">*支持*虚拟帐户和其他 JEA 功能。</span><span class="sxs-lookup"><span data-stu-id="895bf-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="895bf-135"><sup>2</sup>Windows 10 版本 1511 和 1603 不支持以下 JEA 功能：以组托管服务帐户身份运行、会话配置中的条件访问规则、用户驱动器以及向本地用户帐户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="895bf-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="895bf-136">若要获取对这些功能的支持，请将 Windows 更新到 1607 版（周年更新）或更高版本。</span><span class="sxs-lookup"><span data-stu-id="895bf-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="895bf-137">查看安装的 PowerShell 版本类型</span><span class="sxs-lookup"><span data-stu-id="895bf-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="895bf-138">若要查看系统上安装的 PowerShell 版本类型，请查看 Windows PowerShell 提示符中的 `$PSVersionTable` 变量。</span><span class="sxs-lookup"><span data-stu-id="895bf-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="895bf-139">如果主要版本等于或大于 **5**，便可以使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="895bf-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="895bf-140">如果可能，为获得最佳体验，并有权访问所有最新功能，建议升级到 PowerShell **5.1** 版。</span><span class="sxs-lookup"><span data-stu-id="895bf-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="895bf-141">安装 Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="895bf-141">Install Windows Management Framework</span></span>

<span data-ttu-id="895bf-142">如果运行的是 PowerShell 较旧版本，需要使用最新的 Windows Management Framework (WMF) 更新来更新系统。</span><span class="sxs-lookup"><span data-stu-id="895bf-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="895bf-143">可在[下载中心](https://aka.ms/WMF5)找到更新包和最新 WMF 发行说明的链接。</span><span class="sxs-lookup"><span data-stu-id="895bf-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="895bf-144">强烈建议在升级所有服务器前，测试工作负荷与 WMF 的兼容性。</span><span class="sxs-lookup"><span data-stu-id="895bf-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="895bf-145">Windows 10 用户需安装最新功能更新才能获取当前版本的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="895bf-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="895bf-146">启用 PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="895bf-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="895bf-147">PowerShell 远程处理提供了构建 JEA 的基础。</span><span class="sxs-lookup"><span data-stu-id="895bf-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="895bf-148">因此，有必要先确保系统已启用 PowerShell 远程处理并[受到适当保护](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)，然后才能使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="895bf-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="895bf-149">在 Windows Server 2012、2012 R2 和 2016 中，默认启用 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="895bf-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="895bf-150">可通过在提升的 PowerShell 窗口中运行以下命令来启用 PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="895bf-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="895bf-151">启用 PowerShell 模块和脚本块日志记录（可选）</span><span class="sxs-lookup"><span data-stu-id="895bf-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="895bf-152">执行以下步骤将为系统上的所有 PowerShell 操作启用日志记录。</span><span class="sxs-lookup"><span data-stu-id="895bf-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="895bf-153">PowerShell 模块日志记录不是 JEA 必需的，但强烈建议打开它，以确保在中心位置记录用户运行的命令。</span><span class="sxs-lookup"><span data-stu-id="895bf-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="895bf-154">可使用组策略配置 PowerShell 模块日志记录策略。</span><span class="sxs-lookup"><span data-stu-id="895bf-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="895bf-155">在工作站上打开“本地组策略编辑器”，或在 Active Directory 域控制器中，打开“组策略管理控制台”中的“组策略对象”</span><span class="sxs-lookup"><span data-stu-id="895bf-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="895bf-156">导航到“计算机配置\\管理模板\\Windows 组件\\Windows PowerShell”</span><span class="sxs-lookup"><span data-stu-id="895bf-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="895bf-157">双击“打开模块日志记录”</span><span class="sxs-lookup"><span data-stu-id="895bf-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="895bf-158">单击“启用”</span><span class="sxs-lookup"><span data-stu-id="895bf-158">Click **Enabled**</span></span>
5. <span data-ttu-id="895bf-159">在“选项”部分中，单击“模块名称”旁的“显示”</span><span class="sxs-lookup"><span data-stu-id="895bf-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="895bf-160">在弹出窗口中键入“**\***”。</span><span class="sxs-lookup"><span data-stu-id="895bf-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="895bf-161">这将指示 PowerShell 记录来自所有模块的命令。</span><span class="sxs-lookup"><span data-stu-id="895bf-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="895bf-162">单击“确定”设置策略</span><span class="sxs-lookup"><span data-stu-id="895bf-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="895bf-163">双击“打开 PowerShell 脚本块日志记录”</span><span class="sxs-lookup"><span data-stu-id="895bf-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="895bf-164">单击“启用”</span><span class="sxs-lookup"><span data-stu-id="895bf-164">Click **Enabled**</span></span>
10. <span data-ttu-id="895bf-165">单击“确定”设置策略</span><span class="sxs-lookup"><span data-stu-id="895bf-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="895bf-166">（仅在已加入域的计算机上）运行 **gpupdate** 或等待组策略处理更新后的策略，然后应用相应设置</span><span class="sxs-lookup"><span data-stu-id="895bf-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="895bf-167">也可通过“组策略”启用系统范围的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="895bf-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="895bf-168">后续步骤</span><span class="sxs-lookup"><span data-stu-id="895bf-168">Next steps</span></span>

- [<span data-ttu-id="895bf-169">创建角色功能文件</span><span class="sxs-lookup"><span data-stu-id="895bf-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="895bf-170">创建会话配置文件</span><span class="sxs-lookup"><span data-stu-id="895bf-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="895bf-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="895bf-171">See also</span></span>

- [<span data-ttu-id="895bf-172">有关 PowerShell 远程处理和 WinRM 安全性的其他信息</span><span class="sxs-lookup"><span data-stu-id="895bf-172">Additional information about PowerShell Remoting and WinRM security</span></span>](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [<span data-ttu-id="895bf-173">PowerShell ♥ the Blue Team 关于安全的博客文章</span><span class="sxs-lookup"><span data-stu-id="895bf-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)