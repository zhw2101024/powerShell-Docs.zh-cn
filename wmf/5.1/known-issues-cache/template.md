---
title: "已知问题或限制记录的示例模板"
contributor: 
ms.openlocfilehash: e3b98044902cb6665e06582c8259bd5defd6f2ca
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
>注意：提供建议的描述性标题和简短说明

## <a name="example-erroneous-executionpolicy-errors"></a>示例：错误的 ExecutionPolicy 错误 ##
在运行 Windows 7 操作系统的计算机上，使用 PowerShell 模块和 DSC 资源可能导致报告有关 ExecutionPolicy 的错误。

### <a name="resolution"></a>解决方法

若要解决，请通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行），将 **ExecutionPolicy** 设置为 **RemoteSigned**：

```powershell
Set-ExecutionPolicy RemoteSigned
```
