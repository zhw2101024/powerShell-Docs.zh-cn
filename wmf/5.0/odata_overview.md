---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 01d4989711c22db20431876c52740afb350caad0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="6a434-102">基于 OData 终结点生成 PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6a434-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>
<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="6a434-103">基于 OData 终结点生成 Windows PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="6a434-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>
--------------------------------------------------------------

<span data-ttu-id="6a434-104">**Export-ODataEndpointProxy** 是一个 cmdlet，它基于给定的 OData 终结点公开的功能生成一组 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a434-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="6a434-105">以下示例演示了如何使用此新的 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="6a434-105">The following example shows how to use this new cmdlet:</span></span>

<span data-ttu-id="6a434-106">\# Export-ODataEndpointProxy 的基本用例</span><span class="sxs-lookup"><span data-stu-id="6a434-106">\# Basic use case of Export-ODataEndpointProxy</span></span>

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

<span data-ttu-id="6a434-107">此功能的开发阶段仍然使用了部分关键用例，包括但不限于：</span><span class="sxs-lookup"><span data-stu-id="6a434-107">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="6a434-108">关联</span><span class="sxs-lookup"><span data-stu-id="6a434-108">Associations</span></span>
-   <span data-ttu-id="6a434-109">传输流数据</span><span class="sxs-lookup"><span data-stu-id="6a434-109">Passing streams</span></span>

<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="6a434-110">基于 OData 终结点和 ODataUtils 生成 Windows PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="6a434-110">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>
------------------------------------------------------------------------------
<span data-ttu-id="6a434-111">ODataUtils 模块允许从支持 OData 的 REST 终结点生成 Windows PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="6a434-111">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="6a434-112">Microsoft.PowerShell.ODataUtils Windows PowerShell 模块中具有以下增量增强功能。</span><span class="sxs-lookup"><span data-stu-id="6a434-112">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="6a434-113">将附加信息从服务器端终结点引导到客户端。</span><span class="sxs-lookup"><span data-stu-id="6a434-113">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="6a434-114">客户端分页支持</span><span class="sxs-lookup"><span data-stu-id="6a434-114">Client-side paging support</span></span>
-   <span data-ttu-id="6a434-115">通过使用 -Select 参数进行的服务器端筛选</span><span class="sxs-lookup"><span data-stu-id="6a434-115">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="6a434-116">对 Web 请求标头的支持</span><span class="sxs-lookup"><span data-stu-id="6a434-116">Support for web request headers</span></span>

<span data-ttu-id="6a434-117">由 Export-ODataEndPointProxy cmdlet 生成的代理 cmdlet 提供来自信息流（Windows PowerShell 5.0 的新功能）上的服务器端 OData 终结点的附加信息（在客户端代理生成期间使用的 $metadata 中未提及）。</span><span class="sxs-lookup"><span data-stu-id="6a434-117">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="6a434-118">下面举例说明了如何获取该信息。</span><span class="sxs-lookup"><span data-stu-id="6a434-118">Here is an example of how to get that information.</span></span>
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

<span data-ttu-id="6a434-119">你可以通过使用客户端分页支持从服务器端中分批获取记录。</span><span class="sxs-lookup"><span data-stu-id="6a434-119">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="6a434-120">当你必须通过网络从服务器获取大量数据时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="6a434-120">This is useful when you must get a large amount of data from the server over the network.</span></span>
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

<span data-ttu-id="6a434-121">生成的代理 cmdlet 支持 –Select 参数，你可以使用该参数作为筛选器以只接收客户端需要的记录属性。</span><span class="sxs-lookup"><span data-stu-id="6a434-121">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="6a434-122">由于是在服务器端进行筛选，因此这将减少通过网络传输的数据量。</span><span class="sxs-lookup"><span data-stu-id="6a434-122">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="6a434-123">Export-ODataEndpointProxy cmdlet 和由它生成的代理 cmdlet 现在支持 Headers 参数（提供作为哈希表的值），你可以使用该参数来引导服务器端 OData 终结点期望的任何附加信息。</span><span class="sxs-lookup"><span data-stu-id="6a434-123">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="6a434-124">在下面的示例中，你可以通过 Headers 为需要订阅密匙用以进行身份验证的服务引导订阅密匙。</span><span class="sxs-lookup"><span data-stu-id="6a434-124">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
