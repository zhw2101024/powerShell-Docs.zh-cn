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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367146"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="2a601-102">如何测试可更新帮助</span><span class="sxs-lookup"><span data-stu-id="2a601-102">How to Test Updatable Help</span></span>

<span data-ttu-id="2a601-103">本主题介绍用于测试模块的可更新帮助的方法。</span><span class="sxs-lookup"><span data-stu-id="2a601-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="2a601-104">使用 Verbose 检测错误</span><span class="sxs-lookup"><span data-stu-id="2a601-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="2a601-105">为模块上载 HelpInfo XML 文件和 CAB 文件后，通过运行带有**Verbose**参数的[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令来测试文件。</span><span class="sxs-lookup"><span data-stu-id="2a601-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="2a601-106">**Verbose**参数指示 `Update-Help` 报告其操作中的关键步骤，从读取模块清单中的**HelpInfoUri**键到验证解压缩后的 CAB 文件中的文件类型，并将文件放在特定于语言的模块目录中。</span><span class="sxs-lookup"><span data-stu-id="2a601-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="2a601-107">解析所有详细消息后，使用**Debug**参数运行 `Update-Help` 命令。</span><span class="sxs-lookup"><span data-stu-id="2a601-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="2a601-108">此参数应检测可更新帮助文件的任何其他问题。</span><span class="sxs-lookup"><span data-stu-id="2a601-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>