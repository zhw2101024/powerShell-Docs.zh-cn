---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 请求服务器最佳做法
ms.openlocfilehash: 5cb47598b11f7884dddf1440cec21afeab49bebb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417727"
---
# <a name="pull-server-best-practices"></a>请求服务器最佳做法

适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

> [!IMPORTANT]
> 请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划  。 建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](/powershell/scripting/dsc/pull-server/pullserver#community-solutions-for-pull-service)列出的社区解决方案之一。

摘要：本文档旨在包括用于帮助为解决方案进行准备的工程师的过程和可扩展性。 详细信息应提供由客户确定，然后由产品团队验证的最佳做法，以确保建议面向未来并且可视为是稳定的。

| |文档信息|
|:---|:---|
作者 | Michael Greene
审阅者 | Ben Gelens、Ravikanth Chaganti、Aleksandar Nikolic
已发布 | 2015 年 4 月

## <a name="abstract"></a>摘要

本文档旨在为规划 Windows PowerShell 所需状态配置请求服务器实现的任何人提供官方指南。 请求服务器是只应花费几分钟进行部署的简单服务。 虽然本文档会提供可以在部署中使用的技术操作方法指南，不过本文档的价值是作为最佳做法以及在部署之前要考虑的事项的参考。
读者应基本熟悉 DSC 以及用于描述在 DSC 部署中包含的组件的术语。 有关详细信息，请参阅 [Windows PowerShell 所需状态配置概述](/powershell/scripting/dsc/overview)主题。
因为 DSC 预计会随着云一起发展，所以包括请求服务器在内的基础技术也预计会进行发展并引入新功能。 本文档在附录中包含一个版本表，该表提供了对以前版本的参考以及对展望未来的解决方案的参考，以鼓励进行前瞻性设计。

本文档的两个主要部分：

- 配置规划
- 安装指南

### <a name="versions-of-the-windows-management-framework"></a>Windows Management Framework 的版本

本文档中的信息旨在应用于 Windows Management Framework 5.0。 虽然部署和操作请求服务器无需 WMF 5.0，不过版本 5.0 是本文档的重点。

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell 所需状态配置

所需状态配置 (DSC) 是一个管理平台，借助它可以通过使用名为托管对象格式 (MOF) 的行业语法描述通用信息模型 (CIM)，来部署和管理配置数据。 开放式管理基础结构 (OMI) 这一开放源代码项目的存在是为了跨平台（包括 Linux 和网络硬件操作系统）进一步开发这些标准。 有关详细信息，请参阅[链接到 MOF 规范的 DMTF 页面](https://www.dmtf.org/standards/cim)和 [OMI 文档和源](https://collaboration.opengroup.org/omi/documents.php)。

Windows PowerShell 为所需状态配置提供了一组语言扩展，可以用于创建和管理声明性配置。

### <a name="pull-server-role"></a>请求服务器角色

请求服务器提供了一个集中化服务来存储可供目标节点访问的配置。

请求服务器角色可以作为 Web 服务器实例或 SMB 文件共享进行部署。 Web 服务器功能包含一个 OData 接口，并且可以选择包含供目标节点在应用配置时报告返回成功或失败确认的功能。 此功能在存在大量目标节点的环境中非常有用。
配置目标节点（也称为客户端）以指向请求服务器之后，最新配置数据和任何所需脚本会进行下载并应用。 这可以作为一次性部署或作为反复出现的作业（这也使得请求服务器成为用于大规模管理更改的重要资产）来进行。 有关详细信息，请参阅 [Windows PowerShell 所需状态配置请求服务器](/powershell/scripting/dsc/pullServer/pullserver)和

[推送和拉取配置模式](/powershell/scripting/dsc/pullServer/pullserver)。

## <a name="configuration-planning"></a>配置规划

对于任何企业软件部署，都可以提前收集一些信息以规划正确的体系结构以及为完成部署所需的步骤做好准备。 以下各部分提供有关如何进行准备以及可能需要提前进行的组织连接的信息。

### <a name="software-requirements"></a>软件要求

请求服务器的部署需要 Windows Server 的 DSC 服务功能。 此功能是在 Windows Server 2012 中引入的，通过 Windows Management Framework (WMF) 的持续版本进行更新。

### <a name="software-downloads"></a>软件下载

除了从 Windows 更新安装最新内容，还有两个下载被视为用于部署 DSC 请求服务器的最佳做法：Windows Management Framework 的最新版本，以及一个用于自动执行请求服务器预配的 DSC 模块。

### <a name="wmf"></a>WMF

Windows Server 2012 R2 包括一种名为 DSC 服务的功能。 DSC 服务功能提供请求服务器功能，包括支持 OData 终结点的二进制文件。
WMF 包含在 Windows Server 中，在各个 Windows Server 版本之间进行敏捷更新。 [新版本的 WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) 可能包含对 DSC 服务功能的更新。 因此，最佳做法是下载最新版本的 WMF 并查看发行说明以确定该版本是否包含对 DSC 服务功能的更新。 还应查看指示更新或方案的设计状态是列为稳定还是试验性的发行说明部分。
若要允许实现敏捷发行周期，各个功能可以声明为稳定，这指示功能已准备就绪，可以在生产环境中使用（即使 WMF 是以预览版发行）。
历史上一直通过 WMF 版本进行更新的其他功能（请参阅 WMF 发行说明以了解进一步详细信息）：

- Windows PowerShell Windows PowerShell 集成脚本
- 环境 (ISE) Windows PowerShell Web 服务（Management OData
- IIS 扩展）Windows PowerShell 所需状态配置 (DSC)
- Windows 远程管理 (WinRM) Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>DSC 资源

可以通过使用 DSC 配置脚本设置服务来简化请求服务器部署。 本文档包含可以用于部署生产准备就绪服务器节点的配置脚本。 若要使用配置脚本，需要一个未包含在 Windows Server 中的 DSC 模块。 所需模块名称是 **xPSDesiredStateConfiguration**，其中包括 DSC 资源 **xDscWebService**。 可以在[此处](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d)下载 xPSDesiredStateConfiguration 模块。

使用 PowerShellGet  模块中的 `Install-Module` cmdlet。

```powershell
Install-Module xPSDesiredStateConfiguration
```

**PowerShellGet** 模块会将该模块下载到：

`C:\Program Files\Windows PowerShell\Modules`

规划任务|
---|
你是否有权访问 Windows Server 2012 R2 的安装文件？|
部署环境是否可以访问 Internet 以便从联机库下载 WMF 和模块？|
如何在安装操作系统之后安装最新安全更新？|
环境是否可以访问 Internet 以获取更新，或是否具有本地 Windows Server 更新服务 (WSUS) 服务器？|
你是否可以访问已通过脱机注入包含更新的 Windows Server 安装文件？|

### <a name="hardware-requirements"></a>硬件要求

物理和虚拟服务器上都支持请求服务器部署。 请求服务器的大小调整要求与 Windows Server 2012 R2 的要求保持一致。

CPU：1.4 GHz 64 位处理器 内存：512 MB 磁盘空间：32 GB 网络：千兆位以太网适配器

规划任务|
---|
是部署在物理硬件上还是虚拟化平台上？|
为目标环境请求新服务器的过程是什么？|
使服务器可用的平均周转时间是多少？|
请求多大大小的服务器？|

### <a name="accounts"></a>帐户

部署请求服务器实例没有服务帐户要求。
不过在一些情况下，网站可能会在本地用户帐户的上下文中运行。
例如，如果需要访问用于网站内容的存储共享并且承载存储共享的 Windows Server 或设备未加入域。

### <a name="dns-records"></a>DNS 记录

将客户端配置为使用请求服务器环境时，需要使用某个服务器名称。
在测试环境中，通常使用服务器主机名，如果 DNS 名称解析不可用，则可以使用服务器的 IP 地址。
在生产环境中或是在旨在表示生产部署的实验室环境中，最佳做法是创建 DNS CNAME 记录。

DNS CNAME 使你可以创建别名以引用主机 (A) 记录。
附加名称记录的用途是在将来需要更改时提高灵活性。
CNAME 可以帮助隔离客户端配置，以便对服务器环境进行的更改（如替换请求服务器或添加其他请求服务器）无需对客户端配置进行对应更改。

为 DNS 记录选择名称时，请记住解决方案体系结构。
如果使用负载平衡，则用于在 HTTPS 上保护流量安全的证书需要共享与 DNS 记录相同的名称。

方案 |最佳做法
:---|:---
测试环境 |在可能时重现计划生产环境。 服务器主机名适用于简单配置。 如果 DNS 不可用，则可以使用 IP 地址替代主机名。|
单节点部署 |创建指向服务器主机名的 DNS CNAME 记录。|

有关详细信息，请参阅[在 Windows Server 中配置 DNS 轮循机制](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10))。

规划任务|
---|
是否知道与谁联系以创建和更改 DNS 记录？|
针对 DNS 记录的请求的平均周转时间是多少？|
是否需要为服务器请求静态主机名 (A) 记录？|
请求什么内容作为 CNAME？|
如果需要，会使用哪种类型的负载平衡解决方案？ （请参阅标题为“负载平衡”的部分以了解详细信息）|

### <a name="public-key-infrastructure"></a>公钥基础结构

当前大多数组织都要求网络流量（特别是包含诸如如何配置服务器这类敏感数据的流量）在传输过程必须进行验证和/或加密。
虽然可以使用 HTTP（采用明文方便进行客户端请求）部署请求服务器，不过最佳做法是使用 HTTPS 保护流量安全。 可以使用 DSC 资源 **xPSDesiredStateConfiguration** 中的一组参数将服务配置为使用 HTTPS。

保护请求服务器的 HTTPS 流量安全的证书要求与保护任何其他 HTTPS 网站并无不同。 Windows Server 证书服务中的 **Web 服务器**模板满足所需功能。

规划任务|
---|
如果证书请求未自动执行，你需要与谁联系以请求证书？|
请求的平均周转时间是多少？|
证书文件如何传输给你？|
证书私钥如何传输给你？|
默认过期时间是多长？|
是否为请求服务器环境确定了可以用于证书名称的 DNS 名称？|

### <a name="choosing-an-architecture"></a>选择体系结构

可以使用 IIS 上承载的 Web 服务或 SMB 文件共享部署请求服务器。 在大多数情况下，Web 服务选项会提供更高灵活性。 HTTPS 流量经常会穿越网络边界，而在各个网络之间通常会筛选或阻止 SMB 流量。 Web 服务还提供选项以包含一致性服务器或 Web 报表管理器（在本文档的将来版本将讨论这两个主题），从而为客户端提供一种机制，用于将状态报告返回给服务器以便集中查看。
SMB 针对策略规定不应利用 Web 服务器的环境，以及使得不需要 Web 服务器角色的其他环境要求提供了一个选项。
在任一情况下，请记住评估签名和加密流量的要求。 HTTPS、SMB 签名和 IPSEC 策略都是值得考虑的选项。

#### <a name="load-balancing"></a>负载平衡

与 Web 服务进行交互的客户端会针对在单个响应中返回的信息发出请求。 无需连续请求，因此负载平衡平台无需确保在任何时间点都在单台服务器上维持会话。

规划任务|
---|
使用哪种解决方案在服务器间对流量进行负载平衡？|
如果使用硬件负载平衡器，则谁会进行请求以将新配置添加到设备？|
配置新负载平衡 Web 服务的请求的平均周转时间是多少？|
该请求需要哪些信息？|
你是否需要请求附加 IP，或负责进行负载平衡的团队是否会处理该请求？|
你是否具有所需 DNS 记录，以及负责配置负载平衡解决方案的团队是否需要这样？|
负载平衡解决方案是否要求 PKI 由设备进行处理，或是否可以对 HTTPS 流量进行负载平衡（只要没有会话要求）？|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>请求服务器上的暂存配置和模块

作为配置规划的一部分，你需要考虑请求服务器会承载的 DSC 托管模块和配置。 为进行配置规划，需要基本了解如何准备内容并将它部署到请求服务器，这十分重要。

将来，此部分会进行扩展并包含在 DSC 请求服务器的操作指南中。  该指南会讨论使用自动化随时间推移管理模块和配置的日常过程。

#### <a name="dsc-modules"></a>DSC 模块

请求配置的客户端需要所需 DSC 模块。 请求服务器的功能是按需自动将 DSC 模块分发到客户端。 如果你是首次部署请求服务器（可能作为实验室或概念证明），则可能要依赖于可从公共存储库（如 PowerShell 库或用于 DSC 模块的 PowerShell.org GitHub 存储库）获取的 DSC 模块。

请务必记住，即使是对于受信任的联机源（如 PowerShell 库），从公共存储库下载的任何模块在用于生产之前，都应由具有 PowerShell 经验并了解使用模块的环境的人员进行检查。 完成此任务期间，这是检查模块中是否存在可以删除的任何其他负载（如文档和示例脚本）的好时机。 这会在通过网络将模块从服务器下载到客户端时，减少每个客户端在其第一个请求中的网络带宽。

每个模块都必须打包为特定格式（名为 ModuleName_Version.zip 的 ZIP 文件，其中包含模块负载）。 该文件复制到服务器之后，必须创建校验和文件。 客户端连接到服务器时，校验和用于验证 DSC 模块的内容自发布以来未发生更改。

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

规划任务|
---|
如果你在规划测试或实验室环境，则哪些方案是进行验证的关键？|
是否存在包含的资源涵盖你所需的所有内容的公开发布模块，或你是否需要创作自己的资源？|
你的环境是否可以访问 Internet 以检索公共模块？|
谁负责检查 DSC 模块？|
如果你在规划生产环境，则你会使用什么作为本地存储库来用于存储 DSC 模块？|
中心团队是否接受来自应用程序团队的 DSC 模块？ 过程是怎样的？|
是否自动从源存储库打包生产准备就绪 DSC 模块、复制到服务器并为它们创建校验和？|
你的团队是否也负责管理自动化平台？|

#### <a name="dsc-configurations"></a>DSC 配置

请求服务器的用途是提供一种集中式机制，用于将 DSC 配置分发到客户端节点。 配置作为 MOF 文档存储在服务器上。
每个文档都使用唯一的 Guid 进行命名  。 客户端配置为与请求服务器连接时，还会向它们提供它们应请求的配置的 Guid  。 这一通过 Guid 引用配置的系统可保证全局唯一性，并且十分灵活，以便配置可按照每个节点的粒度进行应用，或作为跨应具有相同配置的多台服务器的角色配置  。

#### <a name="guids"></a>Guid

全面考虑请求服务器部署时，规划配置 Guid 值得多加注意  。 对于如何处理 Guid 没有特定要求，该过程可能对于每个环境是唯一的  。 该过程的范围可以从简单到复杂：集中存储的 CSV 文件、简单 SQL 表、CMDB 或需要与其他工具或软件解决方案集成的复杂解决方案。 有两种常规方法：

- **对每台服务器分配 Guid** — 提供一种措施来保证分别控制每台服务器配置。 这提供了更新方面的精度级别，十分适合于包含少量服务器的环境。
- **对每个服务器角色分配 Guid** — 执行相同功能的所有服务器（如 Web 服务器）都使用相同 GUID 引用所需配置数据。  请注意，如果有许多服务器共享相同 GUID，则它们都会在配置更改时同时更新。

  GUID 是应视为敏感数据的信息，因为它可以由具有恶意企图的人员用于获取有关如何在环境中部署和配置服务器的情报。 有关详细信息，请参阅[在 PowerShell Desired State Configuration 拉取模式下安全地分配 Guid](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/)。

规划任务|
---|
谁负责在配置准备就绪时将它们复制到请求服务器文件夹中？|
如果配置由应用程序团队创作，则移交它们的过程是怎样的？|
你是否会在创作配置时，利用存储库在团队间存储配置？|
是否会在配置准备就绪时自动执行将它们复制到服务器并创建校验和的过程？|
如何将 Guid 映射到服务器或角色，以及这会存储在何处？|
你会使用什么过程来配置客户端计算机，以及如何将它与用于创建和存储配置 Guid 的过程集成？|

## <a name="installation-guide"></a>安装指南

*本文档中提供的脚本是稳定示例。在生产环境中执行脚本之前，请始终仔细检查它们。*

### <a name="prerequisites"></a>必备条件

若要验证服务器上的 PowerShell 版本，请使用以下命令。

```powershell
$PSVersionTable.PSVersion
```

如果可能，请升级到 Windows Management Framework 的最新版本。
接下来，使用以下命令下载 `xPsDesiredStateConfiguration` 模块。

```powershell
Install-Module xPSDesiredStateConfiguration
```

该命令会在下载模块之前请求你进行审批。

### <a name="installation-and-configuration-scripts"></a>安装和配置脚本

用于部署 DSC 请求服务器的最佳方法是使用 DSC 配置脚本。 本文档提供的脚本包括仅配置 DSC Web 服务的基本配置和配置 Windows Server 端到端（包括 DSC Web 服务）的高级设置。

注意：当前 `xPSDesiredStateConfiguration` DSC 模块要求服务器是 EN-US 区域设置。

### <a name="basic-configuration-for-windows-server-2012"></a>适用于 Windows Server 2012 的基本配置

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>适用于 Windows Server 2012 R2 的高级配置

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>验证请求服务器功能

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>配置客户端

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>其他参考、代码段和示例

此示例演示如何手动启动客户端连接（需要 WMF5）以进行测试。

```powershell
Update-DscConfiguration –Wait -Verbose
```

[Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet 用于将一种类型的 CNAME 记录添加到 DNS 区域。

用于[创建校验和以及将 DSC MOF 发布到 SMB 请求服务器](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0)的 PowerShell 函数会自动生成所需校验和，然后将 MOF 配置文件和校验和文件都复制到 SMB 请求服务器。

## <a name="appendix---understanding-odata-service-data-file-types"></a>附录 - 了解 ODATA 服务数据文件类型

在包含 OData Web 服务的请求服务器部署过程中，会存储数据文件以创建信息。 文件的类型取决于操作系统，如下所述。

- **Windows Server 2012**：文件类型始终为 .mdb
- **Windows Server 2012 R2**：文件类型默认为 .edb，除非在配置中指定了 .mdb

在用于安装请求服务器的[高级示例脚本](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts)中，还会找到有关如何自动控制 web.config 文件设置以防止文件类型所导致的任何可能错误的示例。
