---
title:   DSC File 资源
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# DSC File 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 File 资源提供了管理目标节点上的文件和文件夹的机制。

## 语法
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ] 
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ] 
    [ MatchSource = [bool] ]
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| DestinationPath| 指示你想确保其中文件或目录状态的位置。| 
| 属性| 指定目标文件或目录的特性的所需状态。| 
| 校验和| 指示当确定两个文件是否相同时使用的校验和类型。 如果未指定__校验和__，则只是文件或目录名用于比较。 有效值包括：SHA-1、SHA-256、SHA-512、createdDate、modifiedDate。| 
| 目录| 指定文件的内容，例如特定字符串。| 
| 凭据| 指示需要进行访问时访问资源（例如源文件）所需的凭据。| 
| Ensure| 指示文件或目录是否存在。 将此属性设置为“Absent”可确保该文件或目录不存在。 将其设置为“Present”可确保该文件或目录确实存在。 默认值为“Present”。| 
| Force| 某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。 使用 Force 属性覆盖此类错误。 默认值为 __$false__。| 
| Recurse| 指示是否包含子目录。 将此属性设置为 __$true__ 以指示你想要包含子目录。 默认值为 __$false__。 **注意：**只有将 Type 属性设置为 Directory 时，此属性才有效。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 
| SourcePath| 指示要从其中复制文件或文件夹资源的路径。| 
| 类型| 指示正在配置的资源是目录还是文件。 将此属性设置为“Directory”可指示该资源是一个目录。 将其设置为“File”可指示该资源是一个文件。 默认值为“File”。| 
| MatchSource| 如果设置的默认值为 __$false__，则将在首次运用此配置时将源中的任何文件（如文件 A、B 和 C）添加到目标中。 如果已添加新文件 (D) 到源中，则即使稍后重新应用配置也不会将其添加到目标中。 如果值为 __$true__，则每当应用此配置时，在源上随后找到的新文件（如本示例中的文件 D）将会被添加到目标中。| 

## 示例

以下示例表明了如何使用 File 资源以确保源计算机（如“请求”服务器）上具有路径 `C:\Users\Public\Documents\DSCDemo\DemoSource` 的目录（以及所有子目录）也存在于目标节点上。 此外，完成时也会将确认消息写入日志，并包含用于确保记录操作前运行文件检查操作的声明。

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```



<!--HONumber=May16_HO3-->


