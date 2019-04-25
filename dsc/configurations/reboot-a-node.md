---
ms.date: 1/17/2019
keywords: dsc,powershell,配置,安装程序
title: 重新启动节点
ms.openlocfilehash: 015b82a32caefc420973651c72e272fd85baf880
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080112"
---
# <a name="reboot-a-node"></a><span data-ttu-id="81877-103">重新启动节点</span><span class="sxs-lookup"><span data-stu-id="81877-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="81877-104">本主题讨论如何重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="81877-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="81877-105">若要使重新启动成功，需要正确配置 ActionAfterReboot 和 RebootNodeIfNeeded LCM 设置。</span><span class="sxs-lookup"><span data-stu-id="81877-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="81877-106">若要了解本地配置管理器设置，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)或[配置本地配置管理器 (v4)](../managing-nodes/metaConfig4.md)。</span><span class="sxs-lookup"><span data-stu-id="81877-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="81877-107">可以使用 `$global:DSCMachineStatus` 标志，从资源中重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="81877-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="81877-108">在 `Set-TargetResource` 函数中将此标志设置为 `1` 会强制 LCM 在当前资源的 Set 方法之后直接重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="81877-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="81877-109">使用此标志时，xPendingReboot 资源会检测重新启动是否在 DSC 外部挂起。</span><span class="sxs-lookup"><span data-stu-id="81877-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="81877-110">[配置](configurations.md)可能会执行需要重新启动节点的步骤。</span><span class="sxs-lookup"><span data-stu-id="81877-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="81877-111">这可能包括诸如以下这类情况：</span><span class="sxs-lookup"><span data-stu-id="81877-111">This could include things such as:</span></span>

- <span data-ttu-id="81877-112">Windows 更新</span><span class="sxs-lookup"><span data-stu-id="81877-112">Windows updates</span></span>
- <span data-ttu-id="81877-113">安装软件</span><span class="sxs-lookup"><span data-stu-id="81877-113">Software install</span></span>
- <span data-ttu-id="81877-114">文件重命名</span><span class="sxs-lookup"><span data-stu-id="81877-114">File renames</span></span>
- <span data-ttu-id="81877-115">计算机重命名</span><span class="sxs-lookup"><span data-stu-id="81877-115">Computer rename</span></span>

<span data-ttu-id="81877-116">xPendingReboot 资源会检查特定计算机位置，以确定重新启动是否挂起。</span><span class="sxs-lookup"><span data-stu-id="81877-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="81877-117">如果节点需要在 DSC 外部重新启动，则 xPendingReboot 资源会将 `$global:DSCMachineStatus` 标志设置为 `1`，从而强制重新启动并解决挂起条件。</span><span class="sxs-lookup"><span data-stu-id="81877-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="81877-118">任何 DSC 资源都可以通过在 `Set-TargetResource` 函数中设置此标志，来指示 LCM 重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="81877-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="81877-119">有关详细信息，请参阅[使用 MOF 编写自定义 DSC 资源](../resources/authoringResourceMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="81877-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="81877-120">语法</span><span class="sxs-lookup"><span data-stu-id="81877-120">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="81877-121">“属性”</span><span class="sxs-lookup"><span data-stu-id="81877-121">Properties</span></span>

| <span data-ttu-id="81877-122">属性</span><span class="sxs-lookup"><span data-stu-id="81877-122">Property</span></span> | <span data-ttu-id="81877-123">说明</span><span class="sxs-lookup"><span data-stu-id="81877-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="81877-124">名称</span><span class="sxs-lookup"><span data-stu-id="81877-124">Name</span></span>| <span data-ttu-id="81877-125">必需参数，对配置中资源的每个实例必须唯一。</span><span class="sxs-lookup"><span data-stu-id="81877-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="81877-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="81877-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="81877-127">跳过由基于组件的服务组件触发的重新启动。</span><span class="sxs-lookup"><span data-stu-id="81877-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="81877-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="81877-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="81877-129">跳过由 Windows 更新触发的重新启动。</span><span class="sxs-lookup"><span data-stu-id="81877-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="81877-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="81877-130">SkipPendingFileRename</span></span> | <span data-ttu-id="81877-131">跳过挂起文件重命名重新启动。</span><span class="sxs-lookup"><span data-stu-id="81877-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="81877-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="81877-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="81877-133">跳过由 ConfigMgr 客户端触发的重新启动。</span><span class="sxs-lookup"><span data-stu-id="81877-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="81877-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="81877-134">SkipComputerRename</span></span> | <span data-ttu-id="81877-135">跳过由计算机重命名触发的重新启动。</span><span class="sxs-lookup"><span data-stu-id="81877-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="81877-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="81877-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="81877-137">在 v5 中受支持。</span><span class="sxs-lookup"><span data-stu-id="81877-137">Supported in v5.</span></span> <span data-ttu-id="81877-138">以指定用户身份执行资源。</span><span class="sxs-lookup"><span data-stu-id="81877-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="81877-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="81877-139">DependsOn</span></span> | <span data-ttu-id="81877-140">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="81877-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="81877-141">例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="81877-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="81877-142">有关详细信息，请参阅[使用 DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="81877-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="81877-143">示例</span><span class="sxs-lookup"><span data-stu-id="81877-143">Example</span></span>

<span data-ttu-id="81877-144">下面的示例使用 [xExchange](https://github.com/PowerShell/xExchange) 资源安装 Microsoft Exchange。</span><span class="sxs-lookup"><span data-stu-id="81877-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="81877-145">在整个安装过程中，xPendingReboot 资源用于重新启动节点。</span><span class="sxs-lookup"><span data-stu-id="81877-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="81877-146">此示例需要有权向林中添加 Exchange 服务器的帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="81877-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="81877-147">有关在 DSC 中使用凭据的详细信息，请参阅[在 DSC 中处理凭据](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="81877-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
> <span data-ttu-id="81877-148">此示例假设已将本地配置管理器配置为允许重新启动并在重新启动之后继续配置。</span><span class="sxs-lookup"><span data-stu-id="81877-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="81877-149">下载位置</span><span class="sxs-lookup"><span data-stu-id="81877-149">Where to Download</span></span>

<span data-ttu-id="81877-150">可以在以下位置或使用 PowerShell 库下载本主题中使用的资源。</span><span class="sxs-lookup"><span data-stu-id="81877-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="81877-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="81877-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="81877-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="81877-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
