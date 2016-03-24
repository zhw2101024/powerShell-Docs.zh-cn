# RefreshMode 和 ConfigurationMode 的频率无需为彼此的倍数

在以前版本的 DSC 中，LCM 将 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 作为彼此的倍数，如[此处](http://blogs.msdn.com/b/powershell/archive/2013/12/09/understanding-meta-configuration-in-windows-powershell-desired-state-configuration.aspx)博客中所述。 在 WMF 5.0 RTM 中，将独立处理这些属性。 下表说明了此行为：

**请求**模式下的行为： 

|                                  |**元配置中的值**|**应用元配置后的值**|**发生请求的频率（分钟）**|**应用配置的频率（分钟）**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |                                    |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |40                                  |                                                |

**推送**模式下的行为：

|                                  |**元配置中的值**|**应用元配置后的值**|**应用配置的频率（分钟）**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |                                                |
<!--HONumber=Mar16_HO2-->
