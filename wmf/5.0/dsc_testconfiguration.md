# Test-DscConfiguration cmdlet 支持引用配置

已更新 Test-DscConfiguration cmdlet，以允许通过指定用于比较的参考配置文档来测试一个或多个目标节点的所需配置状态。

以下新参数集使用指定路径中的 DSC 配置，在指定目标节点上仅测试而绝不应用每个配置。 与 Start-DscConfiguration 和其他 DSC cmdlet，使用每个 MOF 的名称确定要在其上测试配置的目标节点。 

```PowerShell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

以下新参数集使用单个 DSC 配置，在指定的目标节点上仅测试而绝不应用配置。 

```PowerShell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```


<!--HONumber=Jun16_HO4-->


