---
ms.date: 1/17/2019
keywords: dsc,powershell,配置,安装程序
title: 重新启动节点
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676834"
---
# <a name="reboot-a-node"></a><span data-ttu-id="fb096-103">重新启动节点</span><span class="sxs-lookup"><span data-stu-id="fb096-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="fb096-104">本主题讨论了如何重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="fb096-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="fb096-105">为了使重新启动才能成功**ActionAfterReboot**并**RebootNodeIfNeeded** LCM 设置需要正确配置。</span><span class="sxs-lookup"><span data-stu-id="fb096-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="fb096-106">若要了解有关本地配置管理器设置信息，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)，或[配置本地配置管理器 (v4)](../managing-nodes/metaConfig4.md)。</span><span class="sxs-lookup"><span data-stu-id="fb096-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="fb096-107">节点可以重启从在资源中，通过使用`$global:DSCMachineStatus`标志。</span><span class="sxs-lookup"><span data-stu-id="fb096-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="fb096-108">此标志设置为`1`中`Set-TargetResource`函数强制重启后的，直接节点的 LCM**设置**当前资源的方法。</span><span class="sxs-lookup"><span data-stu-id="fb096-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="fb096-109">使用此标志**xPendingReboot**资源检测到重新启动处于挂起状态之外 DSC。</span><span class="sxs-lookup"><span data-stu-id="fb096-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="fb096-110">你[配置](configurations.md)可能会执行需要重新启动的节点的步骤。</span><span class="sxs-lookup"><span data-stu-id="fb096-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="fb096-111">这可能包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="fb096-111">This could include things such as:</span></span>

- <span data-ttu-id="fb096-112">Windows: 更新</span><span class="sxs-lookup"><span data-stu-id="fb096-112">Windows updates</span></span>
- <span data-ttu-id="fb096-113">软件安装</span><span class="sxs-lookup"><span data-stu-id="fb096-113">Software install</span></span>
- <span data-ttu-id="fb096-114">重命名文件</span><span class="sxs-lookup"><span data-stu-id="fb096-114">File renames</span></span>
- <span data-ttu-id="fb096-115">计算机重命名</span><span class="sxs-lookup"><span data-stu-id="fb096-115">Computer rename</span></span>

<span data-ttu-id="fb096-116">**XPendingReboot**资源检查特定计算机位置，以确定重新启动处于挂起状态。</span><span class="sxs-lookup"><span data-stu-id="fb096-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="fb096-117">如果节点需要重新启动 DSC，之外**xPendingReboot**资源集`$global:DSCMachineStatus`标记，用于`1`强制重新启动，并且解决挂起的条件。</span><span class="sxs-lookup"><span data-stu-id="fb096-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="fb096-118">任何 DSC 资源可以指示重启节点中设置此标志的 LCM`Set-TargetResource`函数。</span><span class="sxs-lookup"><span data-stu-id="fb096-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="fb096-119">有关详细信息，请参阅[编写自定义 DSC 资源使用 MOF](../resources/authoringResourceMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="fb096-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="fb096-120">语法</span><span class="sxs-lookup"><span data-stu-id="fb096-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="fb096-121">“属性”</span><span class="sxs-lookup"><span data-stu-id="fb096-121">Properties</span></span>

| <span data-ttu-id="fb096-122">属性</span><span class="sxs-lookup"><span data-stu-id="fb096-122">Property</span></span> | <span data-ttu-id="fb096-123">说明</span><span class="sxs-lookup"><span data-stu-id="fb096-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fb096-124">名称</span><span class="sxs-lookup"><span data-stu-id="fb096-124">Name</span></span>| <span data-ttu-id="fb096-125">必需的参数，它必须是唯一的资源配置内的每个实例。</span><span class="sxs-lookup"><span data-stu-id="fb096-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="fb096-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="fb096-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="fb096-127">由基于组件的服务组件触发的跳过重新启动。</span><span class="sxs-lookup"><span data-stu-id="fb096-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="fb096-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="fb096-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="fb096-129">由 Windows Update 触发的跳过重新启动。</span><span class="sxs-lookup"><span data-stu-id="fb096-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="fb096-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="fb096-130">SkipPendingFileRename</span></span> | <span data-ttu-id="fb096-131">跳过挂起文件重命名的重新启动。</span><span class="sxs-lookup"><span data-stu-id="fb096-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="fb096-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="fb096-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="fb096-133">由 ConfigMgr 客户端触发的跳过重新启动。</span><span class="sxs-lookup"><span data-stu-id="fb096-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="fb096-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="fb096-134">SkipComputerRename</span></span> | <span data-ttu-id="fb096-135">跳过重新进行启动的计算机重命名。</span><span class="sxs-lookup"><span data-stu-id="fb096-135">Skip reboots triggerd by Computer renames.</span></span> |
| <span data-ttu-id="fb096-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="fb096-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="fb096-137">在 v5 中受支持。</span><span class="sxs-lookup"><span data-stu-id="fb096-137">Supported in v5.</span></span> <span data-ttu-id="fb096-138">作为指定的用户执行资源。</span><span class="sxs-lookup"><span data-stu-id="fb096-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="fb096-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fb096-139">DependsOn</span></span> | <span data-ttu-id="fb096-140">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="fb096-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fb096-141">例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="fb096-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="fb096-142">有关详细信息，请参阅[使用 DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="fb096-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="fb096-143">示例</span><span class="sxs-lookup"><span data-stu-id="fb096-143">Example</span></span>

<span data-ttu-id="fb096-144">下面的示例将安装 Microsoft Exchange 使用[xExchange](https://github.com/PowerShell/xExchange)资源。</span><span class="sxs-lookup"><span data-stu-id="fb096-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="fb096-145">在安装中，整个**xPendingReboot**资源用于重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="fb096-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="fb096-146">此示例需要具有权限才能向林中添加 Exchange server 的帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="fb096-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="fb096-147">有关在 DSC 中使用凭据的详细信息，请参阅[在 DSC 中处理凭据](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="fb096-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="fb096-148">此示例假定已配置本地配置管理器，以允许重新启动并继续重新启动后的配置。</span><span class="sxs-lookup"><span data-stu-id="fb096-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="fb096-149">下载位置</span><span class="sxs-lookup"><span data-stu-id="fb096-149">Where to Download</span></span>

<span data-ttu-id="fb096-150">您可以下载本主题的以下位置，或使用 PowerShell 库中使用的资源。</span><span class="sxs-lookup"><span data-stu-id="fb096-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="fb096-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="fb096-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="fb096-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="fb096-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
