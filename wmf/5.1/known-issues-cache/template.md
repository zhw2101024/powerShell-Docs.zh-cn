---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
title: 已知问题或限制记录的示例模板
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
>注意：提供建议的描述性标题和简短说明

## <a name="example-erroneous-executionpolicy-errors"></a>示例：错误的 ExecutionPolicy 错误 ##
在运行 Windows 7 操作系统的计算机上，使用 PowerShell 模块和 DSC 资源可能导致报告有关 ExecutionPolicy 的错误。

### <a name="resolution"></a>解决方法

若要解决，请通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行），将 **ExecutionPolicy** 设置为 **RemoteSigned**：

```powershell
Set-ExecutionPolicy RemoteSigned
```