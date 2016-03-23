# DSC Registry 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **Registry** 资源提供了在目标节点上管理注册表项和值的机制。

## 语法

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## “属性”
|  属性  |  说明   | 
|---|---| 
| 键| 指示要确保其特定状态的注册表项的路径。 路径必须包含配置单元。| 
| ValueName| 指示注册表值的名称。| 
| Ensure| 指示项和值是否存在。 将此属性设置为“Present”以确保其存在。 将此属性设置为“Absent”以确保其不存在。 默认值为“Present”。| 
| Force| 如果指定的注册表项存在，__Force__ 将用新值覆盖它。| 
| Hex| 指示是否以十六进制格式表示数据。 如果指定此项，则以十六进制格式显示 DWORD/QWORD 值数据。 对其他类型无效。 默认值为 __$false__。| 
| DependsOn| 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 
| ValueData| 注册表值的数据。| 
| ValueType| 指示值的类型。 支持的类型有： 
<ul><li>字符串 (REG_SZ)</li>


<li>二进制文件 (REG-BINARY)</li>


<li>Dword 32 位 (REG_DWORD)</li>


<li>Qword 64 位 (REG_QWORD)</li>


<li>多字符串 (REG_MULTI_SZ)</li>


<li>可扩展字符串 (REG_EXPAND_SZ)</li></ul>

## 示例
```powershell
Registry RegistryExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Key = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
    ValueName = "TestValue"
    ValueData = "TestData"
}
```

<!--HONumber=Feb16_HO4-->
