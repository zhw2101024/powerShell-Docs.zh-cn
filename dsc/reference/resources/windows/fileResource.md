---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC File 资源
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077324"
---
# <a name="dsc-file-resource"></a>DSC File 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 File 资源提供了管理目标节点上的文件和文件夹的机制。 目标节点必须能够访问 DestinationPath 和 SourcePath。

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
|DestinationPath|想要确保目标节点上的位置是 `Present` 或 `Absent`。|是|否|
|属性     |目标文件或目录的特性的所需状态。 有效值包括 Archive、Hidden、ReadOnly 和 System。|否|无|
|校验和      |当确定两个文件是否相同时使用的校验和类型。 有效值包括：SHA-1、SHA-256、SHA-512、createdDate 和 modifiedDate。|否|只比较文件或目录名。|
|目录       |仅当与 `File` 类型一起使用时才有效。 指示要确保的内容是目标文件中的 `Present` 或 `Absent`。 |否|无|
|凭据     |访问资源（例如源文件）所需的凭据。|否|目标节点的计算机帐户。 （见备注）|
|Ensure         |目标文件或目录的所需状态。 |否|**存在**|
|Force          |覆盖将导致错误的访问操作（如覆盖文件或删除不为空的目录）。|否|`$false`|
|Recurse        |仅当与 `Directory` 类型一起使用时才有效。 以递归方式对所有子目录执行状态操作。|否|`$false`|
|DependsOn      |设置指定资源的依赖项。 此资源仅在成功执行任何从属资源之后执行。 可以使用语法 `"[ResourceType]ResourceName"` 指定从属资源。 请参阅 [about_DependsOn](../../../configurations/resource-depends-on.md)|否|无|
|SourcePath     |要从其中复制文件或文件夹资源的路径。|否|无|
|类型           |正在配置的资源的类型。 有效值为 `Directory` 和 `File`。|否|`File`|
|MatchSource    |确定资源是否应监视初始复制之后添加到源目录的新文件。 `$true` 值表示，在初始复制之后，任何新的源文件都应复制到目标位置。 如果设置为 `$False`，资源将缓存源目录的内容，并忽略初始复制之后添加的任何文件。|否|`$false`|

> [!WARNING]
> 如果没有为 `Credential` 或 `PSRunAsCredential` 指定值 (PS V.5)，资源将使用目标节点的计算机帐户访问 `SourcePath`。  如果 `SourcePath` 是 UNC 共享，这可能导致“拒绝访问”错误。 请确保相应地设置权限，或者使用 `Credential` 或 `PSRunAsCredential` 属性指定应该使用的帐户。

## <a name="present-vs-absent"></a>存在与不存在

每个 DSC 资源根据你为 `Ensure` 属性指定的值执行不同的操作。 为上述属性指定的值决定执行的状态操作。

### <a name="existence"></a>存在

仅指定 `DestinationPath` 时，资源将确保该路径存在 (`Present`) 或不存在 (`Absent`)。

### <a name="copy-operations"></a>复制操作

当使用目录的 `Type` 值指定 `SourcePath` 和 `DestinationPath` 时，资源会将源目录复制到目标路径。 属性 `Recurse`、`Force` 和 `MatchSource` 更改所执行的复制操作的类型，而 `Credential` 决定使用哪个帐户来访问源目录。

### <a name="limitations"></a>限制

如果在 `DestinationPath` 旁边为 `Attributes` 属性指定了 `ReadOnly` 值，`Ensure = "Present"` 将创建指定的路径，而 `Contents` 将设置文件的内容。  `Absent` 状态操作将完全忽略 `Attributes` 属性，并删除指定路径上的任何文件。

## <a name="example"></a>示例

下面的示例使用文件资源将目录及其子目录从拉取服务器复制到目标节点。 如果操作成功，日志资源会向事件日志写入一条确认消息。

源目录是从拉取服务器共享的 UNC 路径 (`\\PullServer\DemoSource`)。 `Recurse` 属性还确保复制所有子目录。

> [!IMPORTANT]
> 默认情况下，目标节点上的 LCM 在本地系统帐户的上下文中执行。 要授予对 SourcePath 的访问权限，请为目标节点的计算机帐户授予适当权限。 Credential 和 PSDSCRunAsCredential (v5) 都更改了 LCM 用于访问 SourcePath 的上下文。 仍需要向将用于访问 SourcePath 的帐户授予访问权限。

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

有关在 DSC 中使用 Credentials 的详细信息，请参阅[以用户身份运行](../../../configurations/runAsUser.md)或[配置数据凭据](../../../configurations/configDataCredentials.md)。
