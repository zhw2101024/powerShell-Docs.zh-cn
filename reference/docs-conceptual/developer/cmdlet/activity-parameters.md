---
title: 活动参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364636"
---
# <a name="activity-parameters"></a>活动参数

下表列出了活动参数的建议名称和功能。

|参数|功能|
|---|---|
|**追加**<br>数据类型： SwitchParameter|实现此参数，以便用户可以在指定参数时向资源的末尾添加内容。|
|**CaseSensitive**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时，用户可以要求区分大小写。|
|**Command**<br>数据类型：字符串|实现此参数，以便用户可以指定要运行的命令字符串。|
|**CompatibleVersion**<br>数据类型： System.object 对象|实现此参数，以便用户可以指定 cmdlet 必须兼容的语义，以便与以前的版本兼容。|
|压缩<br>数据类型： SwitchParameter|实现此参数以便在指定参数时使用数据压缩。|
|压缩<br>数据类型：关键字|实现此参数，以便用户可以指定要用于数据压缩的算法。|
|**持续**<br>数据类型： SwitchParameter|实现此参数以便在用户在指定参数后终止 cmdlet 前处理数据。 如果未指定参数，则该 cmdlet 将处理预定义数量的数据，然后终止操作。|
|**创建**<br>数据类型： SwitchParameter|实现此参数以指示如果指定了参数，则创建一个资源（如果该资源尚不存在）。|
|**删除**<br>数据类型： SwitchParameter|实现此参数可在指定参数时，在 cmdlet 完成操作时删除资源。|
|**管**<br>数据类型： SwitchParameter|实现此参数可指示在指定参数时，在 cmdlet 处理新数据之前处理未完成的工作项。 如果未指定参数，则立即处理工作项。|
|**Erase**<br>数据类型： Int32|实现此参数，以便用户可以指定在删除资源之前清除该资源的次数。|
|**ErrorLevel**<br>数据类型： Int32|实现此参数，以便用户可以指定要报告的错误级别。|
|**排除**<br>数据类型： String []|实现此参数，以便用户可以从活动中排除某些内容。 有关如何使用输入筛选器的详细信息，请参阅[输入筛选器参数](input-filter-parameters.md)。|
|**ActualRebinds**<br>数据类型：关键字|实现此参数，以便用户可以指定筛选器，以选择要在其上执行 cmdlet 操作的资源。 有关如何使用输入筛选器的详细信息，请参阅[输入筛选器参数](./input-filter-parameters.md)。|
|**参照**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时跟踪进度。|
|**团队**<br>数据类型： SwitchParameter|实现此参数可指示用户即使在指定了参数时也能执行操作。 参数不允许安全漏洞的危害。 例如，此参数允许用户覆盖只读文件。|
|**包括**<br>数据类型： String []|实现此参数，以便用户可以在活动中包含某些内容。 有关如何使用输入筛选器的详细信息，请参阅[输入筛选器参数](input-filter-parameters.md)。|
|**增量**<br>数据类型： SwitchParameter|实现此参数以指示在指定参数时以增量方式执行处理。 例如，此参数允许用户执行增量备份，只备份自上次备份后的文件。|
|**InputObject**<br>数据类型：对象|当 cmdlet 从其他 cmdlet 获取输入时，请实现此参数。 定义**InputObject**参数时，请在声明**参数**属性时始终指定**ValueFromPipeline**关键字。 有关使用输入筛选器的详细信息，请参阅[输入筛选器参数](./input-filter-parameters.md)。|
|**插入**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时，该 cmdlet 将插入一个项。|
|**Interactive**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时，该 cmdlet 可与用户交互工作。|
|间隔<br>数据类型：哈希表|实现此参数，以便用户可以指定包含这些值的关键字的哈希表。 下面的示例显示了**Interval**参数的示例值： `-interval @{ResumeScan=15; Retry=3}`。|
|**日志**<br>数据类型： SwitchParameter|实现此参数可在指定参数时审核 cmdlet 的操作。|
|**NoClobber**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时不会覆盖资源。 此参数通常适用于创建新对象的 cmdlet，以便阻止它们覆盖同名的现有对象。|
|**警告**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时通知用户活动已完成。|
|**NotifyAddress**<br>数据类型：电子邮件地址|实现此参数，以便用户可以指定在指定**通知**参数时用于发送通知的电子邮件地址。|
|**Overwrite**<br>数据类型： SwitchParameter|实现此参数，以便 cmdlet 在指定参数时覆盖任何现有数据。|
|提示<br>数据类型：字符串|实现此参数，以便用户可以指定 cmdlet 的提示。|
|**安静**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时，该 cmdlet 会在其操作中取消用户反馈。|
|**Recurse**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时，该 cmdlet 会以递归方式对资源执行操作。|
|Repair<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时，该 cmdlet 将尝试更正损坏的状态。|
|**RepairString**<br>数据类型：字符串|实现此参数，以便用户可以指定在指定了**Repair**参数时要使用的字符串。|
|**重试**<br>数据类型： Int32|实现此参数，以便用户可以指定 cmdlet 尝试操作的次数。|
|**选择**<br>数据类型：关键字数组|实现此参数，以便用户可以指定项类型的数组。|
|**流**<br>数据类型： SwitchParameter|实现此参数，以便用户可以在指定参数时通过管道流式传输多个输出对象。|
|**Strict**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时将所有错误作为终止错误处理。|
|**TempLocation**<br>数据类型：字符串|实现此参数，以便用户可以指定在 cmdlet 的操作过程中使用的临时数据的位置。|
|**Timeout**<br>数据类型： Int32|实现此参数，以便用户可以指定超时间隔（以毫秒为单位）。|
|**去**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时，该 cmdlet 将截断其操作。 如果未指定参数，则该 cmdlet 将执行其他操作。|
|**验证**<br>数据类型： SwitchParameter|实现此参数，以便该 cmdlet 将进行测试，以确定在指定参数时是否发生了某个操作。|
|**Wait**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时，该 cmdlet 将等待用户输入。
|**WaitTime**<br>数据类型： Int32|实现此参数，以便用户可以指定在指定**wait**参数时 cmdlet 等待用户输入的持续时间（以秒为单位）。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
