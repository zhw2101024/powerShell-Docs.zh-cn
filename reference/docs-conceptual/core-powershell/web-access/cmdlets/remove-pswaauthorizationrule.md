---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "删除 pswaauthorizationrule"
ms.technology: powershell
ms.openlocfilehash: d316cb98efc730ed3e99f6a5dac2b969e3437129
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
#  <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

##  <a name="synopsis"></a>简述

从 Windows PowerShell® Web 访问删除指定授权规则。

## <a name="syntax"></a>语法

###  <a name="id"></a>ID
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>规则
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>说明

从 Windows PowerShell Web 访问删除指定授权规则。

## <a name="parameters"></a>参数

### <a name="-force"></a>-Force

在不提示确认的情况下运行 cmdlet。 默认情况下，cmdlet 在继续之前将向你确认。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

指定要删除的一个或多个规则的标识符 (ID)。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | true                                 |
| 位置在哪里？                            | 2                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | True (ByValue, ByPropertyName)       |
| 是否接受通配符？          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

指定要删除的规则。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | true                                 |
| 位置在哪里？                            | 2                                    |
| 默认值                        | 无                                 |
| 是否接受管道输入？               | True (ByValue)                       |
| 是否接受通配符？          | false                                |

### <a name="-confirm"></a>-Confirm

运行 cmdlet 之前提示你进行确认。

|||  
|-|-|
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | false                                |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-whatif"></a>-WhatIf

显示如果运行 cmdlet 则会发生什么情况。 cmdlet 未运行。

|||  
|-|-|
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | false                                |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。
有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。

## <a name="inputs"></a>输入

###  <a name="int"></a>int\[\]

此 cmdlet 接受整数数组或接受 PswaAuthorizationRule 对象数组。

###  <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

此 cmdlet 接受整数数组或接受 PswaAuthorizationRule 对象数组。

##  <a name="outputs"></a>输出

此 cmdlet 不会生成任何输出。

## <a name="examples"></a>示例

### <a name="example-1"></a>示例 1

此示例将删除 ID 为 2 的授权规则。

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>示例 2 {#example-2 .subHeading}

此示例将删除所有授权规则，并要求用户进行确认。

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

##  <a name="related-topics"></a>相关主题

-  [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
-  [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
-  [Install-PswaWebApplication](install-pswawebapplication.md)
-  [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
