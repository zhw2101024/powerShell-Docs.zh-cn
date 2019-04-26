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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075182"
---
# <a name="activity-parameters"></a>活动参数

下表列出了建议的名称和活动参数的功能。

|参数|功能|
|---|---|
|**Append**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时用户可以将内容添加到资源的结尾。|
|**CaseSensitive**<br>数据类型：SwitchParameter|实现此参数，以便用户可以要求区分大小写，当指定的参数。|
|**命令**<br>数据类型：字符串|实现此参数，以便用户可以指定要运行的命令字符串。|
|**CompatibleVersion**<br>数据类型：System.Version 对象|实现此参数，以便用户可以指定该 cmdlet 必须与以前版本的兼容性与兼容的语义。|
|**压缩**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时使用数据压缩。|
|**压缩**<br>数据类型：关键字|实现此参数，以便用户可以指定要用于数据压缩算法。|
|**连续**<br>数据类型：SwitchParameter|实现此参数，使数据进行处理，直到用户终止该 cmdlet 时指定的参数。 如果未指定参数，该 cmdlet 处理预定义的数据量，然后终止该操作。|
|**创建**<br>数据类型：SwitchParameter|实现此参数以指示，是否尚不存在时指定的参数，创建一个资源。|
|**Delete**<br>数据类型：SwitchParameter|实现此参数，使该 cmdlet 完成其操作时指定的参数时，会删除资源。|
|**清空**<br>数据类型：SwitchParameter|实现此参数以指示该 cmdlet 时指定的参数处理新数据之前处理未完成的工作项。 如果未指定参数，则会立即处理的工作项。|
|**擦除**<br>数据类型：Int32|实现此参数，以便用户可以指定在被删除之前清除资源的次数。|
|**ErrorLevel**<br>数据类型：Int32|实现此参数，以便用户可以指定报告的错误的级别。|
|**Exclude**<br>数据类型：string[]|实现此参数，以便用户可以从活动中排除某些内容。 有关如何使用输入筛选器的详细信息，请参阅[筛选器的输入参数](input-filter-parameters.md)。|
|**筛选器**<br>数据类型：关键字|实现此参数，以便用户可以指定的筛选器，选择要对其执行 cmdlet 操作的资源。 有关如何使用输入筛选器的详细信息，请参阅[筛选器的输入参数](./input-filter-parameters.md)。|
|**Follow**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时跟踪进度。|
|**Force**<br>数据类型：SwitchParameter|实现此参数以指示用户可以执行的操作，即使指定了参数时遇到限制。 参数不允许安全受到威胁。 例如，此参数允许用户覆盖只读文件。|
|**Include**<br>数据类型：string[]|实现此参数，以便用户可以在活动中包含的内容。 有关如何使用输入筛选器的详细信息，请参阅[筛选器的输入参数](input-filter-parameters.md)。|
|**增量**<br>数据类型：SwitchParameter|实现此参数以指示处理执行以增量方式时指定的参数。 例如，此参数允许用户执行自上次备份仅备份文件的增量备份。|
|**InputObject**<br>数据类型：对象|该 cmdlet 将接受来自其他 cmdlet 的输入时，请实现此参数。 在定义**InputObject**参数，始终指定**ValueFromPipeline**关键字声明时**参数**属性。 有关使用输入筛选器的详细信息，请参阅[筛选器的输入参数](./input-filter-parameters.md)。|
|**插入**<br>数据类型：SwitchParameter|实现此参数，使该 cmdlet 将项插入时指定的参数。|
|**Interactive**<br>数据类型：SwitchParameter|实现此参数，以便 cmdlet 的工作方式以交互方式使用用户指定参数。|
|**Interval**<br>数据类型：HashTable|实现此参数，以便用户可以指定包含的值的哈希表的关键字。 下面的示例演示的示例值**间隔**参数： `-interval @{ResumeScan=15; Retry=3}`。|
|**日志**<br>数据类型：SwitchParameter|实现此参数审核该 cmdlet 的操作时指定的参数。|
|**NoClobber**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时，不会覆盖该资源。 此参数通常适用于创建新对象，以便它们可以防止覆盖现有对象具有相同名称的 cmdlet。|
|**通知**<br>数据类型：SwitchParameter|实现此参数，以便将指定参数的活动已完成通知用户。|
|**NotifyAddress**<br>数据类型：电子邮件地址|实现此参数，以便用户可以指定要用于发送通知的电子邮件地址时**通知**指定参数。|
|**Overwrite**<br>数据类型：SwitchParameter|实现此参数，使该 cmdlet 将覆盖任何现有数据时指定的参数。|
|**Prompt**<br>数据类型：字符串|实现此参数，以便用户可以指定该 cmdlet 的提示。|
|**Quiet**<br>数据类型：SwitchParameter|实现此参数，使该 cmdlet 时禁止显示用户反馈在其操作期间指定的参数。|
|**Recurse**<br>数据类型：SwitchParameter|实现此参数，以便 cmdlet 以递归方式对资源执行其操作时指定的参数。|
|**Repair**<br>数据类型：SwitchParameter|实现此参数，使该 cmdlet 会尝试更正从中断状态时指定的参数。|
|**RepairString**<br>数据类型：字符串|实现此参数，以便用户可以指定一个字符串时要使用**修复**指定参数。|
|**Retry**<br>数据类型：Int32|实现此参数，以便用户可以指定该 cmdlet 将尝试操作的次数。|
|**Select**<br>数据类型：关键字数组|实现此参数，以便用户可以指定类型的项的数组。|
|**流**<br>数据类型：SwitchParameter|实现此参数，以便用户可以将流式传输通过管道的多个输出对象时指定的参数。|
|**Strict**<br>数据类型：SwitchParameter|实现此参数，以便所有错误作为终止错误时指定的参数都处理。|
|**TempLocation**<br>数据类型：字符串|实现此参数，以便用户可以指定该 cmdlet 在操作期间使用的临时数据的位置。|
|**超时**<br>数据类型：Int32|实现此参数，以便用户可以指定的超时间隔 （以毫秒为单位）。|
|**截断**<br>数据类型：SwitchParameter|实现此参数，使该 cmdlet 将截断其操作时指定的参数。 如果未指定参数，该 cmdlet 将执行另一项操作。|
|**验证**<br>数据类型：SwitchParameter|实现此参数，使该 cmdlet 将进行测试以确定操作是否已发生时指定的参数。|
|**等待**<br>数据类型：SwitchParameter|实现此参数，使该 cmdlet 将指定参数时继续操作之前等待用户输入。
|**WaitTime**<br>数据类型：Int32|实现此参数，以便用户可以指定的持续时间 （以秒为单位） 该 cmdlet 将等待用户输入时**等待**指定参数。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
