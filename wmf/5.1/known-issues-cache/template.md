---
title: "已知问题或限制记录的示例模板"
contributor: 
translationtype: Human Translation
ms.sourcegitcommit: a952a27ec1695ce9951c352446194cf72d18f50a
ms.openlocfilehash: cfe0a6562743f1df81acb81e33c120cb67f9042c

---

>注意：提供建议的描述性标题和简短说明

## 示例：错误的 ExecutionPolicy 错误 ##
在运行 Windows 7 操作系统的计算机上，使用 PowerShell 模块和 DSC 资源可能导致报告有关 ExecutionPolicy 的错误。

### 解决方法

若要解决，请通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行），将 **ExecutionPolicy** 设置为 **RemoteSigned**：

```powershell
Set-ExecutionPolicy RemoteSigned
```



<!--HONumber=Jul16_HO1-->


