# DSC Script 资源

 
> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **Script** 资源提供了在目标节点上运行 Windows PowerShell 脚本的机制。

## 语法

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| GetScript| 提供调用 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet 时运行的 Windows PowerShell 脚本块。 此块必返回一个哈希表。| 
| SetScript| 提供 Windows PowerShell 脚本块。 调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 时，将首先运行 **TestScript** 块。 如果 **TestScript** 块返回 **$false**，则将运行 **SetScript** 块。 如果 **TestScript** 块返回 **$true**，**SetScript** 块将不会运行。| 
| TestScript| 提供 Windows PowerShell 脚本块。 调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 时，将运行此块。 如果它返回 **$false**，将运行 SetScript 块。 如果它返回 **$true**，将不运行 SetScript 块。 调用 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet 时，也将运行 **TestScript** 块。 但是，在这种情况下，无论 TestScript 返回何值，都不会运行 **SetScript**。 如果实际配置与当前所需状态配置相匹配，**TestScript** 块必返回 True，如果不匹配，则返回 False。 （当前所需状态配置是在使用 DSC 的节点上执行的最后一个配置。）| 
| 凭据| 指示要用于运行此脚本的凭据（如果需要凭据）。| 
| DependsOn| 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。

## 示例
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { <# This must return a hash table #> }          
}
```

<!--HONumber=Feb16_HO4-->
