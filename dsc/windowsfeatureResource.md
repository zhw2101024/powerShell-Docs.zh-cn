# DSC WindowsFeature 资源。

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsFeature** 资源提供了在目标节点上添加或删除角色和功能的机制。

## 语法

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| 名称| 指示想确保添加或删除的角色或功能的名称。 此参数与来自 [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet 的 __Name__ 属性一样，并非该角色或功能的显示名称。| 
| 凭据| 指示要用于添加或删除角色或功能的凭据。| 
| Ensure| 指示是否已添加角色或功能。 若要确保添加了角色或功能，请将此属性设置为“Present”。若要确保删除了角色或功能，请将此属性设为“Absent”。| 
| IncludeAllSubFeature| 将此属性设置为 __$true__ 以确保所有必需子功能的状态均为你通过 __Name__ 属性指定的功能的状态。| 
| LogPath| 指示你希望资源提供程序在其中记录操作的日志文件的路径。| 
| DependsOn| 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 
| 源| 指示要用于安装的源文件的位置（如有必要）。| 

## 示例
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

<!--HONumber=Feb16_HO4-->
