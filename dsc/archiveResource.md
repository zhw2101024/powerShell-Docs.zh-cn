---
title:   DSC Archive 资源
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# DSC Archive 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 Archive 资源提供了在指定路径下解压缩存档 (.zip) 文件的机制。

## 语法 
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## “属性”

|  属性  |  说明   | 
|---|---| 
| 目标| 指定你想将存档内容提取至哪个位置。| 
| 路径| 指定存档文件的源路径。| 
| __校验和__| 定义当确定两个文件是否相同时使用的类型。 如果未指定__校验和__，则只是文件或目录名用于比较。 有效值包括：SHA-1、SHA-256、SHA-512、createdDate、modifiedDate、none（默认）。 如果指定__校验和__不指定__验证__，则配置会失败。| 
| Ensure| 确定是否要检查存档的内容是否位于__目标__上。 将此属性设置为 __Present__ 可确保内容存在。 将其设置为 __Absent__ 可确保内容不存在。 默认值为 __Present__。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 ResourceName、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 
| 验证| 使用校验和属性来确定存档是否和签名匹配。 如果指定校验和不指定验证，则配置会失败。 如果指定验证不指定校验和，则默认使用 SHA-256 校验和。| 
| Force| 某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。 使用 Force 属性覆盖此类错误。 默认值为 False。| 

## 示例

下面的示例将演示如何使用存档资源来确保名为 Test.zip 的存档文件的内容存在，并将内容提取至指定的目标位置。

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
} 
```



<!--HONumber=May16_HO3-->


