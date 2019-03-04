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
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854733"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="a0986-102">如何测试可更新帮助</span><span class="sxs-lookup"><span data-stu-id="a0986-102">How to Test Updatable Help</span></span>

<span data-ttu-id="a0986-103">本主题介绍对模块进行测试可更新帮助的方法。</span><span class="sxs-lookup"><span data-stu-id="a0986-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="a0986-104">使用详细，以检测错误</span><span class="sxs-lookup"><span data-stu-id="a0986-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="a0986-105">上传后的 HelpInfo XML 文件和你的模块的 CAB 文件，通过运行测试文件[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令**Verbose**参数。</span><span class="sxs-lookup"><span data-stu-id="a0986-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="a0986-106">**Verbose**参数指示`Update-Help`报告中读取其操作的关键步骤**HelpInfoUri**密钥验证解包的 CAB 文件中的文件类型在模块清单中并将文件放在特定于语言的模块目录中。</span><span class="sxs-lookup"><span data-stu-id="a0986-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>
<span data-ttu-id="a0986-107">上传后的 HelpInfo XML 文件和你的模块的 CAB 文件，通过运行测试文件[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)命令**Verbose**参数。</span><span class="sxs-lookup"><span data-stu-id="a0986-107">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="a0986-108">**Verbose**参数指示`Update-Help`报告中读取其操作的关键步骤**HelpInfoUri**密钥验证解包的 CAB 文件中的文件类型在模块清单中并将文件放在特定于语言的模块目录中。</span><span class="sxs-lookup"><span data-stu-id="a0986-108">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="a0986-109">解析所有详细消息时，运行`Update-Help`命令**调试**参数。</span><span class="sxs-lookup"><span data-stu-id="a0986-109">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="a0986-110">此参数应检测到可更新帮助文件的任何剩余问题。</span><span class="sxs-lookup"><span data-stu-id="a0986-110">This parameter should detect any remaining problems with the Updatable Help files.</span></span>