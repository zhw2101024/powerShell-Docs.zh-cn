---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: 注册 JEA 配置
ms.openlocfilehash: 2c4a8f64c966903a6eb8fcabe4cd25ae7f98b2c4
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522830"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="1be4f-103">注册 JEA 配置</span><span class="sxs-lookup"><span data-stu-id="1be4f-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="1be4f-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1be4f-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1be4f-105">创建[角色功能](role-capabilities.md)和[会话配置文件](session-configurations.md)后，最后一步还需注册 JEA 终结点，然后才能使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="1be4f-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="1be4f-106">此过程将会话配置信息应用于系统，并使终结点可供用户和自动化引擎使用。</span><span class="sxs-lookup"><span data-stu-id="1be4f-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="1be4f-107">单个计算机配置</span><span class="sxs-lookup"><span data-stu-id="1be4f-107">Single machine configuration</span></span>

<span data-ttu-id="1be4f-108">对于小型环境，可以通过使用 [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet 注册会话配置文件来部署 JEA。</span><span class="sxs-lookup"><span data-stu-id="1be4f-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="1be4f-109">在开始之前，请确保已满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="1be4f-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="1be4f-110">已创建一个或多个角色，并已将其放置于有效 PowerShell 模块的“RoleCapabilities”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="1be4f-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="1be4f-111">已创建并测试会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="1be4f-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="1be4f-112">注册 JEA 配置的用户在系统上具有管理员权限。</span><span class="sxs-lookup"><span data-stu-id="1be4f-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="1be4f-113">还需选择 JEA 终结点名称。</span><span class="sxs-lookup"><span data-stu-id="1be4f-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="1be4f-114">用户要连接到使用 JEA 的系统时，将需要 JEA 终结点名称。</span><span class="sxs-lookup"><span data-stu-id="1be4f-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="1be4f-115">可使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet 查看系统上现有终结点的名称。</span><span class="sxs-lookup"><span data-stu-id="1be4f-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="1be4f-116">Windows 通常随附以“microsoft”开头的终结点。</span><span class="sxs-lookup"><span data-stu-id="1be4f-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="1be4f-117">连接到远程 PowerShell 终结点时，使用的是默认终结点“microsoft.powershell”。</span><span class="sxs-lookup"><span data-stu-id="1be4f-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="1be4f-118">如果已确定 JEA 终结点的对应名称，请运行以下命令注册终结点。</span><span class="sxs-lookup"><span data-stu-id="1be4f-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1be4f-119">上述命令将在系统上重启 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="1be4f-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="1be4f-120">这将终止所有 PowerShell 远程处理会话，以及任何正在进行的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="1be4f-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="1be4f-121">建议先脱机操作任何生产计算机，然后再运行命令，以避免中断业务操作。</span><span class="sxs-lookup"><span data-stu-id="1be4f-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="1be4f-122">如果注册成功，便可以开始[使用 JEA](using-jea.md)。</span><span class="sxs-lookup"><span data-stu-id="1be4f-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="1be4f-123">可以随时删除会话配置文件；注册后不会再使用它。</span><span class="sxs-lookup"><span data-stu-id="1be4f-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="1be4f-124">使用 DSC 的多台计算机配置</span><span class="sxs-lookup"><span data-stu-id="1be4f-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="1be4f-125">如果要在多台计算机上部署 JEA，最简单的部署模型是使用 JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) 资源，在每台计算机上快速且一致地部署 JEA。</span><span class="sxs-lookup"><span data-stu-id="1be4f-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="1be4f-126">若要使用 DSC 部署 JEA，需要确保满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="1be4f-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="1be4f-127">已创作一个或多个角色功能并已将其添加到有效的 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="1be4f-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="1be4f-128">包含角色的 PowerShell 模块存储在每台计算机可访问的（只读）文件共享中。</span><span class="sxs-lookup"><span data-stu-id="1be4f-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="1be4f-129">已确定会话配置设置。</span><span class="sxs-lookup"><span data-stu-id="1be4f-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="1be4f-130">使用 JEA DSC 资源时，无需创建会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="1be4f-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="1be4f-131">已获得可在每台计算机上执行管理操作的凭据，或有权访问用于管理计算机的 DSC 请求服务器。</span><span class="sxs-lookup"><span data-stu-id="1be4f-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="1be4f-132">已下载 [JEA DSC 资源](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="1be4f-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="1be4f-133">在目标计算机上创建 JEA 终结点的 DSC 配置，如果正在使用请求服务器，也可在请求服务器上操作。</span><span class="sxs-lookup"><span data-stu-id="1be4f-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="1be4f-134">在此配置中，将使用 JustEnoughAdministration DSC 资源来设置会话配置文件和文件资源，以从文件共享通过角色功能进行复制。</span><span class="sxs-lookup"><span data-stu-id="1be4f-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="1be4f-135">下列属性可使用 DSC 资源进行配置：</span><span class="sxs-lookup"><span data-stu-id="1be4f-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="1be4f-136">角色定义</span><span class="sxs-lookup"><span data-stu-id="1be4f-136">Role Definitions</span></span>
- <span data-ttu-id="1be4f-137">虚拟帐户组</span><span class="sxs-lookup"><span data-stu-id="1be4f-137">Virtual Account groups</span></span>
- <span data-ttu-id="1be4f-138">组托管服务帐户名称</span><span class="sxs-lookup"><span data-stu-id="1be4f-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="1be4f-139">脚本目录</span><span class="sxs-lookup"><span data-stu-id="1be4f-139">Transcript directory</span></span>
- <span data-ttu-id="1be4f-140">用户驱动器</span><span class="sxs-lookup"><span data-stu-id="1be4f-140">User drive</span></span>
- <span data-ttu-id="1be4f-141">条件访问规则</span><span class="sxs-lookup"><span data-stu-id="1be4f-141">Conditional access rules</span></span>
- <span data-ttu-id="1be4f-142">JEA 会话的启动脚本</span><span class="sxs-lookup"><span data-stu-id="1be4f-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="1be4f-143">DSC 配置中的每个属性的语法都与 PowerShell 会话配置文件一致。</span><span class="sxs-lookup"><span data-stu-id="1be4f-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="1be4f-144">以下示例是常规服务器维护模块的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="1be4f-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="1be4f-145">该示例假定包含“RoleCapabilities”子文件夹中的角色功能的有效 PowerShell 模块位于“\\\\myfileshare\\JEA”文件共享中。</span><span class="sxs-lookup"><span data-stu-id="1be4f-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="1be4f-146">随后可在系统上通过[直接调用本地配置管理器](https://msdn.microsoft.com/powershell/dsc/metaconfig)或更新[请求服务器配置](https://msdn.microsoft.com/powershell/dsc/pullserver)应用此配置。</span><span class="sxs-lookup"><span data-stu-id="1be4f-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="1be4f-147">DSC 资源还可以替换默认的 Microsoft.PowerShell 远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="1be4f-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="1be4f-148">如果这样做，资源将自动注册包含默认 WinRM ACL（允许远程管理用户和本地管理员组成员访问）且名为“Microsoft.PowerShell.Restricted”的备份非约束终结点。</span><span class="sxs-lookup"><span data-stu-id="1be4f-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="1be4f-149">注销 JEA 配置</span><span class="sxs-lookup"><span data-stu-id="1be4f-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="1be4f-150">若要删除系统上的 JEA 终结点，请使用 [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1be4f-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="1be4f-151">注销 JEA 终结点将阻止新用户在系统上创建新的 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="1be4f-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="1be4f-152">它还可以使用相同的终结点名称来重新注册更新后的会话配置文件，从而更新 JEA 配置。</span><span class="sxs-lookup"><span data-stu-id="1be4f-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1be4f-153">注销 JEA 终结点将导致重启 WinRM 服务。</span><span class="sxs-lookup"><span data-stu-id="1be4f-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="1be4f-154">这将中断正在进行的大多数远程管理操作，包括其他 PowerShell 会话、WMI 调用和某些管理工具。</span><span class="sxs-lookup"><span data-stu-id="1be4f-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="1be4f-155">请仅在计划的维护时段注销 PowerShell 终结点。</span><span class="sxs-lookup"><span data-stu-id="1be4f-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1be4f-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="1be4f-156">Next steps</span></span>

- [<span data-ttu-id="1be4f-157">测试 JEA 终结点</span><span class="sxs-lookup"><span data-stu-id="1be4f-157">Test the JEA endpoint</span></span>](using-jea.md)