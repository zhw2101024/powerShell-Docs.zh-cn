---
title: 如何测试可更新的帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082315"
---
# <a name="how-to-test-updatable-help"></a>如何测试可更新帮助

本主题介绍对模块进行测试可更新帮助的方法。

## <a name="using-verbose-to-detect-errors"></a>使用详细，以检测错误

上传后的 HelpInfo XML 文件和你的模块的 CAB 文件，通过运行测试文件[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令**Verbose**参数。 **Verbose**参数指示`Update-Help`报告中读取其操作的关键步骤**HelpInfoUri**密钥验证解包的 CAB 文件中的文件类型在模块清单中并将文件放在特定于语言的模块目录中。

解析所有详细消息时，运行`Update-Help`命令**调试**参数。 此参数应检测到可更新帮助文件的任何剩余问题。