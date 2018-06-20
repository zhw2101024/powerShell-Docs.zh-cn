---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189595"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>简述

在 IIS 中配置 Windows PowerShell® Web 访问 Web 应用程序。

## <a name="syntax"></a>语法

### <a name="default"></a>默认值
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>说明

使用 Install-PswaWebApplication cmdlet 来配置 Windows PowerShell Web 访问 Web 应用程序。 此 cmdlet 用于安装 Web 应用程序，并将其与网站相关联，可选择使用 useTestCertificate 参数创建测试 SSL 证书。 出于安全考虑，Web 管理员不应在生产环境中使用测试证书。

## <a name="parameters"></a>参数

### <a name="-usetestcertificate"></a>-UseTestCertificate

指定已创建测试证书。 如果将此参数设置为 true，则此 cmdlet 将创建一个测试证书，并配置 Windows PowerShell Web 访问 Web 应用程序，以使用 HTTPS 请求的证书。 如果将此参数设置为 false，则不会创建任何证书或绑定。 如果 Windows PowerShell Web 访问使用了另一证书，则将此值设置为 false。

|||
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | named                                |
| 默认值                        | true                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;String&gt;

指定 Web 应用程序的名称。 该名称将显示在 Windows PowerShell Web 访问 URL 的末尾。

|||
|-|-|
| 别名                              | 无                                 |
| 是否必需？                            | false                                |
| 位置在哪里？                            | 1                                    |
| 默认值                        | pswa                                 |
| 是否接受管道输入？               | false                                |
| 是否接受通配符？          | false                                |

### <a name="-websitenameltstringgt"></a>-WebSiteName&lt;String&gt;

指定要在其上安装此 Windows PowerShell Web 访问 Web 应用程序的 Web 服务器 (IIS) 网站名称。

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

此 cmdlet 不会生成任何输出。

## <a name="examples"></a>示例

### <a name="example-1"></a>示例 1

此示例将使用 WebApplicationName (pswa) 的默认值和 WebSiteName（默认网站）参数来安装 PSWA Web 应用程序。

```
Install-PswaWebApplication
```

### <a name="example-2"></a>示例 2

此示例将安装具有测试证书的 PSWA Web 应用程序，并将使用 WebApplicationName 的默认值和 WebSiteName 参数。

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>相关主题

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)