---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 创建和发布项
ms.openlocfilehash: 7c2a2be6986bf65c168d7c3960366fac4ee31301
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189527"
---
# <a name="creating-and-publishing-an-item"></a>创建和发布项

在 PowerShell 库中，可以发布稳定的 PowerShell 模块、脚本和 DSC 资源，并与更广泛的 PowerShell 用户社区共享它们。

本文介绍了有关如何准备脚本或模块，并将其发布到 PowerShell 库的机制和重要步骤。
强烈建议查看[发布指南](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines)，了解如何确保发布的项将为更广泛的 PowerShell 库用户所接受。

若要将项发布到 PowerShell 库，至少必须符合以下要求：

- 拥有 PowerShell 库帐户及其关联的 API 密钥
- 确保项中包含相应的元数据
- 使用预验证工具确保项可供发布
- 使用 Publish-Module 和 Publish-Script 命令将项发布到 PowerShell 库
- 解决与项相关的问题或疑问

PowerShell 库接受 PowerShell 模块和 PowerShell 脚本。
我们所指的 PowerShell 脚本是一个文件，并不属于较大模块。

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell 库帐户和 API 密钥

请参阅[创建 PowerShell 库帐户](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account)，了解如何设置 PowerShell 库帐户。

创建帐户后，便可以获取发布项所需的 API 密钥。
使用此帐户登录后，用户名将显示在 PowerShell 库页面（而不是注册页）的顶部。
单击用户名将转到“我的帐户”页，可以在其中找到 API 密钥。

请注意，必须安全处理 API 密钥，就像处理登录名和密码一样。
使用此密钥，你或其他任何人可以更新你在 PowerShell 库中拥有的全部项。
建议定期更新此密钥，具体方法为使用“我的帐户”页上的“重置密钥”。

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>发布到 PowerShell 库的项的相应元数据

PowerShell 库向库用户提供从脚本或模块清单的元数据字段中提取的信息。
必须满足有关项清单所提供信息的一小组要求，才能创建或修改发布到 PowerShell 库中的项。
强烈建议查看[发布指南](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines)中的“项元数据”部分，了解如何向用户提供最实用的项信息。

[New-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) 和 [New-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlet 将创建清单模板，内含所有清单元素的占位符。

这两个清单都包含两个对发布非常重要的部分，即主键数据和 PrivateData 的 PSData 区域。PowerShell 模块清单中的主键数据是 PrivateData 部分之外的所有数据。
主键集合已绑定到在使用的 PowerShell 版本，并且不支持未定义的主键。
由于 PrivateData 支持添加新键，因此 PowerShell 库的专有元素位于 PSData 中。


对于要发布到 PowerShell 库的项，需要填写的最重要清单元素包括：

- 脚本或模块名称 - 这些提取自脚本的 .PS1 名称或模块的 .PSD1 名称。
- 版本 - 此为必需的主键，格式应遵循 SemVer 指南（有关详细信息，请参阅“最佳做法”）
- 作者 - 此为必需的主键，包含要与项相关联的名称（请参阅下面的“作者和所有者”）
- 说明 - 此为必需的主键，用于简要说明该项的用途和任何使用要求
- ProjectURI - 此为强烈建议填写的 PSData URI 字段，提供指向 Github 存储库或类似可以对项进行开发的位置的链接

PowerShell 库项的作者和所有者是相关概念，并非总是一致。
项所有者是拥有 PowerShell 库帐户且有权维护项的用户。 可能有多个可以更新任意项的所有者。
只能从 PowerShell 库获取所有者。如果将项从一个系统复制到另一个系统，将会丢失所有者。
由于作者是清单数据中内置的字符串，因此始终是项的一部分。
对于 Microsoft 产品项，建议如下：

- 有多个所有者，至少有一个是生产此项的团队的名称；
- 将众所周知的团队名称（如 Azure SDK 团队）或 Microsoft Corporation 设为作者。


## <a name="pre-validate-your-item"></a>预验证项

在将项发布到 PowerShell 库之前，需要对代码运行下面几个工具：

- [PowerShell 脚本分析器](https://www.powershellgallery.com/packages/PSScriptAnalyzer/)（位于 PowerShell 库中）
- 对于模块：属于 PowerShell 的 Test-ModuleManifest
- 对于脚本：PowerShell Get 随附的 Test-ScriptFileInfo

[PowerShell 脚本分析器](https://www.powershellgallery.com/packages/PSScriptAnalyzer/)是一款静态代码分析工具，可用于扫描代码，以确保其符合基本的 PowerShell 编码准则。 此工具可发现代码存在的常见和严重问题，应在开发过程中定期运行，这样有助于确保项可供发布。
PowerShell 脚本分析器会列出标识为“错误”、“警告”和“信息”的问题。
必须先修复所有错误，然后才能将项发布到 PowerShell 库中。 如果是警告，则需要查看，并且大多数都应予以解决。
每当在 PowerShell 库中发布或更新项时，都会运行 PowerShell 脚本分析器。
库运营团队会联系项所有者来修复已发现的错误。

如果 PowerShell 库基础结构无法读取项中的清单信息，将无法发布此项。
[Test-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) 可捕获导致已安装的模块不可用的常见问题。 必须先对每个模块运行此命令，然后才能将其发布到 PowerShell 库中。

同样，[Test-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) 可用于验证脚本中的元数据。必须先对与模块分开发布的每个脚本运行此命令，然后才能将其发布到 PowerShell 库中。


## <a name="publishing-items"></a>发布项

必须使用 [Publish-Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) 或 [Publish-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) 将项发布到 PowerShell 库中。
这两个命令都需要

- 将发布的项的路径。 对于模块，使用为模块指定的文件夹。 如果指定的文件夹包含同一模块的多个版本，必须指定 RequiredVersion。
- Nuget API 密钥。 这是 PowerShell 库的“我的帐户”页面上显示的 API 密钥。

由于命令行中的其他大多数选项都应位于要发布的项的清单数据中，因此无需在命令中指定这些选项。

为了避免出错，强烈建议在发布之前尝试使用 -Whatif -Verbose 运行命令。
这将节省相当多的时间，因为每次将项发布到 PowerShell 库时，都必须更新项的清单部分中的版本号。

示例命令为：'Publish-Module -Path ".\MyModule" -RequiredVersion "0.0.1" -NugetAPIKey "GUID" -Whatif -Verbose' 'Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose'

仔细检查输出，如果没有看到任何错误或警告，请重复运行命令，而不使用 -Whatif。

发布到 PowerShell 库的所有项都会进行病毒扫描，并会使用 PowerShell 脚本分析器进行分析。
此时发现的所有问题都会发回给发布者予以解决。

将项发布到 PowerShell 库后，需要检查是否有项反馈。

- 请务必监视与发布帐户相关联的电子邮件地址。
用户和 PowerShell 库运营团队会通过此帐户提供反馈，包括通过 PSSA 或防病毒扫描发现的问题。
如果电子邮件帐户无效，或将严重问题报告给此帐户后很长时间都未得到解决，可以将项视为已放弃，并将从 PowerShell 库中删除项，如我们的[使用条款](https://www.powershellgallery.com/policies/Terms)所述。
- 建议订阅已发布的每个 PowerShell 库项的评论。
这样，如果有人在 PowerShell 库中对你的项发表评论，可以收到通知。
可以根据需要进行订阅，因为这需要创建 LiveFyre 帐户。