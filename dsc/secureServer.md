---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: 请求服务器最佳做法
ms.openlocfilehash: d8d8667e2fc608e0c5948a0b5046bf92801b49db
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="ab635-103">请求服务器最佳做法</span><span class="sxs-lookup"><span data-stu-id="ab635-103">Pull server best practices</span></span>

><span data-ttu-id="ab635-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ab635-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab635-105">请求服务器（Windows 功能 DSC-Service）是 Windows Server 的一个受支持组件，不过目前没有提供新功能的计划。</span><span class="sxs-lookup"><span data-stu-id="ab635-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="ab635-106">建议开始将托管客户端转换至 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)（包括 Windows Server 上的请求服务器以外的功能）或[此处](pullserver.md#community-solutions-for-pull-service)列出的社区解决方案之一。</span><span class="sxs-lookup"><span data-stu-id="ab635-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="ab635-107">摘要：本文档旨在包括用于帮助为解决方案进行准备的工程师的过程和可扩展性。</span><span class="sxs-lookup"><span data-stu-id="ab635-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="ab635-108">详细信息应提供由客户确定，然后由产品团队验证的最佳做法，以确保建议面向未来并且可视为是稳定的。</span><span class="sxs-lookup"><span data-stu-id="ab635-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="ab635-109">文档信息</span><span class="sxs-lookup"><span data-stu-id="ab635-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="ab635-110">作者</span><span class="sxs-lookup"><span data-stu-id="ab635-110">Author</span></span> | <span data-ttu-id="ab635-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="ab635-111">Michael Greene</span></span>
<span data-ttu-id="ab635-112">审阅者</span><span class="sxs-lookup"><span data-stu-id="ab635-112">Reviewers</span></span> | <span data-ttu-id="ab635-113">Ben Gelens、Ravikanth Chaganti、Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="ab635-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="ab635-114">已发布</span><span class="sxs-lookup"><span data-stu-id="ab635-114">Published</span></span> | <span data-ttu-id="ab635-115">2015 年 4 月</span><span class="sxs-lookup"><span data-stu-id="ab635-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="ab635-116">摘要</span><span class="sxs-lookup"><span data-stu-id="ab635-116">Abstract</span></span>

