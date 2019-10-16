---
title: 如何测试可更新帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367146"
---
# <a name="how-to-test-updatable-help"></a>如何测试可更新帮助

本主题介绍用于测试模块的可更新帮助的方法。

## <a name="using-verbose-to-detect-errors"></a>使用 Verbose 检测错误

为模块上载 HelpInfo XML 文件和 CAB 文件后，通过运行带有**Verbose**参数的[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令来测试文件。 **Verbose**参数定向 `Update-Help`，以报告其操作中的关键步骤，从读取模块清单中的**HelpInfoUri**键到验证解压缩后的 CAB 文件中的文件类型，并将文件置于特定于语言的模块目录。

解析所有详细消息后，使用**Debug**参数运行 `Update-Help` 命令。 此参数应检测可更新帮助文件的任何其他问题。