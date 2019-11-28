---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: 注册 JEA 配置
ms.openlocfilehash: dbed5c7dd71f2f7a09d97416be56dff675799548
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417614"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="0820f-103">注册 JEA 配置</span><span class="sxs-lookup"><span data-stu-id="0820f-103">Registering JEA Configurations</span></span>

<span data-ttu-id="0820f-104">创建[角色功能](role-capabilities.md)和[会话配置文件](session-configurations.md)后，最后一步是注册 JEA 终结点。</span><span class="sxs-lookup"><span data-stu-id="0820f-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="0820f-105">向系统注册 JEA 终结点，使终结点可供用户和自动化引擎使用。</span><span class="sxs-lookup"><span data-stu-id="0820f-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="0820f-106">单个计算机配置</span><span class="sxs-lookup"><span data-stu-id="0820f-106">Single machine configuration</span></span>

<span data-ttu-id="0820f-107">对于小型环境，可以通过使用 [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet 注册会话配置文件来部署 JEA。</span><span class="sxs-lookup"><span data-stu-id="0820f-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="0820f-108">在开始之前，请确保已满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="0820f-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="0820f-109">已创建一个或多个角色，且已将其放置在 PowerShell 模块的“RoleCapabilities”文件夹中  。</span><span class="sxs-lookup"><span data-stu-id="0820f-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="0820f-110">已创建并测试会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="0820f-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="0820f-111">注册 JEA 配置的用户在系统上具有管理员权限。</span><span class="sxs-lookup"><span data-stu-id="0820f-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="0820f-112">已选择 JEA 终结点的名称。</span><span class="sxs-lookup"><span data-stu-id="0820f-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="0820f-113">用户使用 JEA 连接到系统时，将需要 JEA 终结点名称。</span><span class="sxs-lookup"><span data-stu-id="0820f-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="0820f-114">[Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 列出系统上终结点的名称。</span><span class="sxs-lookup"><span data-stu-id="0820f-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="0820f-115">Windows 通常随附以 `microsoft` 开头的终结点。</span><span class="sxs-lookup"><span data-stu-id="0820f-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="0820f-116">`microsoft.powershell` 终结点是连接到远程 PowerShell 终结点时使用的默认终结点。</span><span class="sxs-lookup"><span data-stu-id="0820f-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="0820f-117">运行以下命令来注册终结点。</span><span class="sxs-lookup"><span data-stu-id="0820f-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="0820f-118">上一命令将在系统上重启 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="0820f-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="0820f-119">这将终止所有 PowerShell 远程处理会话，以及所有正在进行的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="0820f-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="0820f-120">建议先将生产计算机脱机，然后再运行命令，以避免中断业务操作。</span><span class="sxs-lookup"><span data-stu-id="0820f-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="0820f-121">注册后即可[使用 JEA](using-jea.md) 了。</span><span class="sxs-lookup"><span data-stu-id="0820f-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="0820f-122">可随时删除会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="0820f-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="0820f-123">注册终结点后不再使用该配置文件。</span><span class="sxs-lookup"><span data-stu-id="0820f-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="0820f-124">使用 DSC 的多台计算机配置</span><span class="sxs-lookup"><span data-stu-id="0820f-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="0820f-125">在多台计算机上部署 JEA 时，最简单的部署模型使用 JEA [Desired State Configuration (DSC)](/powershell/scripting/dsc/overview) 资源，在每台计算机上快速且一致地部署 JEA。</span><span class="sxs-lookup"><span data-stu-id="0820f-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/scripting/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="0820f-126">要使用 DSC 部署 JEA，请确保满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="0820f-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="0820f-127">已创作一个或多个角色功能并已将其添加到 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="0820f-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="0820f-128">包含角色的 PowerShell 模块存储在每台计算机可访问的（只读）文件共享中。</span><span class="sxs-lookup"><span data-stu-id="0820f-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="0820f-129">已确定会话配置设置。</span><span class="sxs-lookup"><span data-stu-id="0820f-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="0820f-130">使用 JEA DSC 资源时，无需创建会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="0820f-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="0820f-131">已获得允许在每台计算机上执行管理操作的凭据，或有权访问用于管理计算机的 DSC 拉取服务器。</span><span class="sxs-lookup"><span data-stu-id="0820f-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="0820f-132">已下载 [JEA DSC 资源](https://github.com/powershell/JEA/tree/master/DSC%20Resource)。</span><span class="sxs-lookup"><span data-stu-id="0820f-132">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="0820f-133">在目标计算机或拉取服务器上创建 JEA 终结点的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="0820f-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="0820f-134">在此配置中，JustEnoughAdministration DSC 资源定义会话配置文件，文件资源从文件共享复制角色功能   。</span><span class="sxs-lookup"><span data-stu-id="0820f-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="0820f-135">下列属性可使用 DSC 资源进行配置：</span><span class="sxs-lookup"><span data-stu-id="0820f-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="0820f-136">角色定义</span><span class="sxs-lookup"><span data-stu-id="0820f-136">Role Definitions</span></span>
- <span data-ttu-id="0820f-137">虚拟帐户组</span><span class="sxs-lookup"><span data-stu-id="0820f-137">Virtual account groups</span></span>
- <span data-ttu-id="0820f-138">组托管服务帐户名称</span><span class="sxs-lookup"><span data-stu-id="0820f-138">Group-managed service account name</span></span>
- <span data-ttu-id="0820f-139">脚本目录</span><span class="sxs-lookup"><span data-stu-id="0820f-139">Transcript directory</span></span>
- <span data-ttu-id="0820f-140">用户驱动器</span><span class="sxs-lookup"><span data-stu-id="0820f-140">User drive</span></span>
- <span data-ttu-id="0820f-141">条件访问规则</span><span class="sxs-lookup"><span data-stu-id="0820f-141">Conditional access rules</span></span>
- <span data-ttu-id="0820f-142">JEA 会话的启动脚本</span><span class="sxs-lookup"><span data-stu-id="0820f-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="0820f-143">DSC 配置中的每个属性的语法都与 PowerShell 会话配置文件一致。</span><span class="sxs-lookup"><span data-stu-id="0820f-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="0820f-144">以下示例是常规服务器维护模块的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="0820f-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="0820f-145">它假定包含角色功能的有效 PowerShell 模块位于 `\\myfileshare\JEA` 文件共享中。</span><span class="sxs-lookup"><span data-stu-id="0820f-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="0820f-146">接下来，可在系统上直接调用[本地配置管理器](/powershell/scripting/dsc/managing-nodes/metaConfig)或更新[拉取服务器配置](/powershell/scripting/dsc/pull-server/pullServer)来应用此配置。</span><span class="sxs-lookup"><span data-stu-id="0820f-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="0820f-147">通过 DSC 资源，还可替换默认的 Microsoft.PowerShell 终结点  。</span><span class="sxs-lookup"><span data-stu-id="0820f-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="0820f-148">替换时，资源会自动注册一个名为 Microsoft.PowerShell.Restricted 的备份终结点  。</span><span class="sxs-lookup"><span data-stu-id="0820f-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="0820f-149">备份终结点具有默认 WinRM ACL，允许远程管理用户和本地管理员组成员对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="0820f-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="0820f-150">注销 JEA 配置</span><span class="sxs-lookup"><span data-stu-id="0820f-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="0820f-151">[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet 删除 JEA 终结点。</span><span class="sxs-lookup"><span data-stu-id="0820f-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="0820f-152">注销 JEA 终结点将阻止新用户在系统上创建新的 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="0820f-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="0820f-153">它还可以使用相同的终结点名称来重新注册更新后的会话配置文件，从而更新 JEA 配置。</span><span class="sxs-lookup"><span data-stu-id="0820f-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="0820f-154">注销 JEA 终结点将导致 WinRM 服务重启。</span><span class="sxs-lookup"><span data-stu-id="0820f-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="0820f-155">这将中断正在进行的大多数远程管理操作，包括其他 PowerShell 会话、WMI 调用和某些管理工具。</span><span class="sxs-lookup"><span data-stu-id="0820f-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="0820f-156">请仅在计划的维护时段注销 PowerShell 终结点。</span><span class="sxs-lookup"><span data-stu-id="0820f-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0820f-157">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0820f-157">Next steps</span></span>

[<span data-ttu-id="0820f-158">测试 JEA 终结点</span><span class="sxs-lookup"><span data-stu-id="0820f-158">Test the JEA endpoint</span></span>](using-jea.md)
