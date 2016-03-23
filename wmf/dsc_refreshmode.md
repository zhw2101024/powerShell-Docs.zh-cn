# RefreshMode 属性的附加值

此版本引入了新的 `RefreshMode` 值 **Disabled**。 设置为此模式时，LCM 不进行文档管理。 当使用第三方配置管理工具而不是 DSC 却仍通过 `Invoke-DscResource` cmdlet 利用 DSC 资源时，或你处于任何原因需要停止 DSC 处理时，可使用此模式。

```powershell
Configuration LCMSettings
{
    Node localhost
    {
        LocalConfigurationManager
        {
           RefreshMode = 'Disabled'
        }
    }
}

LCMSettings -OutputPath .\LCMSettings
Set-DscLocalConfigurationManager -Path .\LCMSettings -Verbose -ComputerName localhost
```
<!--HONumber=Mar16_HO2-->
