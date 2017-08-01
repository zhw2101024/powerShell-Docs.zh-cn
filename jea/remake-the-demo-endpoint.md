---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "重新创建演示终结点"
ms.technology: powershell
ms.openlocfilehash: 4a56272b6f995500d443d441f5e03db85dac6f96
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="remake-the-demo-endpoint"></a><span data-ttu-id="948e4-103">重新创建演示终结点</span><span class="sxs-lookup"><span data-stu-id="948e4-103">Remake the Demo Endpoint</span></span>
<span data-ttu-id="948e4-104">在本部分中，你将了解如何生成上一部分中所使用的演示终结点的精确副本。</span><span class="sxs-lookup"><span data-stu-id="948e4-104">In this section, you will learn how to generate an exact replica of the demo endpoint you used in the above section.</span></span>
<span data-ttu-id="948e4-105">这将引入了解 JEA 所必须了解的核心概念，包括 PowerShell 会话配置和角色功能。</span><span class="sxs-lookup"><span data-stu-id="948e4-105">This will introduce core concepts that are necessary to understand JEA, including PowerShell Session Configurations and Role Capabilities.</span></span>

## <a name="powershell-session-configurations"></a><span data-ttu-id="948e4-106">PowerShell 会话配置</span><span class="sxs-lookup"><span data-stu-id="948e4-106">PowerShell Session Configurations</span></span>
<span data-ttu-id="948e4-107">在上一部分中使用 JEA 时，你是通过运行以下命令开始的：</span><span class="sxs-lookup"><span data-stu-id="948e4-107">When you used JEA in the above section, you started by running the following command:</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

<span data-ttu-id="948e4-108">虽然大多数参数都一目了然，但 *ConfigurationName* 参数最初可能显得令人困惑。</span><span class="sxs-lookup"><span data-stu-id="948e4-108">While most of the parameters are self-explanatory, the *ConfigurationName* parameter may seem confusing at first.</span></span>
<span data-ttu-id="948e4-109">该参数指定了你连接到的 PowerShell 会话配置。</span><span class="sxs-lookup"><span data-stu-id="948e4-109">That parameter specified the PowerShell Session Configuration to which you were connecting.</span></span>

<span data-ttu-id="948e4-110">*PowerShell 会话配置*是 PowerShell 终结点的特别术语。</span><span class="sxs-lookup"><span data-stu-id="948e4-110">*PowerShell Session Configuration* is a fancy term for a PowerShell endpoint.</span></span>
<span data-ttu-id="948e4-111">它是一个象征性的“位置”，用户可连接到它并获取 PowerShell 功能的访问权限。</span><span class="sxs-lookup"><span data-stu-id="948e4-111">It is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="948e4-112">基于会话配置的设置，它可为连接的用户提供不同功能。</span><span class="sxs-lookup"><span data-stu-id="948e4-112">Based on how you set up a Session Configuration, it can provide different functionality to connecting users.</span></span>
<span data-ttu-id="948e4-113">对于 JEA，我们使用会话配置将 PowerShell 限制于一组受限的功能，并以具有特权的虚拟帐户身份运行。</span><span class="sxs-lookup"><span data-stu-id="948e4-113">For JEA, we use Session Configurations to restrict PowerShell to a limited set of functionality and to run as a privileged virtual account.</span></span>

<span data-ttu-id="948e4-114">你的计算机上已具有多个已注册的 PowerShell 会话配置，其设置各有轻微差异。</span><span class="sxs-lookup"><span data-stu-id="948e4-114">You already have several registered PowerShell Session Configurations on your machine, each set up slightly differently.</span></span>
<span data-ttu-id="948e4-115">其中的大多数是 Windows 自带的，但“JEA_Demo”会话配置是在 [必备条件](prerequisites.md) 部分中设置的。</span><span class="sxs-lookup"><span data-stu-id="948e4-115">Most of them come with Windows, but the "JEA_Demo" Session Configuration was set up in the [prerequisites](prerequisites.md) section.</span></span>
<span data-ttu-id="948e4-116">可在管理员 PowerShell 提示符中运行以下命令以查看所有已注册的会话配置：</span><span class="sxs-lookup"><span data-stu-id="948e4-116">You can see all registered Session Configurations by running the following command in an Administrator PowerShell prompt:</span></span>

