# 直接访问 DSC 资源方法


已添加 `Invoke-DscResource` cmdlet，以允许对 DSC 资源及其方法（Get、Set 或 Test）的直接访问。 希望利用 DSC 资源的第三方可以使用它。 此 cmdlet 通常与 `refreshMode = ‘Disabled’` 组合使用，但无论将 refreshMode 设置为何值，都可以使用它。 以下是如何使用此新 cmdlet 的一些示例:

## 确保文件存在

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## 测试文件存在

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## 获取文件内容

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```


<!--HONumber=Apr16_HO4-->


