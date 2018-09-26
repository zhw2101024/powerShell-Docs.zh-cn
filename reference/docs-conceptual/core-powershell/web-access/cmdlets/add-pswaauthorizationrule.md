---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: fe2b71dcfa870ba3f92484ae3fd3c45b3107a1bc
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523070"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>简述

向 Windows PowerShell Web 访问授权规则集添加新的授权规则。

## <a name="syntax"></a>语法

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>说明

Add-PswaAuthorizationRule cmdlet 向 Windows PowerShell(r) Web 访问授权规则集添加新的授权规则。

必须为此规则指定用户、计算机和 Windows PowerShell 终结点。 既可通过个人用户帐户和计算机名称来指定用户和计算机，也可通过指定组来完成此操作。

对于已加入 Active Directory 域的计算机，cmdlet 将使用计算机的安全标识符 (SID) 来创建该规则。 这允许你在登录页的“计算机名”字段中使用短名称、完全限定的域名 (FQDN) 或 IP 地址。

对于未加入 Active Directory 域的计算机，cmdlet 将使用管理员提供的计算机名来创建规则。 要成功连接到此计算机，最终用户必须提供与规则中出现的完全一致的计算机名。

如果网络上出现多个具有相同名称的计算机，则短名称可解析为多台计算机。 这可能在创建连接时造成多义性。 例如，如果名为“Server1”的工作组计算机具有一条规则，与此同时，在网络中又加入一个名为 server1.contoso.com 的新计算机，则成功通过授权规则进行了验证，且 Windows PowerShell Web 访问尝试与名为“Server1”的计算机创建连接。 则无法保证所连接的对象是指定的工作组计算机；该操作有可能连接到工作组，也有可能连接到名为“Server1”的域计算机。 要减少多义性，建议尽量为目标计算机使用 FQDN 来创建授权规则。

授权规则评估 Windows PowerShell Web 访问用户的主登录凭据，而非备用凭据（有关备用凭据集，请前往登录页中的“可选连接设置”查看）。 有关以下内容的示例，请参阅示例 6。

## <a name="parameters"></a>参数

### <a name="-computergroupname-string"></a>-ComputerGroupName \<String\>

指定 Active Directory 域服务 (AD DS) 中计算机组的名称，或指定此规则授予访问权限的本地组名称。

|||
|-|-|
| 别名                     | 无                  |
| 是否必需？                   | true                  |
| 位置在哪里？                   | named                 |
| 默认值               | 无                  |
| 是否接受管道输入？      | True (ByPropertyName) |
| 是否接受通配符？ | false                 |

### <a name="-computername-string"></a>-ComputerName \<String\>

指定此规则授予访问权限的计算机名。

|||
|-|-|
| 别名                     | 无                  |
| 是否必需？                   | true                  |
| 位置在哪里？                   | named                 |
| 默认值               | 无                  |
| 是否接受管道输入？      | True (ByPropertyName) |
| 是否接受通配符？ | false                 |

### <a name="-configurationname-string"></a>-ConfigurationName \<String\>

指定此规则授予访问权限的 Windows PowerShell 会话配置的名称（又称为运行空间）。

|||
|-|-|
| 别名                     | 无                  |
| 是否必需？                   | true                  |
| 位置在哪里？                   | named                 |
| 默认值               | 无                  |
| 是否接受管道输入？      | True (ByPropertyName) |
| 是否接受通配符？ | false                 |

### <a name="-credential--pscredential"></a>-Credential  \<PSCredential\>

为要用于更改 Windows PowerShell Web 访问授权规则的用户帐户指定 PSCredential 对象。 如果不添加此参数，cmdlet 将使用当前登录的用户帐户。 要获取 PSCredential 对象（用于以远程方式添加授权规则），请运行 [Get-Credential cmdlet](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential)。

|||
|-|-|
| 别名                     | 无  |
| 是否必需？                   | false |
| 位置在哪里？                   | named |
| 默认值               | 无  |
| 是否接受管道输入？      | false |
| 是否接受通配符？ | false |

### <a name="-force"></a>-Force

强制运行命令而不要求用户确认。 此外，在输入简单或短计算机名时（例如不是域名的名称，或不是完全限定的名称），系统还会出现确认提示。 该确认请求旨在保证安全，仅当计算机在工作组中时，才可使用简单名称来添加计算机。

|||
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-rulename-string"></a>-RuleName \<String\>

为此规则指定友好名称。

|||
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | True (ByPropertyName)                |
| 是否接受通配符？          | false                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<String\[\]\>

指定 AD DS 中一个或多个用户组的名称，或指定此规则授予访问权限的本地组名称。

|||
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | true                                 |
| 位置在哪里？                            | named                                |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | True (ByPropertyName)                |
| 是否接受通配符？          | false                                |

### <a name="-username-string"></a>-UserName \<String\[\]\>

指定此规则向其授予访问权限的一个或多个用户。 用户名可以是网关计算机上的本地用户帐户，也可以是 AD DS 中的用户。 格式为 `domain\user` 或 `computer\user`。

|||
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | true                                 |
| 位置在哪里？                            | 1                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | True (ByValue, ByPropertyName)       |
| 是否接受通配符？          | false                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

此 cmdlet 支持通用参数：

-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。
有关详细信息，请参阅 [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters)。

## <a name="inputs"></a>输入

### <a name="string"></a>字符串

此 cmdlet 接受字符串或字符串数组作为输入。

### <a name="string"></a>String\[\]

此 cmdlet 接受字符串或字符串数组作为输入。

## <a name="outputs"></a>输出

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

此 cmdlet 将返回授权规则对象。

## <a name="examples"></a>示例

### <a name="example-1"></a>示例 1

此示例授予对 SMAdmins 组中的用户在 srv2 上的会话配置 PSWAEndpoint（一个受限运行空间）的访问权限。

> [!NOTE]
> 该计算机名必须是完全限定的域名 (FQDN)。 管理员定义受限制的会话配置或运行空间，这是一系列可供最终用户运行的有限 cmdlet 和任务。 定义受限制的运行空间可阻止用户访问不在允许的 Windows PowerShell(r) 运行空间中的其他计算机，提高连接安全性。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) 或[安装和使用 Windows PowerShell Web 访问](../install-and-use-windows-powershell-web-access.md)。

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>示例 2

此示例在 srv2 上为名为 `contoso\user1`、`contoso\user2` 和 `contoso\user3` 用户中的用户，授予默认 Windows PowerShell 会话配置访问权限 `Microsoft.PowerShell`。 此 cmdlet 将创建三条规则（每人一条）。

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>示例 3

此示例将说明如何通过管道输入用户名值。

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>示例 4

此示例说明如何按属性名从管道为所有参数获取值。

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>示例 5

此示例将添加一条规则，允许名为 `PswaServer\ChrisLocal` 的本地用户访问名为 srv1.contoso.com 的服务器。

此示例对网关位于工作组，目标计算机位于域中的方案进行了说明。 授权规则适用于网关上的本地用户。 在 Windows PowerShell Web 访问登录页中，要成功进行身份验证，用户必须在“可选连接设置”中提供备用凭据组。 网关服务器使用一组额外的凭据，在服务器名为 srv1.contoso.com 的目标计算机上对用户进行身份验证。

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>示例 6

此示例允许全体用户访问所有计算机中的全部终结点。 这实际上关闭了授权规则。

> [!NOTE]
> 出于安全敏感部署的考虑，除测试环境或对安全要求不高的部署之外，不建议使用通配符 `*`。

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>另请参阅

[Get-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/library/jj592894(v=wps.630).aspx)

[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)
