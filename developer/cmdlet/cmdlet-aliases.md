---
title: Cmdlet 别名 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860503"
---
# <a name="cmdlet-aliases"></a>Cmdlet 别名

可以使用 cmdlet 别名来提高 cmdlet 的用户体验。 可以将别名添加到常用 cmdlet 来减少键入，快速使其能够更轻松地完成任务。 您可以在你的 cmdlet，包括内置别名或用户可以定义自己的自定义别名。

例如， [Get-command](/powershell/module/microsoft.powershell.core/get-command) cmdlet 具有内置`gcm`别名。 别名还可用于从其他语言添加命令名称，以便用户无需了解新的命令。

## <a name="alias-guidelines"></a>别名指导原则

为 cmdlet 创建内置的别名时，请遵循以下准则：

- 分配别名之前，启动 Windows PowerShell，然后运行[Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet 以查看已使用的别名。

- 包含引用的谓词的 cmdlet 名称和引用的名词的 cmdlet 名称的别名后缀别名前缀。 例如，对于别名`Import-Module`cmdlet 是"ipmo"。 所有谓词和其别名的列表，请参阅[Cmdlet 谓词](./approved-verbs-for-windows-powershell-commands.md)。

- 对于具有相同的谓词的 cmdlet，包括相同的别名前缀。 例如，其名称中包含"Get"谓词的所有 Windows PowerShell cmdlet 的别名使用"g"前缀。

- 对于具有相同的名词的 cmdlet，包括相同的别名后缀。 例如，具有"会话"名词名称中的所有 Windows PowerShell cmdlet 的别名中使用"sn 表示"后缀。

- 对于等效于其他语言中的命令的 cmdlet，使用该命令的名称。

- 一般情况下，请尽可能短的别名。 请确保该别名具有至少一个独特的字符的谓词和名词的一个独特的字符。 添加更多的字符，以使唯一别名。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
