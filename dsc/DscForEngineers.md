---
ms.date: 10/13/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于决策者的 Desired State Configuration 概述
ms.openlocfilehash: f8a851c5fbc5165ebe9642c5cd60964f1584efab
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189884"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="a3c6e-103">适用于工程师的 Desired State Configuration 概述</span><span class="sxs-lookup"><span data-stu-id="a3c6e-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="a3c6e-104">本文档旨在使开发人员和运营团队了解 PowerShell Desired State Configuration (DSC) 的优势。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="a3c6e-105">有关 DSC 提供的值的更高级别视图，请参阅[适用于决策者的 Desired State Configuration 概述](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="a3c6e-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="a3c6e-106">Desired State Configuration 的优势</span><span class="sxs-lookup"><span data-stu-id="a3c6e-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="a3c6e-107">DSC 具有以下优势：</span><span class="sxs-lookup"><span data-stu-id="a3c6e-107">DSC exists to:</span></span>

- <span data-ttu-id="a3c6e-108">降低在 Windows 中编写脚本的复杂程度</span><span class="sxs-lookup"><span data-stu-id="a3c6e-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="a3c6e-109">提高迭代速度</span><span class="sxs-lookup"><span data-stu-id="a3c6e-109">Increase the speed of iteration</span></span>

<span data-ttu-id="a3c6e-110">“连续部署”的概念变得更加重要。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="a3c6e-111">连续部署是指能够频繁部署，可能每天进行多次部署。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="a3c6e-112">这些部署的目的不是为了提供修复，而是为了进行快速发布。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="a3c6e-113">通过尽可能顺畅可靠地完成新功能从开发到操作的过程，可以缩短新的业务逻辑转换为价值的时间。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="a3c6e-114">转向云计算意味着采用了利用“声明式”模板模型的部署解决方案，其中结束状态环境声明为文本，并发布到部署引擎中。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="a3c6e-115">此部署技术允许使用针对失败威胁的恢复能力进行大规模的快速更改，这是因为，在任何时候都可以不断重复部署，以保证结束状态。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="a3c6e-116">创建通过自动化支持此操作风格的工具和服务是对这些更改的响应。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="a3c6e-117">DSC 是一个提供声明式和幂等式（可重复）部署、配置和符合项的平台。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="a3c6e-118">通过 DSC 平台，你可以确保数据中心的组件采用了正确的配置，从而避免错误并防止代价高昂的部署失败。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="a3c6e-119">通过将 DSC 配置视为应用程序代码的一部分，DSC 可实现连续部署。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="a3c6e-120">DSC 配置应作为应用程序的一部分进行更新，从而确保部署应用程序所需知识始终保持最新且随时可以使用。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="a3c6e-121">“我已有 PowerShell，为什么还需要 Desired State Configuration？”</span><span class="sxs-lookup"><span data-stu-id="a3c6e-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="a3c6e-122">DSC 配置将意图或“我想要执行哪些操作”与执行或“我要如何操作”分离开来。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="a3c6e-123">这意味着资源内包含执行逻辑。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="a3c6e-124">当某个功能的 DSC 资源可用时，用户无需知道如何实现或部署该功能。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="a3c6e-125">这样，用户就可以专注于部署的结构。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="a3c6e-126">例如，PowerShell 脚本应如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3c6e-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="a3c6e-127">虽然此脚本简单易懂。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="a3c6e-128">但是，如果尝试将该脚本投入生产环境，将会遇到一些问题。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="a3c6e-129">如果该脚本连续运行两次会发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="a3c6e-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="a3c6e-130">如果 Bob 以前对共享具有完全访问权限会发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="a3c6e-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="a3c6e-131">为了弥补这些问题，“实际”版本的脚本将进一步类似于：</span><span class="sxs-lookup"><span data-stu-id="a3c6e-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="a3c6e-132">此脚本更加复杂，包含大量逻辑和错误处理。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="a3c6e-133">该脚本更为复杂，因为不再需要指出要执行哪些操作，而是说明如何执行。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="a3c6e-134">使用 DSC 可以指出要执行哪些操作，并且抽象出底层逻辑。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="a3c6e-135">此脚本格式清晰，简单易读。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="a3c6e-136">逻辑路径和错误处理仍存在于[资源](resources.md)实现中，但对脚本作者不可见。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-136">The logic paths and error handling are still present in the [resource](resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="a3c6e-137">将环境从结构中分离出来</span><span class="sxs-lookup"><span data-stu-id="a3c6e-137">Separating Environment from Structure</span></span>

<span data-ttu-id="a3c6e-138">DevOps 中的常见模式是多个环境用于部署。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="a3c6e-139">例如，可能有用于快速生成原型新代码的“开发”环境。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="a3c6e-140">“开发”环境中的代码进入“测试”环境，其他人员在其中验证新功能。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="a3c6e-141">最后，代码将进入“生产”或实时站点生产环境。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="a3c6e-142">DSC 配置可通过使用[配置数据](configData.md)适应此开发-测试-生产流程。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](configData.md).</span></span>
<span data-ttu-id="a3c6e-143">这可进一步抽象出托管节点的配置结构之间的差异。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="a3c6e-144">例如，可以定义需要 SQL server、IIS 服务器和中间层服务器的配置。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="a3c6e-145">无论哪个节点接收到此配置的不同部分，这三个元素会始终存在。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="a3c6e-146">对于开发环境，可以使用配置数据将所有三个元素指向同一计算机；对于测试环境，可以将这三个元素分离到三个不同的计算机；最后对于生产环境，又可以将其指向所有的生产服务器。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="a3c6e-147">若要部署到各种环境中，可以针对想要面向的环境，使用正确的配置数据调用 Start-DscConfiguration。</span><span class="sxs-lookup"><span data-stu-id="a3c6e-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3c6e-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3c6e-148">See Also</span></span>

[<span data-ttu-id="a3c6e-149">配置</span><span class="sxs-lookup"><span data-stu-id="a3c6e-149">Configurations</span></span>](configurations.md)

[<span data-ttu-id="a3c6e-150">配置数据</span><span class="sxs-lookup"><span data-stu-id="a3c6e-150">Configuration Data</span></span>](configData.md)

[<span data-ttu-id="a3c6e-151">资源</span><span class="sxs-lookup"><span data-stu-id="a3c6e-151">Resources</span></span>](resources.md)