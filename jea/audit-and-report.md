---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: JEA 审核和报告
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188846"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="f7f22-103">JEA 审核和报告</span><span class="sxs-lookup"><span data-stu-id="f7f22-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="f7f22-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f7f22-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f7f22-105">部署 JEA 后，需要定期审核 JEA 配置。</span><span class="sxs-lookup"><span data-stu-id="f7f22-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="f7f22-106">这可帮助你评估有权访问 JEA 终结点的用户是否正确，以及其分配的角色是否仍适用。</span><span class="sxs-lookup"><span data-stu-id="f7f22-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="f7f22-107">本主题介绍了审核 JEA 终结点的各种方法。</span><span class="sxs-lookup"><span data-stu-id="f7f22-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="f7f22-108">查找计算机上已注册的 JEA 会话</span><span class="sxs-lookup"><span data-stu-id="f7f22-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="f7f22-109">若要查看计算机上注册了哪些 JEA 会话，可使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f7f22-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="f7f22-110">“权限”属性中列出了终结点的有效权限。</span><span class="sxs-lookup"><span data-stu-id="f7f22-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="f7f22-111">这些用户有权连接到 JEA 终结点，但他们有权访问的角色（和命令）却是由注册终结点的[会话配置文件](session-configurations.md)中的“RoleDefinitions”字段决定。</span><span class="sxs-lookup"><span data-stu-id="f7f22-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="f7f22-112">可通过扩展“RoleDefinitions”属性中的数据来评估已注册 JEA 终结点中的角色映射。</span><span class="sxs-lookup"><span data-stu-id="f7f22-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="f7f22-113">查找计算机上可用的角色功能</span><span class="sxs-lookup"><span data-stu-id="f7f22-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="f7f22-114">如果角色功能文件存储于有效 PowerShell 模块中的“RoleCapabilities”文件夹中，则仅 JEA 可以使用该文件。</span><span class="sxs-lookup"><span data-stu-id="f7f22-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="f7f22-115">通过搜索可用模块列表，可以查找计算机上可用的所有角色功能。</span><span class="sxs-lookup"><span data-stu-id="f7f22-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="f7f22-116">如果多个角色功能共享同一名称，则此函数的结果顺序无需是选择角色功能的顺序。</span><span class="sxs-lookup"><span data-stu-id="f7f22-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="f7f22-117">查看特定用户的有效权限</span><span class="sxs-lookup"><span data-stu-id="f7f22-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="f7f22-118">设置 JEA 终结点后，建议检查哪些命令对 JEA 会话中的特定用户适用。</span><span class="sxs-lookup"><span data-stu-id="f7f22-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="f7f22-119">如果某个用户以当前组成员身份启动了一个 JEA 会话，可使用 [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) 枚举适用于该用户的所有命令。</span><span class="sxs-lookup"><span data-stu-id="f7f22-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="f7f22-120">`Get-PSSessionCapability` 的输出与 JEA 会话中运行 `Get-Command -CommandType All` 的指定用户的输出完全相同。</span><span class="sxs-lookup"><span data-stu-id="f7f22-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="f7f22-121">如果用户不是将向其授予其他 JEA 权限的组的永久成员，此 cmdlet 可能不会反映这些额外权限。</span><span class="sxs-lookup"><span data-stu-id="f7f22-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="f7f22-122">使用实时 Privileged Access Management 系统允许用户临时隶属于安全组时，通常就是这种情况。</span><span class="sxs-lookup"><span data-stu-id="f7f22-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="f7f22-123">始终仔细评估用户到角色的映射和每个角色的内容，以确保用户仅有权访问成功完成其作业所需的必要命令。</span><span class="sxs-lookup"><span data-stu-id="f7f22-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="f7f22-124">PowerShell 事件日志</span><span class="sxs-lookup"><span data-stu-id="f7f22-124">PowerShell event logs</span></span>

<span data-ttu-id="f7f22-125">如果在系统上启用了模块和/或脚本块日志记录，则可以针对每个用户在其 JEA 会话中运行的每条命令，在 Windows 事件日志中查找相应事件。</span><span class="sxs-lookup"><span data-stu-id="f7f22-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="f7f22-126">若要查找这些事件，打开 Windows 事件查看器，导航到“Microsoft-Windows-PowerShell/Operational”事件日志，然后查找事件 ID 为 **4104** 的事件。</span><span class="sxs-lookup"><span data-stu-id="f7f22-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="f7f22-127">每个事件日志条目都将包括在其中运行命令的会话的相关信息。</span><span class="sxs-lookup"><span data-stu-id="f7f22-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="f7f22-128">对于 JEA 会话，这包括有关 **ConnectedUser**即创建 JEA 会话的实际用户和 **RunAsUser**（标识用于执行命令的 JEA 帐户）的重要信息。</span><span class="sxs-lookup"><span data-stu-id="f7f22-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="f7f22-129">应用程序事件日志将显示 RunAsUser 正在进行的更改，因此启用记录或模块/脚本日志记录对跟踪用户的特定命令回调至关重要。</span><span class="sxs-lookup"><span data-stu-id="f7f22-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="f7f22-130">应用程序事件日志</span><span class="sxs-lookup"><span data-stu-id="f7f22-130">Application event logs</span></span>