```PowerShell
Get-PSSessionConfiguration
```

## <a name="powershell-session-configuration-files"></a><span data-ttu-id="948e4-117">PowerShell 会话配置文件</span><span class="sxs-lookup"><span data-stu-id="948e4-117">PowerShell Session Configuration Files</span></span>
<span data-ttu-id="948e4-118">可通过注册新的 *PowerShell 会话配置文件*来创建新的会话配置。</span><span class="sxs-lookup"><span data-stu-id="948e4-118">You can make new Session Configurations by registering new *PowerShell Session Configuration Files*.</span></span>
<span data-ttu-id="948e4-119">会话配置文件的文件扩展名为“.pssc”。</span><span class="sxs-lookup"><span data-stu-id="948e4-119">Session Configuration Files have ".pssc" file extensions.</span></span>
<span data-ttu-id="948e4-120">你可以使用 New-PSSessionConfigurationFile cmdlet 生成会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="948e4-120">You can generate Session Configuration Files with the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="948e4-121">接下来，你要为 JEA 创建并注册新的会话配置。</span><span class="sxs-lookup"><span data-stu-id="948e4-121">Next, you are going to create and register a new Session Configuration for JEA.</span></span>

## <a name="generate-and-modify-your-powershell-session-configuration"></a><span data-ttu-id="948e4-122">生成并修改 PowerShell 会话配置</span><span class="sxs-lookup"><span data-stu-id="948e4-122">Generate and Modify your PowerShell Session Configuration</span></span>
<span data-ttu-id="948e4-123">运行以下命令以生成 PowerShell 会话配置“主干”文件。</span><span class="sxs-lookup"><span data-stu-id="948e4-123">Run the following command to generate a PowerShell Session Configuration "skeleton" file.</span></span>

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> <span data-ttu-id="948e4-124">**提示：**默认情况下，主干文件仅包含最常用的配置设置。</span><span class="sxs-lookup"><span data-stu-id="948e4-124">**TIP:** Only the most common configuration settings are included in the skeleton file by default.</span></span>
> <span data-ttu-id="948e4-125">使用 `-Full` 参数以在生成的 PSSC 中包含所有适用设置。</span><span class="sxs-lookup"><span data-stu-id="948e4-125">Use the `-Full` parameter to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="948e4-126">在 PowerShell ISE 或你喜爱的文本编辑器中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="948e4-126">Open the file in PowerShell ISE, or your favorite text editor.</span></span>

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="948e4-127">使用以下值更新文件中的以下字段（请记得在自己的非管理员安全组中进行替换）：</span><span class="sxs-lookup"><span data-stu-id="948e4-127">Update the following fields in the file with the values below (remember to substitute in your own non-administrator security group):</span></span>

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

<span data-ttu-id="948e4-128">以下是各条目的含义：</span><span class="sxs-lookup"><span data-stu-id="948e4-128">Here is what each of those entries mean:</span></span>

