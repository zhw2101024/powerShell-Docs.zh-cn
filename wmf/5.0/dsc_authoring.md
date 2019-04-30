---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085637"
---
# <a name="authoring-improvements-using-powershell-ise"></a>使用 PowerShell ISE 创作改进

由于以下改进，现在在 Windows PowerShell ISE 中创作 DSC 配置的操作要容易得多：

- 在其中的某个空行上输入 **Ctrl+Space**，列出**配置**块或**节点**块中的 DSC 资源。
- 属于**枚举**类型的资源属性的自动完成。
- DSC 资源的 **DependsOn** 属性的自动完成基于配置中的其他资源实例。
- 使用“Tab”更好地完成资源属性值。

**注意：** 在可以使用“Ctrl+Space”列出选项之前，资源属性值必须为空字符串。 按 **Tab** 循环显示选项。
