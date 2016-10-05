## 如何解决“警告: 无法下载包‘你的包名称’”问题？




据报告，Install-Module 或 Update-Module 在某些计算机上有时会失败。
根据我们的调查，此问题与网络连接有关。
最近，我们更新了 NuGet 提供程序，使其可以可靠地下载包。
你可以按照以下说明安装 NuGet 提供程序的最新版本，然后安装或更新你的模块。
下面，我们使用“Azure”模块作为示例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```


<!--HONumber=Aug16_HO3-->


