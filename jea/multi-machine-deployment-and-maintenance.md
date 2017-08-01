---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "多计算机部署和维护"
ms.technology: powershell
ms.openlocfilehash: 8117d0d12c062b460cb7117b54c138c8db5a1d0c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="multi-machine-deployment-and-maintenance"></a><span data-ttu-id="40636-103">多计算机部署和维护</span><span class="sxs-lookup"><span data-stu-id="40636-103">Multi-machine Deployment and Maintenance</span></span>
<span data-ttu-id="40636-104">此时，你已多次将 JEA 部署到本地系统。</span><span class="sxs-lookup"><span data-stu-id="40636-104">At this point, you have deployed JEA to local systems several times.</span></span>
<span data-ttu-id="40636-105">因为你的生产环境可能由多台计算机组成，因此请务必演练部署过程中必须在每台计算机上重复的关键步骤。</span><span class="sxs-lookup"><span data-stu-id="40636-105">Because your production environment probably consists of more than one machine, it's important to walk through the critical steps in the deployment process that must be repeated on each machine.</span></span>

## <a name="high-level-steps"></a><span data-ttu-id="40636-106">大致步骤：</span><span class="sxs-lookup"><span data-stu-id="40636-106">High Level Steps:</span></span>
1.  <span data-ttu-id="40636-107">将你的模块（及角色功能）复制到每个节点。</span><span class="sxs-lookup"><span data-stu-id="40636-107">Copy your modules (with Role Capabilities) to each node.</span></span>
2.  <span data-ttu-id="40636-108">将你的会话配置文件复制到每个节点。</span><span class="sxs-lookup"><span data-stu-id="40636-108">Copy your session configuration files to each node.</span></span>
3.  <span data-ttu-id="40636-109">使用你的会话配置运行 `Register-PSSessionConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="40636-109">Run `Register-PSSessionConfiguration` with your session configuration.</span></span>
4.  <span data-ttu-id="40636-110">在安全的位置保留会话配置和工具包的一份副本。</span><span class="sxs-lookup"><span data-stu-id="40636-110">Keep a copy of your session configuration and toolkits in a secure location.</span></span>
<span data-ttu-id="40636-111">进行修改时，最好拥有“单一事实来源”。</span><span class="sxs-lookup"><span data-stu-id="40636-111">As you make modifications, it's good to have a "single source of truth."</span></span>

## <a name="example-script"></a><span data-ttu-id="40636-112">示例脚本</span><span class="sxs-lookup"><span data-stu-id="40636-112">Example Script</span></span>
<span data-ttu-id="40636-113">以下是部署的一个示例脚本。</span><span class="sxs-lookup"><span data-stu-id="40636-113">Here's an example script for deployment.</span></span>
<span data-ttu-id="40636-114">若要在你的环境中使用它，需使用实际文件共享和模块的名称/路径。</span><span class="sxs-lookup"><span data-stu-id="40636-114">To use it in your environment, you'll have to use the names/paths of real file shares and modules.</span></span>
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## <a name="modifying-capabilities"></a><span data-ttu-id="40636-115">修改功能</span><span class="sxs-lookup"><span data-stu-id="40636-115">Modifying Capabilities</span></span>
<span data-ttu-id="40636-116">当处理多台计算机时，请务必以一致的方式推行修改。</span><span class="sxs-lookup"><span data-stu-id="40636-116">When dealing with many machines, it's important that modifications are rolled out in a consistent manner.</span></span>
<span data-ttu-id="40636-117">JEA 拥有 DSC 资源时，这将帮助确保你的环境保持同步。</span><span class="sxs-lookup"><span data-stu-id="40636-117">Once JEA has a DSC Resource, this will help ensure your environment is in sync.</span></span>
<span data-ttu-id="40636-118">在此之前，我们强烈建议你保留会话配置的主副本，并在每次修改后进行重新部署。</span><span class="sxs-lookup"><span data-stu-id="40636-118">Until that time, we highly recommend you keep a master copy of your session configurations and re-deploy each time you make a modification.</span></span>

## <a name="removing-capabilities"></a><span data-ttu-id="40636-119">删除功能</span><span class="sxs-lookup"><span data-stu-id="40636-119">Removing Capabilities</span></span>
<span data-ttu-id="40636-120">若要从系统中删除 JEA 配置，请在每台计算机上使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="40636-120">To remove your JEA configuration from your systems, use the following command on each machine:</span></span>
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```