<span data-ttu-id="ab635-117">本文档旨在为规划 Windows PowerShell 所需状态配置请求服务器实现的任何人提供官方指南。</span><span class="sxs-lookup"><span data-stu-id="ab635-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="ab635-118">请求服务器是只应花费几分钟进行部署的简单服务。</span><span class="sxs-lookup"><span data-stu-id="ab635-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="ab635-119">虽然本文档会提供可以在部署中使用的技术操作方法指南，不过本文档的价值是作为最佳做法以及在部署之前要考虑的事项的参考。</span><span class="sxs-lookup"><span data-stu-id="ab635-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="ab635-120">读者应基本熟悉 DSC 以及用于描述在 DSC 部署中包含的组件的术语。</span><span class="sxs-lookup"><span data-stu-id="ab635-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="ab635-121">有关详细信息，请参阅 [Windows PowerShell 所需状态配置概述](https://technet.microsoft.com/library/dn249912.aspx)主题。</span><span class="sxs-lookup"><span data-stu-id="ab635-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="ab635-122">因为 DSC 预计会随着云一起发展，所以包括请求服务器在内的基础技术也预计会进行发展并引入新功能。</span><span class="sxs-lookup"><span data-stu-id="ab635-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="ab635-123">本文档在附录中包含一个版本表，该表提供了对以前版本的参考以及对展望未来的解决方案的参考，以鼓励进行前瞻性设计。</span><span class="sxs-lookup"><span data-stu-id="ab635-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="ab635-124">本文档的两个主要部分：</span><span class="sxs-lookup"><span data-stu-id="ab635-124">The two major sections of this document:</span></span>

 - <span data-ttu-id="ab635-125">配置规划</span><span class="sxs-lookup"><span data-stu-id="ab635-125">Configuration Planning</span></span>
 - <span data-ttu-id="ab635-126">安装指南</span><span class="sxs-lookup"><span data-stu-id="ab635-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="ab635-127">Windows Management Framework 的版本</span><span class="sxs-lookup"><span data-stu-id="ab635-127">Versions of the Windows Management Framework</span></span>
<span data-ttu-id="ab635-128">本文档中的信息旨在应用于 Windows Management Framework 5.0。</span><span class="sxs-lookup"><span data-stu-id="ab635-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="ab635-129">虽然部署和操作请求服务器无需 WMF 5.0，不过版本 5.0 是本文档的重点。</span><span class="sxs-lookup"><span data-stu-id="ab635-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="ab635-130">Windows PowerShell 所需状态配置</span><span class="sxs-lookup"><span data-stu-id="ab635-130">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="ab635-131">所需状态配置 (DSC) 是一个管理平台，借助它可以通过使用名为托管对象格式 (MOF) 的行业语法描述通用信息模型 (CIM)，来部署和管理配置数据。</span><span class="sxs-lookup"><span data-stu-id="ab635-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="ab635-132">开放式管理基础结构 (OMI) 这一开放源代码项目的存在是为了跨平台（包括 Linux 和网络硬件操作系统）进一步开发这些标准。</span><span class="sxs-lookup"><span data-stu-id="ab635-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="ab635-133">有关详细信息，请参阅[链接到 MOF 规范的 DMTF 页面](http://dmtf.org/standards/cim)和 [OMI 文档和源](https://collaboration.opengroup.org/omi/documents.php)。</span><span class="sxs-lookup"><span data-stu-id="ab635-133">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="ab635-134">Windows PowerShell 为所需状态配置提供了一组语言扩展，可以用于创建和管理声明性配置。</span><span class="sxs-lookup"><span data-stu-id="ab635-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="ab635-135">请求服务器角色</span><span class="sxs-lookup"><span data-stu-id="ab635-135">Pull server role</span></span>
<span data-ttu-id="ab635-136">请求服务器提供了一个集中化服务来存储可供目标节点访问的配置。</span><span class="sxs-lookup"><span data-stu-id="ab635-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="ab635-137">请求服务器角色可以作为 Web 服务器实例或 SMB 文件共享进行部署。</span><span class="sxs-lookup"><span data-stu-id="ab635-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="ab635-138">Web 服务器功能包含一个 OData 接口，并且可以选择包含供目标节点在应用配置时报告返回成功或失败确认的功能。</span><span class="sxs-lookup"><span data-stu-id="ab635-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="ab635-139">此功能在存在大量目标节点的环境中非常有用。</span><span class="sxs-lookup"><span data-stu-id="ab635-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="ab635-140">配置目标节点（也称为客户端）以指向请求服务器之后，最新配置数据和任何所需脚本会进行下载并应用。</span><span class="sxs-lookup"><span data-stu-id="ab635-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="ab635-141">这可以作为一次性部署或作为反复出现的作业（这也使得请求服务器成为用于大规模管理更改的重要资产）来进行。</span><span class="sxs-lookup"><span data-stu-id="ab635-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="ab635-142">有关详细信息，请参阅 [Windows PowerShell 所需状态配置请求服务器](https://technet.microsoft.com/library/dn249913.aspx)和[推送和请求配置模式](https://technet.microsoft.com/library/dn249913.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ab635-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="ab635-143">配置规划</span><span class="sxs-lookup"><span data-stu-id="ab635-143">Configuration planning</span></span>

<span data-ttu-id="ab635-144">对于任何企业软件部署，都可以提前收集一些信息以规划正确的体系结构以及为完成部署所需的步骤做好准备。</span><span class="sxs-lookup"><span data-stu-id="ab635-144">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="ab635-145">以下各部分提供有关如何进行准备以及可能需要提前进行的组织连接的信息。</span><span class="sxs-lookup"><span data-stu-id="ab635-145">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="ab635-146">软件要求</span><span class="sxs-lookup"><span data-stu-id="ab635-146">Software requirements</span></span>

<span data-ttu-id="ab635-147">请求服务器的部署需要 Windows Server 的 DSC 服务功能。</span><span class="sxs-lookup"><span data-stu-id="ab635-147">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="ab635-148">此功能是在 Windows Server 2012 中引入的，通过 Windows Management Framework (WMF) 的持续版本进行更新。</span><span class="sxs-lookup"><span data-stu-id="ab635-148">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="ab635-149">软件下载</span><span class="sxs-lookup"><span data-stu-id="ab635-149">Software downloads</span></span>

<span data-ttu-id="ab635-150">除了从 Windows 更新安装最新内容，还有两个被视为用于部署 DSC 请求服务器的最佳做法的下载文件：Windows Management Framework 的最新版本，以及用于自动执行请求服务器设置的 DSC 模块。</span><span class="sxs-lookup"><span data-stu-id="ab635-150">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="ab635-151">WMF</span><span class="sxs-lookup"><span data-stu-id="ab635-151">WMF</span></span>

<span data-ttu-id="ab635-152">Windows Server 2012 R2 包括一种名为 DSC 服务的功能。</span><span class="sxs-lookup"><span data-stu-id="ab635-152">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="ab635-153">DSC 服务功能提供请求服务器功能，包括支持 OData 终结点的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="ab635-153">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="ab635-154">WMF 包含在 Windows Server 中，在各个 Windows Server 版本之间进行敏捷更新。</span><span class="sxs-lookup"><span data-stu-id="ab635-154">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="ab635-155">[新版本的 WMF 5.0](http://aka.ms/wmf5latest) 可能包含对 DSC 服务功能的更新。</span><span class="sxs-lookup"><span data-stu-id="ab635-155">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="ab635-156">因此，最佳做法是下载最新版本的 WMF 并查看发行说明以确定该版本是否包含对 DSC 服务功能的更新。</span><span class="sxs-lookup"><span data-stu-id="ab635-156">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="ab635-157">还应查看指示更新或方案的设计状态是列为稳定还是试验性的发行说明部分。</span><span class="sxs-lookup"><span data-stu-id="ab635-157">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="ab635-158">若要允许实现敏捷发行周期，各个功能可以声明为稳定，这指示功能已准备就绪，可以在生产环境中使用（即使 WMF 是以预览版发行）。</span><span class="sxs-lookup"><span data-stu-id="ab635-158">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="ab635-159">历史上一直通过 WMF 版本进行更新的其他功能（请参阅 WMF 发行说明以了解进一步详细信息）：</span><span class="sxs-lookup"><span data-stu-id="ab635-159">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="ab635-160">Windows PowerShell Windows PowerShell 集成脚本</span><span class="sxs-lookup"><span data-stu-id="ab635-160">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="ab635-161">环境 (ISE) Windows PowerShell Web 服务（Management OData</span><span class="sxs-lookup"><span data-stu-id="ab635-161">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="ab635-162">IIS 扩展）Windows PowerShell 所需状态配置 (DSC)</span><span class="sxs-lookup"><span data-stu-id="ab635-162">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="ab635-163">Windows 远程管理 (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="ab635-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="ab635-164">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="ab635-164">DSC resource</span></span>

<span data-ttu-id="ab635-165">可以通过使用 DSC 配置脚本设置服务来简化请求服务器部署。</span><span class="sxs-lookup"><span data-stu-id="ab635-165">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="ab635-166">本文档包含可以用于部署生产准备就绪服务器节点的配置脚本。</span><span class="sxs-lookup"><span data-stu-id="ab635-166">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="ab635-167">若要使用配置脚本，需要一个未包含在 Windows Server 中的 DSC 模块。</span><span class="sxs-lookup"><span data-stu-id="ab635-167">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="ab635-168">所需模块名称是 **xPSDesiredStateConfiguration**，其中包括 DSC 资源 **xDscWebService**。</span><span class="sxs-lookup"><span data-stu-id="ab635-168">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="ab635-169">可以在[此处](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d)下载 xPSDesiredStateConfiguration 模块。</span><span class="sxs-lookup"><span data-stu-id="ab635-169">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="ab635-170">使用来自 **PowerShellGet** 模块的 **Install-Module** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ab635-170">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="ab635-171">**PowerShellGet** 模块会将该模块下载到：</span><span class="sxs-lookup"><span data-stu-id="ab635-171">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="ab635-172">规划任务</span><span class="sxs-lookup"><span data-stu-id="ab635-172">Planning task</span></span>|
---|
<span data-ttu-id="ab635-173">你是否有权访问 Windows Server 2012 R2 的安装文件？</span><span class="sxs-lookup"><span data-stu-id="ab635-173">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="ab635-174">部署环境是否可以访问 Internet 以便从联机库下载 WMF 和模块？</span><span class="sxs-lookup"><span data-stu-id="ab635-174">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="ab635-175">如何在安装操作系统之后安装最新安全更新？</span><span class="sxs-lookup"><span data-stu-id="ab635-175">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="ab635-176">环境是否可以访问 Internet 以获取更新，或是否具有本地 Windows Server 更新服务 (WSUS) 服务器？</span><span class="sxs-lookup"><span data-stu-id="ab635-176">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="ab635-177">你是否可以访问已通过脱机注入包含更新的 Windows Server 安装文件？</span><span class="sxs-lookup"><span data-stu-id="ab635-177">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="ab635-178">硬件要求</span><span class="sxs-lookup"><span data-stu-id="ab635-178">Hardware requirements</span></span>

<span data-ttu-id="ab635-179">物理和虚拟服务器上都支持请求服务器部署。</span><span class="sxs-lookup"><span data-stu-id="ab635-179">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="ab635-180">请求服务器的大小调整要求与 Windows Server 2012 R2 的要求保持一致。</span><span class="sxs-lookup"><span data-stu-id="ab635-180">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="ab635-181">CPU：1.4 GHz 64 位处理器；内存：512MB；磁盘空间：32GB；网络：千兆位以太网适配器</span><span class="sxs-lookup"><span data-stu-id="ab635-181">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="ab635-182">规划任务</span><span class="sxs-lookup"><span data-stu-id="ab635-182">Planning task</span></span>|
---|
<span data-ttu-id="ab635-183">是部署在物理硬件上还是虚拟化平台上？</span><span class="sxs-lookup"><span data-stu-id="ab635-183">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="ab635-184">为目标环境请求新服务器的过程是什么？</span><span class="sxs-lookup"><span data-stu-id="ab635-184">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="ab635-185">使服务器可用的平均周转时间是多少？</span><span class="sxs-lookup"><span data-stu-id="ab635-185">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="ab635-186">请求多大大小的服务器？</span><span class="sxs-lookup"><span data-stu-id="ab635-186">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="ab635-187">帐户</span><span class="sxs-lookup"><span data-stu-id="ab635-187">Accounts</span></span>

<span data-ttu-id="ab635-188">部署请求服务器实例没有服务帐户要求。</span><span class="sxs-lookup"><span data-stu-id="ab635-188">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="ab635-189">不过在一些情况下，网站可能会在本地用户帐户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="ab635-189">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="ab635-190">例如，如果需要访问用于网站内容的存储共享并且承载存储共享的 Windows Server 或设备未加入域。</span><span class="sxs-lookup"><span data-stu-id="ab635-190">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="ab635-191">DNS 记录</span><span class="sxs-lookup"><span data-stu-id="ab635-191">DNS records</span></span>

<span data-ttu-id="ab635-192">将客户端配置为使用请求服务器环境时，需要使用某个服务器名称。</span><span class="sxs-lookup"><span data-stu-id="ab635-192">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="ab635-193">在测试环境中，通常使用服务器主机名，如果 DNS 名称解析不可用，则可以使用服务器的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="ab635-193">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="ab635-194">在生产环境中或是在旨在表示生产部署的实验室环境中，最佳做法是创建 DNS CNAME 记录。</span><span class="sxs-lookup"><span data-stu-id="ab635-194">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="ab635-195">DNS CNAME 使你可以创建别名以引用主机 (A) 记录。</span><span class="sxs-lookup"><span data-stu-id="ab635-195">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="ab635-196">附加名称记录的用途是在将来需要更改时提高灵活性。</span><span class="sxs-lookup"><span data-stu-id="ab635-196">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="ab635-197">CNAME 可以帮助隔离客户端配置，以便对服务器环境进行的更改（如替换请求服务器或添加其他请求服务器）无需对客户端配置进行对应更改。</span><span class="sxs-lookup"><span data-stu-id="ab635-197">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="ab635-198">为 DNS 记录选择名称时，请记住解决方案体系结构。</span><span class="sxs-lookup"><span data-stu-id="ab635-198">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="ab635-199">如果使用负载平衡，则用于在 HTTPS 上保护流量安全的证书需要共享与 DNS 记录相同的名称。</span><span class="sxs-lookup"><span data-stu-id="ab635-199">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="ab635-200">方案</span><span class="sxs-lookup"><span data-stu-id="ab635-200">Scenario</span></span> |<span data-ttu-id="ab635-201">最佳做法</span><span class="sxs-lookup"><span data-stu-id="ab635-201">Best Practice</span></span>
:---|:---
<span data-ttu-id="ab635-202">测试环境</span><span class="sxs-lookup"><span data-stu-id="ab635-202">Test Environment</span></span> |<span data-ttu-id="ab635-203">在可能时重现计划生产环境。</span><span class="sxs-lookup"><span data-stu-id="ab635-203">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="ab635-204">服务器主机名适用于简单配置。</span><span class="sxs-lookup"><span data-stu-id="ab635-204">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="ab635-205">如果 DNS 不可用，则可以使用 IP 地址替代主机名。</span><span class="sxs-lookup"><span data-stu-id="ab635-205">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="ab635-206">单节点部署</span><span class="sxs-lookup"><span data-stu-id="ab635-206">Single Node Deployment</span></span> |<span data-ttu-id="ab635-207">创建指向服务器主机名的 DNS CNAME 记录。</span><span class="sxs-lookup"><span data-stu-id="ab635-207">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="ab635-208">有关详细信息，请参阅[在 Windows Server 中配置 DNS 轮循机制](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="ab635-208">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="ab635-209">规划任务</span><span class="sxs-lookup"><span data-stu-id="ab635-209">Planning task</span></span>|
---|
<span data-ttu-id="ab635-210">是否知道与谁联系以创建和更改 DNS 记录？</span><span class="sxs-lookup"><span data-stu-id="ab635-210">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="ab635-211">针对 DNS 记录的请求的平均周转时间是多少？</span><span class="sxs-lookup"><span data-stu-id="ab635-211">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="ab635-212">是否需要为服务器请求静态主机名 (A) 记录？</span><span class="sxs-lookup"><span data-stu-id="ab635-212">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="ab635-213">请求什么内容作为 CNAME？</span><span class="sxs-lookup"><span data-stu-id="ab635-213">What will you request as a CNAME?</span></span>|
<span data-ttu-id="ab635-214">如果需要，会使用哪种类型的负载平衡解决方案？</span><span class="sxs-lookup"><span data-stu-id="ab635-214">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="ab635-215">（请参阅标题为“负载平衡”的部分以了解详细信息）</span><span class="sxs-lookup"><span data-stu-id="ab635-215">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="ab635-216">公钥基础结构</span><span class="sxs-lookup"><span data-stu-id="ab635-216">Public Key Infrastructure</span></span>

<span data-ttu-id="ab635-217">当前大多数组织都要求网络流量（特别是包含诸如如何配置服务器这类敏感数据的流量）在传输过程必须进行验证和/或加密。</span><span class="sxs-lookup"><span data-stu-id="ab635-217">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="ab635-218">虽然可以使用 HTTP（采用明文方便进行客户端请求）部署请求服务器，不过最佳做法是使用 HTTPS 保护流量安全。</span><span class="sxs-lookup"><span data-stu-id="ab635-218">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="ab635-219">可以使用 DSC 资源 **xPSDesiredStateConfiguration** 中的一组参数将服务配置为使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="ab635-219">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="ab635-220">保护请求服务器的 HTTPS 流量安全的证书要求与保护任何其他 HTTPS 网站并无不同。</span><span class="sxs-lookup"><span data-stu-id="ab635-220">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="ab635-221">Windows Server 证书服务中的 **Web 服务器**模板满足所需功能。</span><span class="sxs-lookup"><span data-stu-id="ab635-221">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="ab635-222">规划任务</span><span class="sxs-lookup"><span data-stu-id="ab635-222">Planning task</span></span>|
---|
<span data-ttu-id="ab635-223">如果证书请求未自动执行，你需要与谁联系以请求证书？</span><span class="sxs-lookup"><span data-stu-id="ab635-223">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="ab635-224">请求的平均周转时间是多少？</span><span class="sxs-lookup"><span data-stu-id="ab635-224">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="ab635-225">证书文件如何传输给你？</span><span class="sxs-lookup"><span data-stu-id="ab635-225">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="ab635-226">证书私钥如何传输给你？</span><span class="sxs-lookup"><span data-stu-id="ab635-226">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="ab635-227">默认过期时间是多长？</span><span class="sxs-lookup"><span data-stu-id="ab635-227">How long is the default expiration time?</span></span>|
<span data-ttu-id="ab635-228">是否为请求服务器环境确定了可以用于证书名称的 DNS 名称？</span><span class="sxs-lookup"><span data-stu-id="ab635-228">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="ab635-229">选择体系结构</span><span class="sxs-lookup"><span data-stu-id="ab635-229">Choosing an architecture</span></span>

<span data-ttu-id="ab635-230">可以使用 IIS 上承载的 Web 服务或 SMB 文件共享部署请求服务器。</span><span class="sxs-lookup"><span data-stu-id="ab635-230">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="ab635-231">在大多数情况下，Web 服务选项会提供更高灵活性。</span><span class="sxs-lookup"><span data-stu-id="ab635-231">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="ab635-232">HTTPS 流量经常会穿越网络边界，而在各个网络之间通常会筛选或阻止 SMB 流量。</span><span class="sxs-lookup"><span data-stu-id="ab635-232">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="ab635-233">Web 服务还提供选项以包含一致性服务器或 Web 报表管理器（在本文档的将来版本将讨论这两个主题），从而为客户端提供一种机制，用于将状态报告返回给服务器以便集中查看。</span><span class="sxs-lookup"><span data-stu-id="ab635-233">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="ab635-234">SMB 针对策略规定不应利用 Web 服务器的环境，以及使得不需要 Web 服务器角色的其他环境要求提供了一个选项。</span><span class="sxs-lookup"><span data-stu-id="ab635-234">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="ab635-235">在任一情况下，请记住评估签名和加密流量的要求。</span><span class="sxs-lookup"><span data-stu-id="ab635-235">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="ab635-236">HTTPS、SMB 签名和 IPSEC 策略都是值得考虑的选项。</span><span class="sxs-lookup"><span data-stu-id="ab635-236">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="ab635-237">负载平衡</span><span class="sxs-lookup"><span data-stu-id="ab635-237">Load balancing</span></span>
<span data-ttu-id="ab635-238">与 Web 服务进行交互的客户端会针对在单个响应中返回的信息发出请求。</span><span class="sxs-lookup"><span data-stu-id="ab635-238">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="ab635-239">无需连续请求，因此负载平衡平台无需确保在任何时间点都在单台服务器上维持会话。</span><span class="sxs-lookup"><span data-stu-id="ab635-239">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="ab635-240">规划任务</span><span class="sxs-lookup"><span data-stu-id="ab635-240">Planning task</span></span>|
---|
<span data-ttu-id="ab635-241">使用哪种解决方案在服务器间对流量进行负载平衡？</span><span class="sxs-lookup"><span data-stu-id="ab635-241">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="ab635-242">如果使用硬件负载平衡器，则谁会进行请求以将新配置添加到设备？</span><span class="sxs-lookup"><span data-stu-id="ab635-242">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="ab635-243">配置新负载平衡 Web 服务的请求的平均周转时间是多少？</span><span class="sxs-lookup"><span data-stu-id="ab635-243">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="ab635-244">该请求需要哪些信息？</span><span class="sxs-lookup"><span data-stu-id="ab635-244">What information will be required for the request?</span></span>|
<span data-ttu-id="ab635-245">你是否需要请求附加 IP，或负责进行负载平衡的团队是否会处理该请求？</span><span class="sxs-lookup"><span data-stu-id="ab635-245">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="ab635-246">你是否具有所需 DNS 记录，以及负责配置负载平衡解决方案的团队是否需要这样？</span><span class="sxs-lookup"><span data-stu-id="ab635-246">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="ab635-247">负载平衡解决方案是否要求 PKI 由设备进行处理，或是否可以对 HTTPS 流量进行负载平衡（只要没有会话要求）？</span><span class="sxs-lookup"><span data-stu-id="ab635-247">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="ab635-248">请求服务器上的暂存配置和模块</span><span class="sxs-lookup"><span data-stu-id="ab635-248">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="ab635-249">作为配置规划的一部分，你需要考虑请求服务器会承载的 DSC 托管模块和配置。</span><span class="sxs-lookup"><span data-stu-id="ab635-249">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="ab635-250">为进行配置规划，需要基本了解如何准备内容并将它部署到请求服务器，这十分重要。</span><span class="sxs-lookup"><span data-stu-id="ab635-250">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="ab635-251">将来，此部分会进行扩展并包含在 DSC 请求服务器的操作指南中。</span><span class="sxs-lookup"><span data-stu-id="ab635-251">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="ab635-252">该指南会讨论使用自动化随时间推移管理模块和配置的日常过程。</span><span class="sxs-lookup"><span data-stu-id="ab635-252">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="ab635-253">DSC 模块</span><span class="sxs-lookup"><span data-stu-id="ab635-253">DSC modules</span></span>
<span data-ttu-id="ab635-254">请求配置的客户端需要所需 DSC 模块。</span><span class="sxs-lookup"><span data-stu-id="ab635-254">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="ab635-255">请求服务器的功能是按需自动将 DSC 模块分发到客户端。</span><span class="sxs-lookup"><span data-stu-id="ab635-255">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="ab635-256">如果你是首次部署请求服务器（可能作为实验室或概念证明），则可能要依赖于可从公共存储库（如 PowerShell 库或用于 DSC 模块的 PowerShell.org GitHub 存储库）获取的 DSC 模块。</span><span class="sxs-lookup"><span data-stu-id="ab635-256">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="ab635-257">请务必记住，即使是对于受信任的联机源（如 PowerShell 库），从公共存储库下载的任何模块在用于生产之前，都应由具有 PowerShell 经验并了解使用模块的环境的人员进行检查。</span><span class="sxs-lookup"><span data-stu-id="ab635-257">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="ab635-258">完成此任务期间，这是检查模块中是否存在可以删除的任何其他负载（如文档和示例脚本）的好时机。</span><span class="sxs-lookup"><span data-stu-id="ab635-258">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="ab635-259">这会在通过网络将模块从服务器下载到客户端时，减少每个客户端在其第一个请求中的网络带宽。</span><span class="sxs-lookup"><span data-stu-id="ab635-259">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="ab635-260">每个模块都必须打包为特定格式（名为 ModuleName_Version.zip 的 ZIP 文件，其中包含模块负载）。</span><span class="sxs-lookup"><span data-stu-id="ab635-260">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="ab635-261">该文件复制到服务器之后，必须创建校验和文件。</span><span class="sxs-lookup"><span data-stu-id="ab635-261">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="ab635-262">客户端连接到服务器时，校验和用于验证 DSC 模块的内容自发布以来未发生更改。</span><span class="sxs-lookup"><span data-stu-id="ab635-262">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="ab635-263">规划任务</span><span class="sxs-lookup"><span data-stu-id="ab635-263">Planning task</span></span>|
---|
<span data-ttu-id="ab635-264">如果你在规划测试或实验室环境，则哪些方案是进行验证的关键？</span><span class="sxs-lookup"><span data-stu-id="ab635-264">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="ab635-265">是否存在包含的资源涵盖你所需的所有内容的公开发布模块，或你是否需要创作自己的资源？</span><span class="sxs-lookup"><span data-stu-id="ab635-265">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="ab635-266">你的环境是否可以访问 Internet 以检索公共模块？</span><span class="sxs-lookup"><span data-stu-id="ab635-266">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="ab635-267">谁负责检查 DSC 模块？</span><span class="sxs-lookup"><span data-stu-id="ab635-267">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="ab635-268">如果你在规划生产环境，则你会使用什么作为本地存储库来用于存储 DSC 模块？</span><span class="sxs-lookup"><span data-stu-id="ab635-268">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="ab635-269">中心团队是否接受来自应用程序团队的 DSC 模块？</span><span class="sxs-lookup"><span data-stu-id="ab635-269">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="ab635-270">过程是怎样的？</span><span class="sxs-lookup"><span data-stu-id="ab635-270">What will the process be?</span></span>|
<span data-ttu-id="ab635-271">是否自动从源存储库打包生产准备就绪 DSC 模块、复制到服务器并为它们创建校验和？</span><span class="sxs-lookup"><span data-stu-id="ab635-271">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="ab635-272">你的团队是否也负责管理自动化平台？</span><span class="sxs-lookup"><span data-stu-id="ab635-272">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="ab635-273">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="ab635-273">DSC configurations</span></span>

<span data-ttu-id="ab635-274">请求服务器的用途是提供一种集中式机制，用于将 DSC 配置分发到客户端节点。</span><span class="sxs-lookup"><span data-stu-id="ab635-274">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="ab635-275">配置作为 MOF 文档存储在服务器上。</span><span class="sxs-lookup"><span data-stu-id="ab635-275">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="ab635-276">每个文档都使用唯一的 GUID 进行命名。</span><span class="sxs-lookup"><span data-stu-id="ab635-276">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="ab635-277">客户端配置为与请求服务器连接时，还会向它们提供它们应请求的配置的 GUID。</span><span class="sxs-lookup"><span data-stu-id="ab635-277">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="ab635-278">这一通过 GUID 引用配置的系统可保证全局唯一性，并且十分灵活，以便配置可按照每个节点的粒度进行应用，或作为跨应具有相同配置的多台服务器的角色配置。</span><span class="sxs-lookup"><span data-stu-id="ab635-278">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="ab635-279">GUID</span><span class="sxs-lookup"><span data-stu-id="ab635-279">GUIDs</span></span>

<span data-ttu-id="ab635-280">全面考虑请求服务器部署时，规划配置 GUID 值得多加注意。</span><span class="sxs-lookup"><span data-stu-id="ab635-280">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="ab635-281">对于如何处理 GUID 没有特定要求，该过程可能对于每个环境是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ab635-281">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="ab635-282">该过程的范围可以从简单到复杂：集中存储的 CSV 文件、简单 SQL 表、CMDB 或需要与其他工具或软件解决方案集成的复杂解决方案。</span><span class="sxs-lookup"><span data-stu-id="ab635-282">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="ab635-283">有两种常规方法：</span><span class="sxs-lookup"><span data-stu-id="ab635-283">There are two general approaches:</span></span>

 - <span data-ttu-id="ab635-284">**对每台服务器分配 GUID** — 提供一种措施来保证分别控制每台服务器配置。</span><span class="sxs-lookup"><span data-stu-id="ab635-284">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="ab635-285">这提供了更新方面的精度级别，十分适合于包含少量服务器的环境。</span><span class="sxs-lookup"><span data-stu-id="ab635-285">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="ab635-286">**对每个服务器角色分配 GUID** — 执行相同功能的所有服务器（如 Web 服务器）都使用相同 GUID 引用所需配置数据。</span><span class="sxs-lookup"><span data-stu-id="ab635-286">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="ab635-287">请注意，如果有许多服务器共享相同 GUID，则它们都会在配置更改时同时更新。</span><span class="sxs-lookup"><span data-stu-id="ab635-287">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="ab635-288">GUID 是应视为敏感数据的信息，因为它可以由具有恶意企图的人员用于获取有关如何在环境中部署和配置服务器的情报。</span><span class="sxs-lookup"><span data-stu-id="ab635-288">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="ab635-289">有关详细信息，请参阅[在 PowerShell 所需状态配置请求模式中安全地分配 GUID](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ab635-289">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="ab635-290">规划任务</span><span class="sxs-lookup"><span data-stu-id="ab635-290">Planning task</span></span>|
---|
<span data-ttu-id="ab635-291">谁负责在配置准备就绪时将它们复制到请求服务器文件夹中？</span><span class="sxs-lookup"><span data-stu-id="ab635-291">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="ab635-292">如果配置由应用程序团队创作，则移交它们的过程是怎样的？</span><span class="sxs-lookup"><span data-stu-id="ab635-292">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="ab635-293">你是否会在创作配置时，利用存储库在团队间存储配置？</span><span class="sxs-lookup"><span data-stu-id="ab635-293">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="ab635-294">是否会在配置准备就绪时自动执行将它们复制到服务器并创建校验和的过程？</span><span class="sxs-lookup"><span data-stu-id="ab635-294">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="ab635-295">如何将 GUID 映射到服务器或角色，以及这会存储在何处？</span><span class="sxs-lookup"><span data-stu-id="ab635-295">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="ab635-296">你会使用什么过程来配置客户端计算机，以及如何将它与用于创建和存储配置 GUID 的过程集成？</span><span class="sxs-lookup"><span data-stu-id="ab635-296">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="ab635-297">安装指南</span><span class="sxs-lookup"><span data-stu-id="ab635-297">Installation Guide</span></span>

<span data-ttu-id="ab635-298">*本文档中提供的脚本是稳定示例。在生产环境中执行脚本之前，请始终仔细检查它们。*</span><span class="sxs-lookup"><span data-stu-id="ab635-298">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ab635-299">必备条件</span><span class="sxs-lookup"><span data-stu-id="ab635-299">Prerequisites</span></span>

<span data-ttu-id="ab635-300">若要验证服务器上的 PowerShell 版本，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="ab635-300">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="ab635-301">如果可能，请升级到 Windows Management Framework 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="ab635-301">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="ab635-302">接下来，使用以下命令下载 `xPsDesiredStateConfiguration` 模块。</span><span class="sxs-lookup"><span data-stu-id="ab635-302">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="ab635-303">该命令会在下载模块之前请求你进行审批。</span><span class="sxs-lookup"><span data-stu-id="ab635-303">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="ab635-304">安装和配置脚本</span><span class="sxs-lookup"><span data-stu-id="ab635-304">Installation and configuration scripts</span></span>
-

<span data-ttu-id="ab635-305">用于部署 DSC 请求服务器的最佳方法是使用 DSC 配置脚本。</span><span class="sxs-lookup"><span data-stu-id="ab635-305">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="ab635-306">本文档提供的脚本包括仅配置 DSC Web 服务的基本配置和配置 Windows Server 端到端（包括 DSC Web 服务）的高级设置。</span><span class="sxs-lookup"><span data-stu-id="ab635-306">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="ab635-307">注意：当前 `xPSDesiredStateConfiguation` DSC 模块要求服务器是 EN-US 区域设置。</span><span class="sxs-lookup"><span data-stu-id="ab635-307">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="ab635-308">适用于 Windows Server 2012 的基本配置</span><span class="sxs-lookup"><span data-stu-id="ab635-308">Basic configuration for Windows Server 2012</span></span>
-------------------------------------------
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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="ab635-309">适用于 Windows Server 2012 R2 的高级配置</span><span class="sxs-lookup"><span data-stu-id="ab635-309">Advanced configuration for Windows Server 2012 R2</span></span>

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


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="ab635-310">验证请求服务器功能</span><span class="sxs-lookup"><span data-stu-id="ab635-310">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN'

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="ab635-311">配置客户端</span><span class="sxs-lookup"><span data-stu-id="ab635-311">Configure clients</span></span>

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


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="ab635-312">其他参考、代码段和示例</span><span class="sxs-lookup"><span data-stu-id="ab635-312">Additional references, snippets, and examples</span></span>

<span data-ttu-id="ab635-313">此示例演示如何手动启动客户端连接（需要 WMF5）以进行测试。</span><span class="sxs-lookup"><span data-stu-id="ab635-313">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="ab635-314">[Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet 用于将一种类型的 CNAME 记录添加到 DNS 区域。</span><span class="sxs-lookup"><span data-stu-id="ab635-314">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="ab635-315">用于[创建校验和以及将 DSC MOF 发布到 SMB 请求服务器](http://bit.ly/1E46BhI)的 PowerShell 函数会自动生成所需校验和，然后将 MOF 配置文件和校验和文件都复制到 SMB 请求服务器。</span><span class="sxs-lookup"><span data-stu-id="ab635-315">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="ab635-316">附录 - 了解 ODATA 服务数据文件类型</span><span class="sxs-lookup"><span data-stu-id="ab635-316">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="ab635-317">在包含 OData Web 服务的请求服务器部署过程中，会存储数据文件以创建信息。</span><span class="sxs-lookup"><span data-stu-id="ab635-317">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="ab635-318">文件的类型取决于操作系统，如下所述。</span><span class="sxs-lookup"><span data-stu-id="ab635-318">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="ab635-319">**Windows Server 2012**：文件类型始终为 .mdb</span><span class="sxs-lookup"><span data-stu-id="ab635-319">**Windows Server 2012** The file type will always be   .mdb</span></span>
 - <span data-ttu-id="ab635-320">**Windows Server 2012 R2**：文件类型默认为 .edb，除非在配置中指定了 .mdb</span><span class="sxs-lookup"><span data-stu-id="ab635-320">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="ab635-321">在用于安装请求服务器的[高级示例脚本](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts)中，还会找到有关如何自动控制 web.config 文件设置以防止文件类型所导致的任何可能错误的示例。</span><span class="sxs-lookup"><span data-stu-id="ab635-321">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>