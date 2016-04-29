# 编写单实例 DSC 资源（最佳做法）

>**注意：**本主题介绍了在配置中定义仅允许单个配置实例的 DSC 资源的最佳做法。 目前还没有用于实现此操作的内置 DSC 功能。 这在
>将来可能会发生改变。

在一些情况下，你不希望允许在配置中多次使用某一资源。 例如， 
在 [xTimeZone](https://github.com/PowerShell/xTimeZone) 资源的早期实现中，配置可以多次调用资源，在每个资源块中将时区设置为不同的设置：

```powershell
Configuration SetTimeZone 
{ 
    Param 
    ( 
        [String[]]$NodeName = $env:COMPUTERNAME 

    ) 

    Import-DSCResource -ModuleName xTimeZone 
 
 
    Node $NodeName 
    { 
         xTimeZone TimeZoneExample 
         { 
        
            TimeZone = 'Eastern Standard Time' 
         } 

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }        

    } 
} 
```

这是由 DSC 资源键的作用方式导致的。 一个资源必须具有至少一个键属性。 如果资源实例的所有键属性的值组合是唯一的， 
那么该实例也被视为是唯一的。 在其之前的实现中，[xTimeZone](https://github.com/PowerShell/xTimeZone) 资源仅有一个属性--**TimeZone**， 
该属性必须是一个键。 因此，如上所示的配置可以编译和运行，而不会发出警告。 每个 **xTimeZone** 资源块都被视为是唯一的。 这将导致 
配置重复应用于该节点，反复循环时区。

为确保配置只能为目标节点设置一次时区，已更新资源以添加另一属性，即 **IsSingleInstance**，该属性已成为键属性。 
已使用 **ValueMap** 将 **IsSingleInstance** 限制为单个值，即“Yes”。 该资源的旧 MOF 架构为：

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

该资源更新后的 MOF 架构为：

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

资源脚本也已更新为使用新参数。 以下是旧资源脚本：

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Invoke-Expression "tzutil.exe /g"

    $returnValue = @{
        TimeZone = $CurrentTimeZone
    }

    #Output the target resource
    $returnValue
}


function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )
    
    #Output the result of Get-TargetResource function.
    $GetCurrentTimeZone = Get-TargetResource -TimeZone $TimeZone

    If($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        Try
        {
            Write-Verbose "Setting the TimeZone"
            Invoke-Expression "tzutil.exe /s ""$TimeZone"""
        }
        Catch
        {
            $ErrorMsg = $_.Exception.Message
            Write-Verbose $ErrorMsg
        }
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $Get = Get-TargetResource -TimeZone $TimeZone

    If($TimeZone -eq $Get.TimeZone)
    {
        return $true
    }
    Else
    {
        return $false
    }
}

Export-ModuleMember -Function *-TargetResource
```

以下是更新后的脚本。 请注意，**IsSingleInstance** 强制参数已被添加到每个函数中。

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance, 

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
    }

    #Output the target resource
    $returnValue
}


function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance, 

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )
    
    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone
    
    If($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        Try{
            if($CurrentTimeZone -ne $TimeZone){
                Write-Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
            else{
                Write-Verbose "TimeZone already set to $TimeZone"
            }
        }
        Catch{
            $ErrorMsg = $_.Exception.Message
            Write-Verbose $ErrorMsg
        }
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance, 

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    If($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    Else
    {
        return $false
    }
}

Function Get-TimeZone 
{
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone 
{
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone    
    }catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

请注意，**TimeZone** 属性不再是一个键。 现在，如果配置（通过使用两个带有不同 **TimeZone** 值的不同 **xTimeZone** 块）尝试设置时区两次，
尝试编译配置将会导致错误：

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and 
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the 
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property 
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
   

<!--HONumber=Apr16_HO1-->


