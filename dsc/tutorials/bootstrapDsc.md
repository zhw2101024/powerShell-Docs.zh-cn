---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 初始启动时使用 DSC 配置虚拟机
ms.openlocfilehash: 7b9ebc6c818aa39365759945667426c8976997e5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400873"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="a5407-103">初始启动时使用 DSC 配置虚拟机</span><span class="sxs-lookup"><span data-stu-id="a5407-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5407-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a5407-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="a5407-105">要求</span><span class="sxs-lookup"><span data-stu-id="a5407-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="a5407-106">本主题所述的 DSCAutomationHostEnabled 注册表项在 PowerShell 4.0 中不可用。</span><span class="sxs-lookup"><span data-stu-id="a5407-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="a5407-107">有关如何在初始启动时在 PowerShell 4.0 中配置新虚拟机的信息，请参阅[想要在初始启动时使用 DSC 自动配置计算机？]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="a5407-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="a5407-108">若要运行这些示例，则需要：</span><span class="sxs-lookup"><span data-stu-id="a5407-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="a5407-109">要使用的可启动 VHD。</span><span class="sxs-lookup"><span data-stu-id="a5407-109">A bootable VHD to work with.</span></span> <span data-ttu-id="a5407-110">可以在 [TechNet 评估中心](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)下载具有 Windows Server 2016 评估副本的 ISO。</span><span class="sxs-lookup"><span data-stu-id="a5407-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> <span data-ttu-id="a5407-111">可以在[创建可启动虚拟硬盘](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10))处找到有关如何从 ISO 映像创建 VHD 的说明。</span><span class="sxs-lookup"><span data-stu-id="a5407-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="a5407-112">已启用 Hyper-V 的主计算机。</span><span class="sxs-lookup"><span data-stu-id="a5407-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="a5407-113">有关信息，请参阅 [Hyper-V 概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="a5407-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="a5407-114">通过使用 DSC，可以在初始启动时对计算机实现软件安装和配置的自动化。</span><span class="sxs-lookup"><span data-stu-id="a5407-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="a5407-115">可以通过将配置 MOF 文档或元配置注入可启动媒体（例如 VHD）来执行此操作，以便它们能在初始启动过程中运行。</span><span class="sxs-lookup"><span data-stu-id="a5407-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="a5407-116">通过 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies` 下的 [DSCAutomationHostEnabled 注册表项](DSCAutomationHostEnabled.md) 注册表项指定此行为。</span><span class="sxs-lookup"><span data-stu-id="a5407-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.</span></span>
  <span data-ttu-id="a5407-117">默认情况下，此项的值为 2，这允许 DSC 在启动时运行。</span><span class="sxs-lookup"><span data-stu-id="a5407-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="a5407-118">如果不希望 DSC 在启动时运行，将 [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) 注册表项的值设置为 0。</span><span class="sxs-lookup"><span data-stu-id="a5407-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="a5407-119">将配置 MOF 文档注入 VHD</span><span class="sxs-lookup"><span data-stu-id="a5407-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="a5407-120">将 DSC 元配置注入 VHD</span><span class="sxs-lookup"><span data-stu-id="a5407-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="a5407-121">启动时，请禁用 DSC</span><span class="sxs-lookup"><span data-stu-id="a5407-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="a5407-122">可以将 `Pending.mof` 和 `MetaConfig.mof` 同时注入计算机。</span><span class="sxs-lookup"><span data-stu-id="a5407-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="a5407-123">如果这两个文件都存在，则在 `MetaConfig.mof` 中指定的设置优先。</span><span class="sxs-lookup"><span data-stu-id="a5407-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="a5407-124">将配置 MOF 文档注入 VHD</span><span class="sxs-lookup"><span data-stu-id="a5407-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="a5407-125">若要在初始启动时执行配置，可以将已编译的配置 MOF 文档注入 VHD 作为其 `Pending.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="a5407-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="a5407-126">如果将 **DSCAutomationHostEnabled** 注册表项设置为 2（默认值），则在首次启动计算机时，DSC 将应用由 `Pending.mof` 定义的配置。</span><span class="sxs-lookup"><span data-stu-id="a5407-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="a5407-127">对于此示例，我们将使用以下配置，它将在新计算机上安装 IIS：</span><span class="sxs-lookup"><span data-stu-id="a5407-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="a5407-128">将配置 MOF 文档注入 VHD</span><span class="sxs-lookup"><span data-stu-id="a5407-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="a5407-129">通过调用 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet，将 VHD 装入想要注入配置的位置。</span><span class="sxs-lookup"><span data-stu-id="a5407-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="a5407-130">例如：</span><span class="sxs-lookup"><span data-stu-id="a5407-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="a5407-131">在运行 PowerShell 5.0 或更高版本的计算机上，将以上配置 (**SampleIISInstall**) 保存为 PowerShell 脚本 (.ps1) 文件。</span><span class="sxs-lookup"><span data-stu-id="a5407-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="a5407-132">在 PowerShell 控制台中，导航到保存 .ps1 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a5407-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="a5407-133">运行以下 PowerShell 命令来编译 MOF 文档（有关编译 DSC 配置的信息，请参阅 [DSC 配置](../configurations/configurations.md)：</span><span class="sxs-lookup"><span data-stu-id="a5407-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="a5407-134">这将在名为 `SampleIISInstall` 的新文件夹中创建 `localhost.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="a5407-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="a5407-135">通过使用 [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet，重命名该文件并将其移动到 VHD 上的正确位置，作为 `Pending.mof`。</span><span class="sxs-lookup"><span data-stu-id="a5407-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="a5407-136">例如：</span><span class="sxs-lookup"><span data-stu-id="a5407-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="a5407-137">通过调用 [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet 卸除 VHD。</span><span class="sxs-lookup"><span data-stu-id="a5407-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="a5407-138">例如：</span><span class="sxs-lookup"><span data-stu-id="a5407-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="a5407-139">通过使用安装了 DSC MOF 文档的 VHD 创建 VM。</span><span class="sxs-lookup"><span data-stu-id="a5407-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="a5407-140">初始启动并安装操作系统之后，将安装 IIS。</span><span class="sxs-lookup"><span data-stu-id="a5407-140">After intial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="a5407-141">可以通过调用 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet 对此进行验证。</span><span class="sxs-lookup"><span data-stu-id="a5407-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="a5407-142">将 DSC 元配置注入 VHD</span><span class="sxs-lookup"><span data-stu-id="a5407-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="a5407-143">还可通过将元配置注入 VHD 作为其 `MetaConfig.mof` 文件，从而在初始启动时配置计算机以拉取配置（请参阅[配置本地配置管理器 (LCM)](../managing-nodes/metaConfig.md)）。</span><span class="sxs-lookup"><span data-stu-id="a5407-143">You can also configure a computer to pull a configuration at intial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="a5407-144">如果将 **DSCAutomationHostEnabled** 注册表项设置为 2（默认值），则在首次启动计算机时，DSC 会将由 `MetaConfig.mof` 定义的元配置应用到 LCM。</span><span class="sxs-lookup"><span data-stu-id="a5407-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="a5407-145">如果元配置指定 LCM 应从请求服务器拉取配置，则计算机将尝试在初始启动时从该请求服务器拉取配置。</span><span class="sxs-lookup"><span data-stu-id="a5407-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at inital boot-up.</span></span>
<span data-ttu-id="a5407-146">有关设置 DSC 请求服务器的信息，请参阅[设置 DSC Web 请求服务器](../pull-server/pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="a5407-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="a5407-147">对于此示例，我们将使用上一节中所述的配置 (**SampleIISInstall**)，以及以下元配置：</span><span class="sxs-lookup"><span data-stu-id="a5407-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="a5407-148">将元配置 MOF 文档注入 VHD</span><span class="sxs-lookup"><span data-stu-id="a5407-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="a5407-149">通过调用 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet，将 VHD 装入想要注入元配置的位置。</span><span class="sxs-lookup"><span data-stu-id="a5407-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="a5407-150">例如：</span><span class="sxs-lookup"><span data-stu-id="a5407-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="a5407-151">[设置 DSC Web 请求服务器](../pull-server/pullServer.md)，并将 **SampleIISInistall** 配置保存到相应的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a5407-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInistall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="a5407-152">在运行 PowerShell 5.0 或更高版本的计算机上，将以上元配置 (**PullClientBootstrap**) 保存为 PowerShell 脚本 (.ps1) 文件。</span><span class="sxs-lookup"><span data-stu-id="a5407-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="a5407-153">在 PowerShell 控制台中，导航到保存 .ps1 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a5407-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="a5407-154">运行以下 PowerShell 命令来编译元配置 MOF 文档（有关编译 DSC 配置的信息，请参阅 [DSC 配置](../configurations/configurations.md)：</span><span class="sxs-lookup"><span data-stu-id="a5407-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="a5407-155">这将在名为 `PullClientBootstrap` 的新文件夹中创建 `localhost.meta.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="a5407-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="a5407-156">通过使用 [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet，重命名该文件并将其移动到 VHD 上的正确位置，作为 `MetaConfig.mof`。</span><span class="sxs-lookup"><span data-stu-id="a5407-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="a5407-157">通过调用 [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet 卸除 VHD。</span><span class="sxs-lookup"><span data-stu-id="a5407-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="a5407-158">例如：</span><span class="sxs-lookup"><span data-stu-id="a5407-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="a5407-159">通过使用安装了 DSC MOF 文档的 VHD 创建 VM。</span><span class="sxs-lookup"><span data-stu-id="a5407-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="a5407-160">初始启动并安装操作系统之后，DSC 将从请求服务器拉取配置，并安装 IIS。</span><span class="sxs-lookup"><span data-stu-id="a5407-160">After intial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="a5407-161">可以通过调用 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet 对此进行验证。</span><span class="sxs-lookup"><span data-stu-id="a5407-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="a5407-162">启动时，请禁用 DSC</span><span class="sxs-lookup"><span data-stu-id="a5407-162">Disable DSC at boot time</span></span>

<span data-ttu-id="a5407-163">默认情况下，`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` 项的值设置为 2，以允许在计算机处于挂起或当前状态时运行 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="a5407-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="a5407-164">如果不希望配置在初始启动时运行，则需要将此项的值设置为 0：</span><span class="sxs-lookup"><span data-stu-id="a5407-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="a5407-165">通过调用 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet 装载 VHD。</span><span class="sxs-lookup"><span data-stu-id="a5407-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="a5407-166">例如：</span><span class="sxs-lookup"><span data-stu-id="a5407-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="a5407-167">通过调用 `reg load` 从 VHD 加载注册表 `HKLM\Software` 子项。</span><span class="sxs-lookup"><span data-stu-id="a5407-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="a5407-168">使用 PowerShell 注册表提供程序导航到 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*`。</span><span class="sxs-lookup"><span data-stu-id="a5407-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. <span data-ttu-id="a5407-169">将 `DSCAutomationHostEnabled` 的值更改为 0。</span><span class="sxs-lookup"><span data-stu-id="a5407-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="a5407-170">通过运行以下命令来卸载注册表：</span><span class="sxs-lookup"><span data-stu-id="a5407-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="a5407-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5407-171">See Also</span></span>

[<span data-ttu-id="a5407-172">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="a5407-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="a5407-173">DSCAutomationHostEnabled 注册表项</span><span class="sxs-lookup"><span data-stu-id="a5407-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="a5407-174">配置本地配置管理器 (LCM)</span><span class="sxs-lookup"><span data-stu-id="a5407-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="a5407-175">设置 DSC Web 请求服务器</span><span class="sxs-lookup"><span data-stu-id="a5407-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
