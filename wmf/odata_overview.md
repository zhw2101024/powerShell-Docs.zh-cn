# 基于 OData 终结点生成 PowerShell Cmdlet
基于 OData 终结点生成 Windows PowerShell cmdlet
--------------------------------------------------------------

**Export-ODataEndpointProxy** 是一个 cmdlet，它基于给定的 OData 终结点公开的功能生成一组 Windows PowerShell cmdlet。

以下示例演示了如何使用此新的 cmdlet：

\# Export-ODataEndpointProxy 的基本用例

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

此功能的开发阶段仍然使用了部分关键用例，包括但不限于：
-   关联
-   传输流数据

基于 OData 终结点和 ODataUtils 生成 Windows PowerShell cmdlet
------------------------------------------------------------------------------
ODataUtils 模块允许从支持 OData 的 REST 终结点生成 Windows PowerShell cmdlet Microsoft.PowerShell.ODataUtils Windows PowerShell 模块中具有以下增量增强功能。
-   将附加信息从服务器端终结点引导到客户端。
-   客户端分页支持
-   通过使用 -Select 参数进行的服务器端筛选
-   对 Web 请求标头的支持

由 Export-ODataEndPointProxy cmdlet 生成的代理 cmdlet 提供来自信息流（Windows PowerShell 5.0 的新功能）上的服务器端 OData 终结点的附加信息（在客户端代理生成期间使用的 $metadata 中未提及）。 下面举例说明了如何获取该信息。
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

你可以通过使用客户端分页支持从服务器端中分批获取记录。 当你必须通过网络从服务器获取大量数据时，这非常有用。
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

生成的代理 cmdlet 支持 –Select 参数，你可以使用该参数作为筛选器以只接收客户端需要的记录属性。 由于是在服务器端进行筛选，因此这将减少通过网络传输的数据量。
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Export-ODataEndpointProxy cmdlet 和由它生成的代理 cmdlet 现在支持 Headers 参数（提供作为哈希表的值），你可以使用该参数来引导服务器端 OData 终结点期望的任何附加信息。 在下面的示例中，你可以通过 Headers 为需要订阅密匙用以进行身份验证的服务引导订阅密匙。
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```


<!--HONumber=Jun16_HO4-->


