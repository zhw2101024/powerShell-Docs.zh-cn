---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="df35d-102">Test-DscConfiguration cmdlet 支持引用配置</span><span class="sxs-lookup"><span data-stu-id="df35d-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="df35d-103">已更新 Test-DscConfiguration cmdlet，以允许通过指定用于比较的参考配置文档来测试一个或多个目标节点的所需配置状态。</span><span class="sxs-lookup"><span data-stu-id="df35d-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="df35d-104">以下新参数集使用指定路径中的 DSC 配置，在指定目标节点上仅测试而绝不应用每个配置。</span><span class="sxs-lookup"><span data-stu-id="df35d-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="df35d-105">与 Start-DscConfiguration 和其他 DSC cmdlet，使用每个 MOF 的名称确定要在其上测试配置的目标节点。</span><span class="sxs-lookup"><span data-stu-id="df35d-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span> 

```powershell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

<span data-ttu-id="df35d-106">以下新参数集使用单个 DSC 配置，在指定的目标节点上仅测试而绝不应用配置。</span><span class="sxs-lookup"><span data-stu-id="df35d-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span> 

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

