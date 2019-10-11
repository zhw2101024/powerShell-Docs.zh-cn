---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC File 资源
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954674"
---
# <a name="dsc-file-resource"></a>DSC File 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **File** 资源提供用于管理目标节点上的文件和文件夹的机制。 目标节点必须能够访问 **DestinationPath** 和 **SourcePath**。

## <a name="syntax"></a>语法

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|DestinationPath |想要通过 **Ensure** 确保目标节点上的位置 **Present** 或 **Absent**。 |
|属性 |目标文件或目录的特性的所需状态。 有效值包括 Archive  、Hidden  、ReadOnly  和 System  。 |
|校验和 |当确定两个文件是否相同时使用的校验和类型。 有效值包括：**SHA-1**、**SHA-256**、**SHA-512**、**createdDate**、**modifiedDate**。 |
|目录 |仅当与 **Type** **File** 一起使用时才有效。 指示要 **Ensure** 的内容在目标文件中的 **Present** 或 **Absent** 状态。 |
|凭据 |访问资源（例如源文件）所需的凭据。 |
|Force |覆盖将导致错误的访问操作（如覆盖文件或删除不为空的目录）。 默认值为 `$false`。 |
|Recurse |仅当与 **Type** **Directory** 类型一起使用时才有效。 以递归方式对所有子目录执行状态操作。 默认值为 `$false`。 |
|SourcePath |要从其中复制文件或文件夹资源的路径。 |
|类型 |正在配置的资源的类型。 有效值为 **Directory** 和 **File**。 默认值为 **File**。 |
|MatchSource |确定资源是否应监视初始复制之后添加到源目录的新文件。 `$true` 值表示，在初始复制之后，任何新的源文件都应复制到目标位置。 如果设置为 `$false`，资源将缓存源目录的内容，并忽略初始复制之后添加的任何文件。 默认值为 `$false`。 |

> [!WARNING]
> 如果没有为 **Credential** 或 **PSRunAsCredential** 指定值，则资源将使用目标节点的计算机帐户访问 **SourcePath**。 如果 **SourcePath** 是 UNC 共享，这可能导致“拒绝访问”错误。 请确保相应地设置权限，或者使用 **Credential** 或 **PSRunAsCredential** 属性指定应该使用的帐户。

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |确定文件和 **Destination** 中的 **Contents** 是否应该存在。 将此属性设置为 **Present** 可确保文件存在。 将其设置为 **Absent** 可确保内容不存在。 默认值为 **Present**。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

### <a name="additional-information"></a>附加信息

- 仅指定 **DestinationPath** 时，资源可确保该路径存在 (**Present**) 或不存在 (**Absent**)。
- 当使用 **Directory** 的 **Type** 值指定 **SourcePath** 和 **DestinationPath** 时，资源会将源目录复制到目标路径。 属性 **Recurse**、**Force** 和 **MatchSource** 更改所执行的复制操作的类型，而 **Credential** 决定使用哪个帐户来访问源目录。
- 如果为 **Attributes** 属性指定的值为 **ReadOnly** 并指定 **DestinationPath**，则 **Ensure** **Present** 将创建指定的路径，而 **Contents** 将设置文件的内容。 **Ensure** **Absent** 设置将完全忽略 **Attributes** 属性，并删除指定路径下的任何文件。

## <a name="example"></a>示例

下面的示例使用文件资源将目录及其子目录从拉取服务器复制到目标节点。 如果操作成功，日志资源会向事件日志写入一条确认消息。

源目录是从拉取服务器共享的 UNC 路径 (`\\PullServer\DemoSource`)。 **Recurse** 属性还可确保复制所有子目录。

> [!IMPORTANT]
> 默认情况下，目标节点上的 LCM 在本地系统帐户的上下文中执行。 要授予对 SourcePath  的访问权限，请为目标节点的计算机帐户授予适当权限。 **Credential** 和 **PSDSCRunAsCredential** 都更改了 LCM 用于访问 **SourcePath** 的上下文。 仍需要向将用于访问 SourcePath  的帐户授予访问权限。

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

有关在 DSC 中使用 Credentials  的详细信息，请参阅[以用户身份运行](../../../configurations/runAsUser.md)或[配置数据凭据](../../../configurations/configDataCredentials.md)。