# DSC Package 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **Package** 资源提供了在目标节点上安装或卸载程序包（如 Windows Installer 和 setup.exe 程序包）的机制。

## 语法

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## “属性”
|  属性  |  说明   | 
|---|---| 
| 名称| 指示要确保其特定状态的程序包的名称。| 
| 路径| 指示程序包所在的路径。| 
| ProductId| 指示唯一标识程序包的产品 ID。| 
| 参数| 列出按照原样传输到程序包的参数字符串。| 
| 凭据| 提供远程源上程序包的访问权限。 此属性不用于安装程序包。 程序包始终安装在本地系统上。| 
| Ensure| 指示程序包是否已安装。 将此属性设置为“Absent”以确保未安装程序包（如果已安装则卸载程序包）。 将其设置为“Present”（默认值）以确保已安装程序包。| 
| LogPath| 指示你希望提供程序用于保存安装或卸载程序包的日志文件的完整路径。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"``。| 
| ReturnCode| 指示预期的返回代码。 如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。| 

## 示例

此示例将运行位于指定路径且具有指定产品 ID 的 .msi 安装程序。

```powershell
Package PackageExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path  = "$Env:SystemDrive\TestFolder\TestProject.msi"
    Name = "TestPackage"
    ProductId = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
} 
```
<!--HONumber=Feb16_HO4-->
