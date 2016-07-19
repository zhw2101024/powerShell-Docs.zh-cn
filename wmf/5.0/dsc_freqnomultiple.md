# RefreshMode 和 ConfigurationMode 的频率无需为彼此的倍数

在以前版本的 DSC 中，LCM 将 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 作为彼此的倍数。 在 WMF 5.0 RTM 中，将独立处理这些属性。 

有关详细信息，请参阅[配置本地配置管理器](https://msdn.microsoft.com/powershell/dsc/metaconfig)。

<!--HONumber=Jul16_HO1-->


