---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Archive 资源
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954764"
---
# <a name="dsc-archive-resource"></a>DSC Archive 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 Archive 资源提供了在指定路径下解压缩存档 (.zip) 文件的机制。

## <a name="syntax"></a>语法

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|目标 |指定你想将存档内容提取至哪个位置。 |
|路径 |指定存档文件的源路径。 |
|校验和 |定义当确定两个文件是否相同时使用的类型。 如果未指定**校验和**，则只是文件或目录名用于比较。 有效值包括：**SHA-1**、**SHA-256**、**SHA-512**、**createdDate**、**modifiedDate**。 如果指定**校验和**不指定**验证**，则配置会失败。 |
|Force |某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。 使用 **Force** 属性覆盖此类错误。 默认值为 **False**。 |
|验证| 使用 **Checksum** 属性来确定存档是否和签名匹配。 如果指定**校验和**不指定**验证**，则配置会失败。 如果指定 **Validate** 而不指定 **Checksum**，则默认使用 _SHA-256_ **Checksum**。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |确定是否要检查存档的内容是否位于**目标**上。 将此属性设置为 **Present** 可确保内容存在。 将其设置为 **Absent** 可确保内容不存在。 默认值为 **Present**。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

以下示例演示如何使用 Archive 资源来确保名为 `Test.zip` 的存档文件的内容存在，并将内容提取到指定的目标位置。

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```