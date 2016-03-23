# New-Guid
通常脚本（或写入 DSC 资源）需要唯一标识符。 GUID 使用效果良好，并且调用 .NET Framework Guid 类即可轻松生成 GUID，但使用 cmdlet 可让尚不熟悉 .NET Framework 类的终端用户更容易发现此操作：

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
<!--HONumber=Mar16_HO2-->