<span data-ttu-id="f7f22-131">在与外部应用程序或服务交互的 JEA 会话中运行命令时，这些应用程序可能会将事件记录为其自己的事件日志。</span><span class="sxs-lookup"><span data-stu-id="f7f22-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="f7f22-132">与 PowerShell 日志和脚本不同，其他日志记录机制不会捕获 JEA 会话的已连接用户，而只记录虚拟运行身份用户或组托管服务帐户。</span><span class="sxs-lookup"><span data-stu-id="f7f22-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="f7f22-133">若要确定运行该命令的用户，需要参考[会话脚本](#session-transcripts)或相关 PowerShell 事件日志以及在应用程序事件日志中显示的时间和用户。</span><span class="sxs-lookup"><span data-stu-id="f7f22-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="f7f22-134">WinRM 日志还可帮助将应用程序事件日志中的运行身份用户与连接用户相关联。</span><span class="sxs-lookup"><span data-stu-id="f7f22-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="f7f22-135">**Microsoft-Windows-Windows Remote Management/Operational** 日志中 ID 为 **193** 的事件记录了每次创建 JEA 会话时，连接用户和运行身份用户的安全标识符 (SID) 和帐户名称。</span><span class="sxs-lookup"><span data-stu-id="f7f22-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="f7f22-136">会话脚本</span><span class="sxs-lookup"><span data-stu-id="f7f22-136">Session transcripts</span></span>

<span data-ttu-id="f7f22-137">如果已将 JEA 配置为为每个用户会话创建脚本，每个用户操作的文本副本将存储在指定的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f7f22-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="f7f22-138">若要查找所有脚本目录，可在使用 JEA 配置的计算机上以管理员身份运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="f7f22-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="f7f22-139">每个脚本的开头部分都包含以下内容：会话开始时间、连接到会话的用户和分配给用户的 JEA 标识。</span><span class="sxs-lookup"><span data-stu-id="f7f22-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="f7f22-140">记录的正文记录的是用户调用的每个命令的相关信息。</span><span class="sxs-lookup"><span data-stu-id="f7f22-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="f7f22-141">考虑到针对 PowerShell 远程处理的命令转换方式，用户运行命令的确切语法在 JEA 会话中不适用，但仍可确定已执行的有效命令。</span><span class="sxs-lookup"><span data-stu-id="f7f22-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="f7f22-142">以下示例是来自 JEA 会话中运行 `Get-Service Dns` 的用户的脚本代码段：</span><span class="sxs-lookup"><span data-stu-id="f7f22-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="f7f22-143">对于用户运行的每个命令，都将编写“CommandInvocation”行，用于描述用户调用的 cmdlet 或函数。</span><span class="sxs-lookup"><span data-stu-id="f7f22-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="f7f22-144">ParameterBindings 遵循每个 CommandInvocation，介绍使用该命令提供的每个参数和值。</span><span class="sxs-lookup"><span data-stu-id="f7f22-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="f7f22-145">在上述示例中，你可以看到针对“Get-Service”向“Name”参数提供了值“Dns”。</span><span class="sxs-lookup"><span data-stu-id="f7f22-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="f7f22-146">每个命令的输出通常还会对 Out-Default 触发 CommandInvocation。</span><span class="sxs-lookup"><span data-stu-id="f7f22-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="f7f22-147">Out-Default 的 InputObject 是从命令返回的 PowerShell 对象。</span><span class="sxs-lookup"><span data-stu-id="f7f22-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="f7f22-148">该对象的详细信息如下面几行所示，严格模拟用户将看到的内容。</span><span class="sxs-lookup"><span data-stu-id="f7f22-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7f22-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7f22-149">See also</span></span>

- [<span data-ttu-id="f7f22-150">审核 JEA 会话中的用户操作</span><span class="sxs-lookup"><span data-stu-id="f7f22-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="f7f22-151">PowerShell ♥ the Blue Team 关于安全的博客文章</span><span class="sxs-lookup"><span data-stu-id="f7f22-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)