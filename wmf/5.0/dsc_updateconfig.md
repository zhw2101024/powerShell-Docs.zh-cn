---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057564"
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="1d89c-102">DSC 配置的按需请求</span><span class="sxs-lookup"><span data-stu-id="1d89c-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="1d89c-103">新的 Update-DscConfiguration cmdlet 将触发对元配置中所定义请求服务器的请求。</span><span class="sxs-lookup"><span data-stu-id="1d89c-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="1d89c-104">该行为通常称为“立即请求”。</span><span class="sxs-lookup"><span data-stu-id="1d89c-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="1d89c-105">一旦触发，请求的行为将与以正常频率触发的行为完全相同：</span><span class="sxs-lookup"><span data-stu-id="1d89c-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="1d89c-106">将当前配置的校验和与请求服务器上配置的校验和相比较。</span><span class="sxs-lookup"><span data-stu-id="1d89c-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="1d89c-107">如果它们相同，则不应用配置而成功完成操作。</span><span class="sxs-lookup"><span data-stu-id="1d89c-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="1d89c-108">如果它们不同，则从请求服务器请求并应用配置。</span><span class="sxs-lookup"><span data-stu-id="1d89c-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="1d89c-109">**注意：** 如果元配置 RefreshMode = 'Push'，则此 cmdlet 将返回错误，从而当目标节点为“推送”模式时，此 cmdlet 将始终不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="1d89c-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
