---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC File 资源
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677454"
---
# <a name="dsc-file-resource"></a>DSC File 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 File 资源提供了管理目标节点上的文件和文件夹的机制。 **DestinationPath**并**SourcePath**必须都为可由目标节点访问。

## <a name="syntax"></a>语法

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

## <a name="properties"></a>“属性”

|属性       |说明                                                                   |必需|默认值|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|你想要确保在目标节点上的位置是`Present`或`Absent`。|是|否|
|属性     |目标的文件或目录的属性所需的状态。 有效的值为**存档**， **Hidden**， **ReadOnly**，以及**系统**。|否|无|
|校验和      |确定两个文件是否相同时要使用的校验和类型。 有效值包括：Sha-1、 SHA-256、 SHA-512、 createdDate、 modifiedDate。|否|仅在文件或目录名称进行比较。|
|目录       |仅当与一起使用时有效`File`类型。 指示为确保内容`Present`或`Absent`从目标文件。 |否|无|
|凭据     |所访问资源，如源文件所需的凭据。|否|目标节点的计算机帐户。 （见备注）|
|Ensure         |目标文件或目录的所需的状态。 |否|**存在**|
|Force          |重写访问操作会导致错误 （如覆盖的文件或删除目录不为空）。|否|`$false`|
|Recurse        |仅当与一起使用时有效`Directory`类型。 执行状态操作以递归方式将为所有子目录。|否|`$false`|
|DependsOn      |设置指定资源的依赖项。 此资源将仅在成功执行所有从属资源后执行。 您可以指定使用语法的从属资源`"[ResourceType]ResourceName"`。 请参阅 [about_DependsOn](../../../configurations/resource-depends-on.md)|否|无|
|SourcePath     |要从其中复制文件或文件夹资源路径。|否|无|
|类型           |正在配置资源的类型。 有效的值为`Directory`和`File`。|否|`File`|
|MatchSource    |确定是否资源应监视的初始复制后添加到源目录的新文件。 值为`$true`指示，初始复制后，任何新的源代码文件应复制到目标。 如果设置为`$False`，资源缓存源目录的内容，并忽略初始复制后添加的任何文件。|否|`$false`|

> [!WARNING]
> 如果未指定的值`Credential`或`PSRunAsCredential`(PS V.5)，该资源将用于目标节点的计算机帐户访问`SourcePath`。  当`SourcePath`是 UNC 共享，这可能导致"拒绝访问"错误。 请确保你的权限相应地，设置或使用`Credential`或`PSRunAsCredential`属性以指定应使用的帐户。

## <a name="present-vs-absent"></a>存在 vs。不存在

每个 DSC 资源执行基于的值为指定的不同操作`Ensure`属性。 执行以上属性决定状态操作指定的值。

### <a name="existence"></a>存在

当仅指定`DestinationPath`，资源可以确保该路径存在 (`Present`) 或不存在 (`Absent`)。

### <a name="copy-operations"></a>复制操作

当指定`SourcePath`和一个`DestinationPath`与`Type`的值**Directory**，到目标路径的资源副本源目录。 属性`Recurse`， `Force`，并`MatchSource`更改复制操作的类型执行，而`Credential`确定要用于访问源目录的帐户。

### <a name="limitations"></a>限制

如果指定的值`ReadOnly`有关`Attributes`属性一起`DestinationPath`，`Ensure = "Present"`将创建指定的路径时`Contents`会设置该文件的内容。  `Absent`状态操作会忽略`Attributes`属性完全，并删除任何文件在指定的路径。

## <a name="example"></a>示例

下面的示例从请求服务器复制的目录和子目录到目标节点使用文件资源。 如果操作成功，日志资源向事件日志写入一条确认消息。

源目录是 UNC 路径 (`\\PullServer\DemoSource`) 从请求服务器中共享。 `Recurse`属性可确保所有子目录也会都复制。

> [!IMPORTANT]
> 默认情况下，目标节点上的 LCM 本地系统帐户的上下文中执行。 若要授予访问权限**SourcePath**，目标节点的计算机帐户授予适当的权限。 **凭据**并**PSDSCRunAsCredential** (v5) 同时更改上下文 LCM 用来访问**SourcePath**。 仍需要授予访问权限将使用的帐户访问**SourcePath**。

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

有关更多在使用**凭据**在 DSC，请参阅[用户身份运行](../../../configurations/runAsUser.md)或[配置数据凭据](../../../configurations/configDataCredentials.md)。
