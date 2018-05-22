---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 用于从请求服务器查询节点信息的 DSC 函数。
ms.openlocfilehash: 069fc79a79fbd5f75bcce27f7f0bd95af0d7b1ad
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a><span data-ttu-id="cd554-103">用于从请求服务器查询节点信息的 DSC 函数。</span><span class="sxs-lookup"><span data-stu-id="cd554-103">DSC function to query node information from pull server.</span></span>

```powershell
function QueryNodeInformation
{
Param (
       [string] $Uri =
"http://localhost:7070/PSDSCComplianceServer.svc/Status",
       [string] $ContentType = "application/json"
     )

  Write-Host "Querying node information from pull server URI  = $Uri" -ForegroundColor Green

  Write-Host "Querying node status in content type  = $ContentType " -ForegroundColor Green

   $response = Invoke-WebRequest -Uri $Uri -Method Get -ContentType $ContentType -UseDefaultCredentials -Headers
    @{Accept = $ContentType}

   if($response.StatusCode -ne 200)
 {
     Write-Host "node information was not retrieved." -ForegroundColor Red
 }

 $jsonResponse = ConvertFrom-Json $response.Content

  return $jsonResponse
}
```

<span data-ttu-id="cd554-104">用你的请求服务器的 URI 替换 `Uri` 参数。</span><span class="sxs-lookup"><span data-stu-id="cd554-104">Replace the `Uri` parameter with the URI for your pull server.</span></span> <span data-ttu-id="cd554-105">如果你想要 XML 格式的节点信息，请将 `ContentType` 设置为 `application/xml`。</span><span class="sxs-lookup"><span data-stu-id="cd554-105">If you want the node information in XML format, set `ContentType` to `application/xml`.</span></span>

<span data-ttu-id="cd554-106">若要从 `$json` 参数检索节点信息，请使用以下内容：</span><span class="sxs-lookup"><span data-stu-id="cd554-106">To retrieve the node information from the `$json` parameter, use the following:</span></span>

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```