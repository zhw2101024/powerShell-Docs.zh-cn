---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.topic: conceptual
title: 已知问题或限制记录的示例模板
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055541"
---
 >注意：提供建议的描述性标题和简短说明

## <a name="example-erroneous-executionpolicy-errors"></a>例如：错误的 ExecutionPolicy 错误
在运行 Windows 7 操作系统的计算机上，使用 PowerShell 模块和 DSC 资源可能导致报告有关 ExecutionPolicy 的错误。

### <a name="resolution"></a>解决方法

若要解决，请通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行），将 **ExecutionPolicy** 设置为 **RemoteSigned**：

```powershell
Set-ExecutionPolicy RemoteSigned
```
