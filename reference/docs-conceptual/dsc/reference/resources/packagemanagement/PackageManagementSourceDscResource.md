---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagementSource 资源
ms.openlocfilehash: 20b7851e44751d4bd0add718d2f7294d5215ab70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954784"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagementSource** 资源提供了一种在目标节点上注册或取消注册程序包管理源的机制。
**以这种方式注册的程序包管理源在系统上下文中注册，可供系统帐户或 DSC 引擎使用。** 此资源需要 [PowerShell 库](https://PowerShellGallery.com)中的 **PackageManagement** 模块。

> [!IMPORTANT]
> PackageManagement  模块应至少为版本 1.1.7.0，以下属性信息才正确。

## <a name="syntax"></a>语法

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|名称 |指定要在系统上注册或取消注册的包源名称。 |
|ProviderName |指定 OneGet 提供程序的名称，借此可以与包源进行互操作。 |
|SourceLocation |指定包源的 URI。 |
|InstallationPolicy |供提供程序使用，如内置的 Nuget 提供程序。 确定是否信任包的源。 可取值为：**Untrusted** 或 **Trusted**。 |
|SourceCredential |提供远程源上程序包的访问权限。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |确定是要注册还是要取消注册包源。 默认值为 **Present**。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

此示例使用 PackageManagementSource  DSC 资源注册 `https://nuget.org` 包源。

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```