1.  <span data-ttu-id="948e4-129">*SessionType* 字段定义要用于此终结点的预设默认设置。</span><span class="sxs-lookup"><span data-stu-id="948e4-129">The *SessionType* field defines preset default settings to use with this endpoint.</span></span>
<span data-ttu-id="948e4-130">*RestrictedRemoteServer* 定义远程管理所需的最低设置。</span><span class="sxs-lookup"><span data-stu-id="948e4-130">*RestrictedRemoteServer* defines the minimal settings necessary for remote management.</span></span>
<span data-ttu-id="948e4-131">默认情况下，*RestrictedRemoteServer* 终结点将公开 Get-Command、Get-FormatData、Select-Object、Get-Help、Measure-Object、Exit-PSSession、Clear-Host 和 Out-Default。</span><span class="sxs-lookup"><span data-stu-id="948e4-131">By default, a *RestrictedRemoteServer* endpoint will expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default.</span></span>
<span data-ttu-id="948e4-132">它会将 *ExecutionPolicy* 设置为 *RemoteSigned*，并将 *LanguageMode* 设置为 *NoLanguage*。</span><span class="sxs-lookup"><span data-stu-id="948e4-132">It will set the *ExecutionPolicy* to *RemoteSigned*, and the *LanguageMode* to *NoLanguage*.</span></span>
<span data-ttu-id="948e4-133">这些设置的净效果是用于配置终结点的安全的最低起点。</span><span class="sxs-lookup"><span data-stu-id="948e4-133">The net effect of these settings is a secure and minimal starting point for configuring your endpoint.</span></span>

2.  <span data-ttu-id="948e4-134">*RoleDefinitions* 字段将角色功能分配给特定组。</span><span class="sxs-lookup"><span data-stu-id="948e4-134">The *RoleDefinitions* field assigns Role Capabilities to specific groups.</span></span>
<span data-ttu-id="948e4-135">它定义特定用户可以特权帐户身份执行的操作。</span><span class="sxs-lookup"><span data-stu-id="948e4-135">It defines who can do what as a privileged account.</span></span>
<span data-ttu-id="948e4-136">使用此字段，你可以指定基于组成员身份的任何连接用户可用的功能。</span><span class="sxs-lookup"><span data-stu-id="948e4-136">With this field, you can specify the functionality available to any connecting user based on group membership.</span></span>
<span data-ttu-id="948e4-137">这是 JEA 的 RBAC 功能的核心。</span><span class="sxs-lookup"><span data-stu-id="948e4-137">This is the core of JEA's RBAC functionality.</span></span>
<span data-ttu-id="948e4-138">在此示例中，你将向“Contoso\JEA_NonAdmin_Operator”组的成员公开预制的“维护”角色功能。</span><span class="sxs-lookup"><span data-stu-id="948e4-138">In this example, you are exposing the pre-made "Maintenance" RoleCapability to members of the "Contoso\JEA_NonAdmin_Operator" group.</span></span>

3.  <span data-ttu-id="948e4-139">*RunAsVirtualAccount* 字段指示 PowerShell 在此终结点处的“运行方式”应为虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="948e4-139">The *RunAsVirtualAccount* field indicates that PowerShell should "run as" a Virtual Account at this endpoint.</span></span>
<span data-ttu-id="948e4-140">默认情况下，虚拟帐户是内置“管理员”组的成员。</span><span class="sxs-lookup"><span data-stu-id="948e4-140">By default, the Virtual Account is a member of the built in Administrators group.</span></span>
<span data-ttu-id="948e4-141">在域控制器上，默认情况下，它也是“域管理员”组的成员。</span><span class="sxs-lookup"><span data-stu-id="948e4-141">On a domain controller, it is also a member of the Domain Administrators group by default.</span></span>
<span data-ttu-id="948e4-142">在本指南稍后部分，你将了解如何自定义虚拟帐户的特权。</span><span class="sxs-lookup"><span data-stu-id="948e4-142">Later in this guide, you will learn how to customize the privileges of the Virtual Account.</span></span>

