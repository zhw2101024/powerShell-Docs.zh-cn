---
ms.date: 08/15/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于 Windows 的 Desired State Configuration (DSC) 入门
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988882"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="240bd-103">适用于 Windows 的 Desired State Configuration (DSC) 入门</span><span class="sxs-lookup"><span data-stu-id="240bd-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="240bd-104">本主题介绍了如何开始使用适用于 Windows 的 PowerShell Desired State Configuration (DSC)。</span><span class="sxs-lookup"><span data-stu-id="240bd-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="240bd-105">有关 DSC 的常规信息，请参阅 [Windows PowerShell Desired State Configuration 入门](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="240bd-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="240bd-106">支持的 Windows 操作系统版本</span><span class="sxs-lookup"><span data-stu-id="240bd-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="240bd-107">支持以下版本：</span><span class="sxs-lookup"><span data-stu-id="240bd-107">The following versions are supported:</span></span>

- <span data-ttu-id="240bd-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="240bd-108">Windows Server 2019</span></span>
- <span data-ttu-id="240bd-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="240bd-109">Windows Server 2016</span></span>
- <span data-ttu-id="240bd-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="240bd-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="240bd-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="240bd-111">Windows Server 2012</span></span>
- <span data-ttu-id="240bd-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="240bd-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="240bd-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="240bd-113">Windows 10</span></span>
- <span data-ttu-id="240bd-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="240bd-114">Windows 8.1</span></span>
- <span data-ttu-id="240bd-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="240bd-115">Windows 7</span></span>

<span data-ttu-id="240bd-116">由于 [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) 独立产品 SKU 不包含 Desired State Configuraion 实现，因此无法由 PowerShell DSC 或 Azure Automation State Configuration 管理。</span><span class="sxs-lookup"><span data-stu-id="240bd-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="240bd-117">安装 DSC</span><span class="sxs-lookup"><span data-stu-id="240bd-117">Installing DSC</span></span>

<span data-ttu-id="240bd-118">PowerShell Desired State Configuration 包含在 Windows 中，并通过 Windows Management Framework 进行更新。</span><span class="sxs-lookup"><span data-stu-id="240bd-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="240bd-119">最新版本为 [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)。</span><span class="sxs-lookup"><span data-stu-id="240bd-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="240bd-120">无需启用 Windows Server 功能“DSC 服务”，即可使用 DSC 管理计算机。</span><span class="sxs-lookup"><span data-stu-id="240bd-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="240bd-121">只有在生成 Windows 拉取服务器实例时，才需要此功能。</span><span class="sxs-lookup"><span data-stu-id="240bd-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="240bd-122">使用适用于 Windows 的 DSC</span><span class="sxs-lookup"><span data-stu-id="240bd-122">Using DSC for Windows</span></span>

<span data-ttu-id="240bd-123">下面几个部分介绍了如何在 Windows 计算机上创建和运行 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="240bd-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="240bd-124">创建配置 MOF 文档</span><span class="sxs-lookup"><span data-stu-id="240bd-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="240bd-125">Windows PowerShell Configuration 关键字用于创建配置。</span><span class="sxs-lookup"><span data-stu-id="240bd-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="240bd-126">下面逐步介绍了如何使用 Windows PowerShell 创建配置文档。</span><span class="sxs-lookup"><span data-stu-id="240bd-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="240bd-127">定义配置并生成配置文档：</span><span class="sxs-lookup"><span data-stu-id="240bd-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="240bd-128">安装包含 DSC 资源的模块</span><span class="sxs-lookup"><span data-stu-id="240bd-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="240bd-129">Windows PowerShell Desired State Configuration 有包含 DSC 资源的内置模块。</span><span class="sxs-lookup"><span data-stu-id="240bd-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="240bd-130">也可以使用 PowerShellGet cmdlet 从 PowerShell 库等外部源加载模块。</span><span class="sxs-lookup"><span data-stu-id="240bd-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="240bd-131">将配置应用于计算机</span><span class="sxs-lookup"><span data-stu-id="240bd-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="240bd-132">可以使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet，将配置文档（MOF 文件）应用于计算机。</span><span class="sxs-lookup"><span data-stu-id="240bd-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="240bd-133">获取配置的当前状态</span><span class="sxs-lookup"><span data-stu-id="240bd-133">Get the current state of the configuration</span></span>

<span data-ttu-id="240bd-134">[Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet 可查询计算机的当前状态，并返回配置的当前值。</span><span class="sxs-lookup"><span data-stu-id="240bd-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="240bd-135">[Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet 可返回应用于计算机的当前元配置。</span><span class="sxs-lookup"><span data-stu-id="240bd-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="240bd-136">从计算机中删除当前配置</span><span class="sxs-lookup"><span data-stu-id="240bd-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="240bd-137">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="240bd-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="240bd-138">在本地配置管理器中配置设置</span><span class="sxs-lookup"><span data-stu-id="240bd-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="240bd-139">使用 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet 将元配置 MOF 文件应用于计算机。</span><span class="sxs-lookup"><span data-stu-id="240bd-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="240bd-140">需要元配置 MOF 的路径。</span><span class="sxs-lookup"><span data-stu-id="240bd-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="240bd-141">Windows PowerShell Desired State Configuration 日志文件</span><span class="sxs-lookup"><span data-stu-id="240bd-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="240bd-142">DSC 日志写入 Windows 事件日志，路径为 `Microsoft-Windows-Dsc/Operational`。</span><span class="sxs-lookup"><span data-stu-id="240bd-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="240bd-143">可以按照 [DSC 事件日志位置](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)中的步骤操作，启用其他日志用于调试目的。</span><span class="sxs-lookup"><span data-stu-id="240bd-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
