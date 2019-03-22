---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用 DSC 报表服务器
ms.openlocfilehash: 73208477a74ff3c615d7d515fcad555beabe8f32
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059263"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="d471d-103">使用 DSC 报表服务器</span><span class="sxs-lookup"><span data-stu-id="d471d-103">Using a DSC report server</span></span>

<span data-ttu-id="d471d-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d471d-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d471d-105">请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。</span><span class="sxs-lookup"><span data-stu-id="d471d-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="d471d-106">建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="d471d-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="d471d-107">本主题中描述的报表服务器在 PowerShell 4.0 中不可用。</span><span class="sxs-lookup"><span data-stu-id="d471d-107">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="d471d-108">可将节点的本地配置管理器 (LCM) 配置为向请求服务器发送有关其配置状态的报表，然后即可查询该服务器以检索此数据。</span><span class="sxs-lookup"><span data-stu-id="d471d-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="d471d-109">每当节点检查和应用配置时，它都会将报表发送到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="d471d-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="d471d-110">这些报表存储在服务器上的数据库中，可通过调用报告 Web 服务进行检索。</span><span class="sxs-lookup"><span data-stu-id="d471d-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="d471d-111">每个报表中包含所应用的配置、配置是否成功、所使用的资源、引发的所有错误以及开始时间和结束时间等信息。</span><span class="sxs-lookup"><span data-stu-id="d471d-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="d471d-112">将节点配置为发送报表</span><span class="sxs-lookup"><span data-stu-id="d471d-112">Configuring a node to send reports</span></span>

<span data-ttu-id="d471d-113">使用节点上 LCM 配置中的 **ReportServerWeb** 块可指示节点将报表发送到服务器（若要了解如何配置 LCM，请参阅[配置本地配置管理器](../managing-nodes/metaConfig.md)）。</span><span class="sxs-lookup"><span data-stu-id="d471d-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="d471d-114">必须将节点向其发送报表的服务器设置为 Web 请求服务器（不能将报表发送到 SMB 共享）。</span><span class="sxs-lookup"><span data-stu-id="d471d-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="d471d-115">有关设置请求服务器的信息，请参阅[设置 DSC 请求服务器](pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="d471d-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="d471d-116">报表服务器可以是节点从中请求配置和获取资源的同一服务，也可以是不同服务。</span><span class="sxs-lookup"><span data-stu-id="d471d-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="d471d-117">在 **ReportServerWeb** 块中，指定请求服务的 URL 和服务器已知的注册密钥。</span><span class="sxs-lookup"><span data-stu-id="d471d-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="d471d-118">以下配置将节点配置为从一项服务请求配置，并将报表发送到另一台服务器上的服务。</span><span class="sxs-lookup"><span data-stu-id="d471d-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="d471d-119">以下配置将节点配置为将单个服务器用于配置、资源和报告。</span><span class="sxs-lookup"><span data-stu-id="d471d-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> <span data-ttu-id="d471d-120">在设置请求服务器时可以将 Web 服务命名为任何所需形式，但是 ServerURL 属性必须与服务名称匹配。</span><span class="sxs-lookup"><span data-stu-id="d471d-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="d471d-121">获取报表数据</span><span class="sxs-lookup"><span data-stu-id="d471d-121">Getting report data</span></span>

<span data-ttu-id="d471d-122">发送到请求服务器的报表将被输入该服务器上的数据库。</span><span class="sxs-lookup"><span data-stu-id="d471d-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="d471d-123">通过调用 Web 服务即可使用这些报表。</span><span class="sxs-lookup"><span data-stu-id="d471d-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="d471d-124">若要检索特定节点的报表，请通过以下形式向报表 Web 服务发送 HTTP 请求：`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span><span class="sxs-lookup"><span data-stu-id="d471d-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span></span>
<span data-ttu-id="d471d-125">其中 `MyNodeAgentId` 是你想要获取其报表的节点的 AgentId。</span><span class="sxs-lookup"><span data-stu-id="d471d-125">where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="d471d-126">可通过在节点上调用 [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) 来获取相应节点的 AgentID。</span><span class="sxs-lookup"><span data-stu-id="d471d-126">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="d471d-127">报表将返回为 JSON 对象数组。</span><span class="sxs-lookup"><span data-stu-id="d471d-127">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="d471d-128">以下脚本将返回其运行于的节点的报表：</span><span class="sxs-lookup"><span data-stu-id="d471d-128">The following script returns the reports for the node on which it is run:</span></span>

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)", 
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a><span data-ttu-id="d471d-129">查看报表数据</span><span class="sxs-lookup"><span data-stu-id="d471d-129">Viewing report data</span></span>

<span data-ttu-id="d471d-130">如果将变量设置为 **GetReport** 函数的结果，就可以查看所返回数组元素中的各个字段：</span><span class="sxs-lookup"><span data-stu-id="d471d-130">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

<span data-ttu-id="d471d-131">默认情况下，报表按 **JobID** 排序。</span><span class="sxs-lookup"><span data-stu-id="d471d-131">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="d471d-132">若要获取最新报表，可以按 **StartTime** 属性对其进行降序排序，然后获取数组的第一个元素：</span><span class="sxs-lookup"><span data-stu-id="d471d-132">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="d471d-133">请注意，**StatusData** 属性是具有多个属性的对象。</span><span class="sxs-lookup"><span data-stu-id="d471d-133">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="d471d-134">这是大部分报表数据所在的位置。</span><span class="sxs-lookup"><span data-stu-id="d471d-134">This is where much of the reporting data is.</span></span> <span data-ttu-id="d471d-135">让我们来看看最新报表的 **StatusData** 属性的各个字段：</span><span class="sxs-lookup"><span data-stu-id="d471d-135">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

<span data-ttu-id="d471d-136">此外，这表明最新配置调用了两种资源，其中之一处于所需状态，而另一个没有。</span><span class="sxs-lookup"><span data-stu-id="d471d-136">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="d471d-137">你可以获取 **ResourcesNotInDesiredState** 属性的可读性更强的输出：</span><span class="sxs-lookup"><span data-stu-id="d471d-137">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

<span data-ttu-id="d471d-138">请注意，这些示例旨在让你了解如何使用报表数据。</span><span class="sxs-lookup"><span data-stu-id="d471d-138">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="d471d-139">有关在 PowerShell 中使用 JSON 的介绍，请参阅 [Playing with JSON and PowerShell（使用 JSON 和 PowerShell）](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/)。</span><span class="sxs-lookup"><span data-stu-id="d471d-139">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="d471d-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d471d-140">See Also</span></span>

[<span data-ttu-id="d471d-141">配置本地配置管理器</span><span class="sxs-lookup"><span data-stu-id="d471d-141">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="d471d-142">设置 DSC Web 请求服务器</span><span class="sxs-lookup"><span data-stu-id="d471d-142">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="d471d-143">使用配置名称设置请求客户端</span><span class="sxs-lookup"><span data-stu-id="d471d-143">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)