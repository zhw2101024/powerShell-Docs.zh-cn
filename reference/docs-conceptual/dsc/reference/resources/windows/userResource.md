---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC User 资源
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953004"
---
# <a name="dsc-user-resource"></a>DSC User 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **User** 资源提供在目标节点上管理用户帐户的机制。

## <a name="syntax"></a>语法

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|UserName |指示要确保其特定状态的帐户名。 |
|说明 |指示要用于用户帐户的说明。 |
|禁用 |指示帐户是否已启用。 将此属性设置为 `$true` 可确保已禁用保此帐户，将其设置为 `$false` 可确保已启用此帐户。 |
|FullName |表示包含要用于用户帐户的完整名称的字符串。 |
|密码 |指示要用于此帐户的密码。 |
|PasswordChangeNotAllowed |指示用户是否可以更改密码。 将此属性设置为 `$true` 可确保用户无法更改密码，将其设置为 `$false` 可允许用户更改密码。 默认值为 `$false`。 |
|PasswordChangeRequired |指定用户下次登录时是否必须更改密码。 要使用户必须更改密码，请将此属性设置为 `$true`。 默认值为 `$true`。 |
|PasswordNeverExpires |指示密码是否会过期。 若要确保此帐户的密码永不过期，请将此属性设置为 `$true`。 如果密码将过期，请将其设置为 `$false`。 默认值为 `$false`。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示帐户是否存在。 将此属性设置为 **Present** 可确保帐户存在，将其设置为 **Absent** 可确保帐户不存在。 默认值为 **Present**。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```