4.  <span data-ttu-id="948e4-143">*TranscriptDirectory* 字段定义每个远程会话结束后将“即时权限提升”PowerShell 脚本保存到的位置。</span><span class="sxs-lookup"><span data-stu-id="948e4-143">The *TranscriptDirectory* field defines where "over-the-shoulder" PowerShell transcripts are saved after each remote session.</span></span>
<span data-ttu-id="948e4-144">这些脚本使你能够以可读的方式检查每个会话中所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="948e4-144">These transcripts allow you to inspect the actions taken in each session in a readable way.</span></span>
<span data-ttu-id="948e4-145">有关 PowerShell 脚本的详细信息，请参阅这篇[博客文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。</span><span class="sxs-lookup"><span data-stu-id="948e4-145">For more information about PowerShell transcripts, check out this [blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>
<span data-ttu-id="948e4-146">注意：常规 Windows 事件也将捕获有关每个用户使用 PowerShell 所运行项目的信息。</span><span class="sxs-lookup"><span data-stu-id="948e4-146">Note: regular Windows Eventing also captures information about what each user ran with PowerShell.</span></span>
<span data-ttu-id="948e4-147">但脚本可读性稍高。</span><span class="sxs-lookup"><span data-stu-id="948e4-147">Transcripts are just a bit more readable.</span></span>

<span data-ttu-id="948e4-148">最后，将你的更改保存到 *JEADemo2.pssc*。</span><span class="sxs-lookup"><span data-stu-id="948e4-148">Finally, save your changes to *JEADemo2.pssc*.</span></span>

## <a name="apply-the-powershell-session-configuration"></a><span data-ttu-id="948e4-149">应用 PowerShell 会话配置</span><span class="sxs-lookup"><span data-stu-id="948e4-149">Apply the PowerShell Session Configuration</span></span>

<span data-ttu-id="948e4-150">若要从会话配置文件创建终结点，需注册该文件。</span><span class="sxs-lookup"><span data-stu-id="948e4-150">To create an endpoint from a Session Configuration file, you need to register the file.</span></span>
<span data-ttu-id="948e4-151">这需要几条信息：</span><span class="sxs-lookup"><span data-stu-id="948e4-151">This requires a few pieces of information:</span></span>

1. <span data-ttu-id="948e4-152">会话配置文件的路径。</span><span class="sxs-lookup"><span data-stu-id="948e4-152">The path to the Session Configuration file.</span></span>
2. <span data-ttu-id="948e4-153">你已注册的会话配置的名称。</span><span class="sxs-lookup"><span data-stu-id="948e4-153">The name of your registered Session Configuration.</span></span> <span data-ttu-id="948e4-154">此名称与用户使用 `Enter-PSSession` 或 `New-PSSession` 连接到你的终结点时向“ConfigurationName”参数提供的名称相同。</span><span class="sxs-lookup"><span data-stu-id="948e4-154">This is the same name users provide to the "ConfigurationName" parameter when they connect to your endpoint with `Enter-PSSession` or `New-PSSession`.</span></span>

<span data-ttu-id="948e4-155">若要在本地计算机上注册会话配置，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="948e4-155">To register the Session Configuration on your local machine, run the following command:</span></span>

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="948e4-156">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="948e4-156">Congratulations!</span></span> <span data-ttu-id="948e4-157">你已设置 JEA 终结点。</span><span class="sxs-lookup"><span data-stu-id="948e4-157">You have set up your JEA endpoint.</span></span>

## <a name="test-out-your-endpoint"></a><span data-ttu-id="948e4-158">测试终结点</span><span class="sxs-lookup"><span data-stu-id="948e4-158">Test Out Your Endpoint</span></span>
<span data-ttu-id="948e4-159">针对你的新终结点重新运行 [使用 JEA](using-jea.md) 部分中所列出的步骤，确认它按照预期方式运行。</span><span class="sxs-lookup"><span data-stu-id="948e4-159">Re-run the steps listed in the [Using JEA](using-jea.md) section against your new endpoint to confirm it is operating as intended.</span></span>
<span data-ttu-id="948e4-160">为 `Enter-PSSession` 提供配置名称时，请确保使用新的终结点名称 (JEADemo2)。</span><span class="sxs-lookup"><span data-stu-id="948e4-160">Be sure to use the new endpoint name (JEADemo2) when providing the configuration name to `Enter-PSSession`.</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## <a name="key-concepts"></a><span data-ttu-id="948e4-161">关键概念</span><span class="sxs-lookup"><span data-stu-id="948e4-161">Key Concepts</span></span>
<span data-ttu-id="948e4-162">**PowerShell 会话配置**：有时称为 *PowerShell 终结点*，这是一个象征性的“位置”，用户可连接到它并获取 PowerShell 功能的访问权限。</span><span class="sxs-lookup"><span data-stu-id="948e4-162">**PowerShell Session Configuration**: Sometimes referred to as *PowerShell Endpoint*, this is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="948e4-163">你可以通过运行 `Get-PSSessionConfiguration` 列出系统上已注册的会话配置。</span><span class="sxs-lookup"><span data-stu-id="948e4-163">You can list the registered Session Configurations on your system by running `Get-PSSessionConfiguration`.</span></span>
<span data-ttu-id="948e4-164">以特定方式配置后，可将 PowerShell 会话配置称为 *JEA 终结点*。</span><span class="sxs-lookup"><span data-stu-id="948e4-164">When configured in a specific way, a PowerShell Session Configuration can be called a *JEA Endpoint*.</span></span>

<span data-ttu-id="948e4-165">**PowerShell 会话配置文件 (.pssc)**：注册后，此文件定义 PowerShell 会话配置的设置。</span><span class="sxs-lookup"><span data-stu-id="948e4-165">**PowerShell Session Configuration File (.pssc)**: A file that, when registered, defines settings for a PowerShell Session Configuration.</span></span>
<span data-ttu-id="948e4-166">它包含可连接到终结点的用户角色的规范、“运行方式”虚拟帐户等。</span><span class="sxs-lookup"><span data-stu-id="948e4-166">It contains specifications for user roles that can connect to the endpoint, the "run as" Virtual Account, and more.</span></span>     

<span data-ttu-id="948e4-167">**角色定义**：会话配置文件中定义授予连接用户的角色功能的字段。</span><span class="sxs-lookup"><span data-stu-id="948e4-167">**Role Definitions**: The field in a Session Configuration File that defines the Role Capabilities granted to connecting users.</span></span>
<span data-ttu-id="948e4-168">它定义特定*用户*可以特权帐户身份执行的*操作*。</span><span class="sxs-lookup"><span data-stu-id="948e4-168">It defines *who* can do *what* as a privileged account.</span></span>
<span data-ttu-id="948e4-169">这是 JEA 的 RBAC 功能的核心。</span><span class="sxs-lookup"><span data-stu-id="948e4-169">This is the core of JEA's RBAC capabilities.</span></span>

<span data-ttu-id="948e4-170">**SessionType**：会话配置文件中表示会话配置的默认设置的字段。</span><span class="sxs-lookup"><span data-stu-id="948e4-170">**SessionType**: A field in a Session Configuration File that represents default settings for a Session Configuration.</span></span>
<span data-ttu-id="948e4-171">对于 JEA 终结点，必须将此字段设置为 RestrictedRemoteServer。</span><span class="sxs-lookup"><span data-stu-id="948e4-171">For JEA endpoints, this must be set to RestrictedRemoteServer.</span></span>

<span data-ttu-id="948e4-172">**PowerShell 脚本**：包含 PowerShell 会话的“即时权限提升”视图的文件。</span><span class="sxs-lookup"><span data-stu-id="948e4-172">**PowerShell Transcript**: A file containing an "over-the-shoulder" view of a PowerShell session.</span></span>
<span data-ttu-id="948e4-173">你可以将 PowerShell 设置为使用 TranscriptDirectory 字段生成 JEA 会话的脚本。</span><span class="sxs-lookup"><span data-stu-id="948e4-173">You can set PowerShell to generate transcripts for JEA sessions using the TranscriptDirectory field.</span></span>
<span data-ttu-id="948e4-174">有关脚本的详细信息，请参阅这篇[博客文章](https://technet.microsoft.com/en-us/magazine/ff687007.aspx)。</span><span class="sxs-lookup"><span data-stu-id="948e4-174">For more information on transcripts, check out this [blog post](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span></span>

