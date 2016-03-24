# DSC Log 资源 

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 内的 __Log__ 资源提供了将消息写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的机制。

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

## “属性”
|  属性  |  说明   | 
|---|---| 
| 消息| 指示要写入 Microsoft-Windows-Desired State Configuration/Analytic 事件日志的消息。| 
| DependsOn | 指示必须先运行其他资源的配置，再写入此日志消息。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 

## 示例

下面的示例演示如何在 Microsoft-Windows-Desired State Configuration/Analytic 事件日志中纳入消息。

> **注意**：如果你在配置此资源后运行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，它将始终返回 **$false**。

```powershell 
Log LogExample
{
    Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
} 
```

<!--HONumber=Feb16_HO4-->
