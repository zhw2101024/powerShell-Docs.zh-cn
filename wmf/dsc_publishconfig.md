# 传递配置文档而不应用

**Publish-DscConfiguration** cmdlet 将配置 MOF 文件复制到目标节点上，但不应用该配置。 将在下次一致性通过时或运行 `Update-DscConfiguration` cmdlet 时应用此配置。

```powershell
Publish-DscConfiguration [-Path] <string> [[-ComputerName] <string[]>] [-Force] [-Credential <pscredential>] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]

Publish-DscConfiguration [-Path] <string> -CimSession <CimSession[]> [-Force] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<!--HONumber=Mar16_HO2-->
