---
title: "直接调用 DSC 资源方法"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 1fe624c2532e44ed675762f3c141934fb4f0b60d

---

# 直接调用 DSC 资源方法

>适用于：Windows PowerShell 5.0

你可以使用 [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) cmdlet 直接调用 DSC 资源的函数或方法（基于 MOF 资源的 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 函数，或基于类的资源的 **Get**、**Set** 和 **Test** 方法）。 这可为想要使用 DSC 资源的第三方所用，也可以作为开发资源时非常有用的工具。 

此 cmdlet 通常与元配置属性 `refreshMode = 'Disabled'` 组合使用，但无论 **refreshMode** 设置为何值，都可以使用它。

在调用 **Invoke DscResource** cmdlet 时，可以通过使用 **Method** 参数来指定要调用的方法和函数。 你可以将哈希表作为 **Property** 参数的值进行传递，从而指定资源的属性。

直接调用资源方法的示例如下：

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

>**注意：**不支持直接调用复合资源方法。 请改为调用构成复合资源的基础资源的方法。

## 另请参阅
- [使用 MOF 编写自定义 DSC 资源](authoringResourceMOF.md) 
- [使用 PowerShell 类编写自定义 DSC 资源](authoringResourceClass.md)
- [调试 DSC 资源](debugResource.md)




<!--HONumber=Jun16_HO4-->


