---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "测试 pswaauthorizationrule"
ms.technology: powershell
ms.openlocfilehash: 1b480b68c7ce2064f42281d8c5d76156a39e0222
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
#  <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

##  <a name="synopsis"></a>简述

验证是否为特定用户、计算机或终结点设置了规则。

## <a name="syntax"></a>语法

###  <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

###  <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>说明

Test-PswaAuthorizationRule 用于验证是否为特定用户、计算机或终结点设置了规则。
此 cmdlet 还可用于测试授权规则，以验证某个特定用户、计算机或终结点的访问请求是否被授权。
默认情况下，此 cmdlet 评估授权文件中的所有规则。
但是，可指定一个用于测试的规则子集。

可使用此 cmdlet 对身份验证失败进行故障排除。

此 cmdlet 的参数对应于 Windows PowerShell®Web 访问登录页上的字段。

## <a name="parameters"></a>参数

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;String&gt;

指定要测试的计算机的名称。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | true                                 |
| 位置在哪里？                            | 2                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;String&gt;

指定要测试的 Windows PowerShell 会话配置的名称（又称为终结点或运行空间）。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | 3                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

指定要测试的连接 URI。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | true                                 |
| 位置在哪里？                            | 2                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

为要用于测试 Windows PowerShell Web 访问授权规则的用户帐户指定 PSCredential 对象。 如果不添加此参数，cmdlet 将使用当前登录的用户帐户。 要获取 PSCredential 对象（用于以远程方式测试授权规则），请运行 [Get-Credential cmdlet](http://go.microsoft.com/fwlink/?LinkID=293936)。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

指定要测试的规则子集。 如果此参数未指定，则此 cmdlet 将针对所有授权规则进行测试。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | True (ByValue)                       |
| 是否接受通配符？          | false                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;String&gt;

指定要测试的用户的名称。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | true                                 |
| 位置在哪里？                            | 1                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。
有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。

## <a name="inputs"></a>输入

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

此 cmdlet 接受一组 PswaAuthorizationRule 对象作为输入。

##  <a name="outputs"></a>输出

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

此 cmdlet 生成一组 PswaAuthorizationRule 对象作为输出。

## <a name="examples"></a>示例

### <a name="example-1"></a>示例 1

此示例测试所有授权规则，以显示所有允许用户 contoso\\mhanson 连接到计算机 srv2 的规则，并使用名为 test 的 Windows PowerShell 会话配置。

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>示例 2

此示例测试所有授权规则，以检查在用户 contoso\\mhanson 上应用了哪些授权规则。

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

##  <a name="related-topics"></a>相关主题

-  [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
-  [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
-  [Install-PswaWebApplication](install-pswawebapplication.md)
-  [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
