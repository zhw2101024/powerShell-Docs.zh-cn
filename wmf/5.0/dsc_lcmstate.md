# 关于 LCM 状态的详细信息

我们在公开有关 LCM 状态的详细信息方面进行了改进。 Get-DscLocalConfigurationManager 返回的 LCMState 现在可以包含以下值：

* **空闲**
* **忙碌**
* **PendingReboot**
* **PendingConfiguration**

我们还添加了 LCMStateDetail 属性，它包含有关状态的详细信息。


<!--HONumber=Jun16_HO4-->


