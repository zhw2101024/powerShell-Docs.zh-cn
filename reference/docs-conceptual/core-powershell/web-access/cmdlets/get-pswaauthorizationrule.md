---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188902"
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>简述

返回一组 Windows PowerShell® Web 访问的授权规则。

## <a name="syntax"></a>语法

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>名称
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>说明

Get-PswaAuthorizationRule cmdlet 将返回一组 Windows PowerShell® Web 访问授权规则。
如果既没指定 Id 参数，也没指定 RuleName 参数，则此 cmdlet 将列出所有规则。 可使用 Id 参数筛选结果。

## <a name="parameters"></a>参数

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

指定此 cmdlet 应获取的规则标识符 (ID)。 如果不指定任何 ID，则此 cmdlet 将返回所有授权规则。

|||
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | 2                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | True (ByValue, ByPropertyName)       |
| 是否接受通配符？          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String\[\]&gt;

指定要检索的授权规则名称。 此参数将返回与此数组中的字符串规则名称完全匹配的任何规则。

|||
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | true                                 |
| 位置在哪里？                            | 2                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | True (ByValue, ByPropertyName)       |
| 是否接受通配符？          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。
有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。

## <a name="inputs"></a>输入

### <a name="int"></a>int\[\]

此 cmdlet 接受整数数组或字符串值数组作为输入。

### <a name="string"></a>String\[\]

此 cmdlet 接受整数数组或字符串值数组作为输入。

## <a name="outputs"></a>输出

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

此 cmdlet 将生成一个 PswaAuthorizationRule 对象作为输出。


## <a name="examples"></a>示例

### <a name="example-1"></a>示例 1

此示例将获取所有规则。

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>示例 2

此示例获取 ID 为 2 的规则。

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>示例 3 {#example-3 .subHeading}

此示例介绍 cmdlet 如何从管道接受值。
使用此 cmdlet 传递规则 ID 和规则名称。

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>相关主题

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)