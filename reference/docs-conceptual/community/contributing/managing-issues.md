---
title: 如何管理问题
description: 本文介绍 PowerShell-Docs 团队如何管理拉取请求。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: cd7aba83d42a6a2eba1ce73910fdd34096342c21
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060272"
---
# <a name="how-we-manage-issues"></a>如何管理问题

本文记录了如何管理 PowerShell-Docs 存储库中的问题。 本文旨在为 PowerShell-Docs 团队成员提供帮助。 在此处发布本文，以便为公共参与者提供流程透明性。

## <a name="sources-of-issues"></a>问题源

- 社区参与者
- 内部参与者
- 来自社交媒体渠道的注释转录
- 通过 Docs 反馈窗体提供的反馈

## <a name="response-time-targets"></a>响应时间目标

- 已会审 - 5 个工作日
- 修复或更改 - 无具体目标 - 仅尽最大努力

### <a name="labeling--milestones"></a>标记和里程碑

#### <a name="label-types"></a>标签类型

|前缀  | 说明                                                         |
|------- | --------------------------------------------------------------------|
|区域    | 用于指示问题正在讨论哪个部分的 PowerShell 或文档。<br>有助于功能所有者查找其功能的问题。|
|Pri     | 用于指示问题的优先级。 值范围是 0-4。        |
|问题   | 用于对问题的反馈类型进行分类                     |
|审阅  | 用于需要团队进一步评审的问题              |
|状态  | 用于指示工作项的状态                        |
|等待 | 用于指示我们正在等待                   |

#### <a name="milestones"></a>里程碑

应使用相应的里程碑标记的问题和 PR。 如果问题并未针对特定版本，则不使用里程碑。 应将尚未合并到 PowerShell 代码库中的更改的 Docs PR 的问题分配给“未来”  里程碑。 合并代码更改后，将里程碑更改为相应的版本。

|    里程碑     |                    说明                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | 与 PowerShell 6.0 到 6.2.x 相关的工作项 |
| 7.0.0            | 与 PowerShell 7.0 相关的工作项               |
| 7.1.0            | 与 PowerShell 7.1 相关的工作项               |
| 未来           | 工作项 PowerShell 的未来版本          |
| PSReadline-vNext | 工作项 PSReadline 的未来版本          |

## <a name="triage-process"></a>会审过程

PowerShell Docs 团队每周都要开会讨论自上次会议以来新增的任何问题。 如果分配了标签或分配了所有者，则会将问题视为已会审。 建议 PowerShell Docs 团队成员每天审查问题，并在遇到新问题时进行会审。 然后，可以根据需要开展每周会审会议来更详细地讨论新问题。

### <a name="misplaced-product-feedback"></a>错放的产品反馈

- 输入客户注释，指明它是产品反馈，并提供指向相应反馈渠道的链接。
- 可选：将问题复制到相应的产品反馈位置，将链接添加到复制的项，并关闭问题。 请勿将问题复制到 UserVoice。

  | DocSet    | 产品反馈 URL                                         |
  | --------- | ------------------------------------------------------------ |
  | 开发人员 | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | dsc       | https://windowsserver.uservoice.com/forums/301869-powershell |
  | 库   | https://github.com/powershell/powershellgallery/issues/new   |
  | jea       | https://github.com/powershell/jea/issues/new                 |
  | reference | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | wmf       | https://windowsserver.uservoice.com/forums/301869-powershell |

### <a name="support-requests"></a>支持请求

- 如果支持问题很简单，请礼貌答复并关闭问题。
- 如果问题较为复杂，或者提交者回复了更多问题，请将这些问题重定向到论坛和支持渠道。 用于重定向到论坛的建议文本：

    > 这并不是这些问题的正确论坛。 尝试在社区支持论坛中发布你的问题。 有关社区论坛的列表，请参阅： https://docs.microsoft.com/powershell/scripting/community/community-support

### <a name="code-of-conduct-violations"></a>行为准则冲突

- 编辑问题以删除任何冒犯性内容（如有必要）。
- 输入一条注释，指示此问题是垃圾邮件，关闭问题，然后将其锁定以防止进一步注释。
- 每次出现该问题时应在每周会审中进行讨论，以确定是否需要执行进一步操作（向 GitHub 或 Microsoft 法律报告）。
