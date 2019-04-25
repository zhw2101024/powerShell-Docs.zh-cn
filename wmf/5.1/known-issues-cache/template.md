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
 ><span data-ttu-id="3b417-103">注意：提供建议的描述性标题和简短说明</span><span class="sxs-lookup"><span data-stu-id="3b417-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="3b417-104">例如：错误的 ExecutionPolicy 错误</span><span class="sxs-lookup"><span data-stu-id="3b417-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="3b417-105">在运行 Windows 7 操作系统的计算机上，使用 PowerShell 模块和 DSC 资源可能导致报告有关 ExecutionPolicy 的错误。</span><span class="sxs-lookup"><span data-stu-id="3b417-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="3b417-106">解决方法</span><span class="sxs-lookup"><span data-stu-id="3b417-106">Resolution</span></span>

<span data-ttu-id="3b417-107">若要解决，请通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行），将 **ExecutionPolicy** 设置为 **RemoteSigned**：</span><span class="sxs-lookup"><span data-stu-id="3b417-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
