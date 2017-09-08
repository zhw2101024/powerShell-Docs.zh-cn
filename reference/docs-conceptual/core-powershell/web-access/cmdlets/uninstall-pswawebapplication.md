---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "卸载 pswawebapplication"
ms.technology: powershell
ms.openlocfilehash: 64d546427e44d7bd284da8f682a7218afbadd0ad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
#  <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

##  <a name="synopsis"></a>简述

卸载 Windows PowerShell® Web 应用程序。

## <a name="syntax"></a>语法

###  <a name="default"></a>默认值
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>说明

Uninstall-PswaWebApplication cmdlet 将卸载 Windows PowerShell Web 应用程序，并从 IIS 删除该网站。 该 cmdlet 不会卸载 IIS 或任何其他已安装的功能，因为它们是 Windows PowerShell 运行所必需的。

## <a name="parameters"></a>参数

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

指示由 Install\_PswaWebApplication cmdlet（包含 UseTestCertificate 参数）创建的测试证书已被删除。
仅删除与 Install-PswaWebApplication 创建的 cmdlet 具有相同名称的测试证书。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | true                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;String&gt;

指定要卸载的 Web 应用程序的名称。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | 1                                    |
| 默认值                        | pswa                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;String&gt;

指定安装 Web 应用程序的网站的名称。

|||  
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | 默认网站                     |
| 是否接受管道输入？               | false                                |
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

显示如果运行 cmdlet 则会发生什么情况。
cmdlet 未运行。

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

此 cmdlet 不接受任何输入。

## <a name="outputs"></a>输出

此 cmdlet 不返回任何输出。

## <a name="examples"></a>示例

### <a name="example-1"></a>示例 1

此命令将卸载 Windows PowerShell Web 应用程序。
如果使用了默认值来安装 Windows PowerShell Web 应用程序，则可使用此 cmdlet 对其进行卸载。

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>示例 2

此命令将卸载 Windows PowerShell Web 应用程序，并删除与该应用程序相关联的测试证书。
如果使用了默认值来安装 Windows PowerShell Web 应用程序并创建了测试证书，则可使用此 cmdlet 对其进行卸载。

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>示例 3 {#example-3 .subHeading}

如果在安装过程中指定了自定义网站和应用程序，此命令将卸载 Windows PowerShell Web 应用程序。
该命令将删除名为 MySite 的网站及名为 TestApplication 的应用程序，并指定删除与该应用程序相关联的测试证书。

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

##  <a name="related-topics"></a>相关主题

-  [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
-  [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
-  [Install-PswaWebApplication](install-pswawebapplication.md)
-  [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
-  [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
