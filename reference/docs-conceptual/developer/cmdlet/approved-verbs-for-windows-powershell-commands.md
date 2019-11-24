---
title: PowerShell 命令的已批准谓词 |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370026"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell 命令的批准的谓词

对于 cmdlet 的名称及其派生的 Microsoft .NET 框架类，PowerShell 使用动词-名词对。
例如，PowerShell 提供的 `Get-Command` cmdlet 用于检索在 PowerShell 中注册的所有命令。
名称的 verb 部分标识该 cmdlet 执行的操作。
名称的名词部分标识对其执行操作的实体。

> [!NOTE]
> PowerShell 使用术语 "*谓词*" 来描述一个表示操作的单词，即使该单词不是英语的标准谓词也是如此。
> 例如，"*新建*" 一词是有效的 PowerShell 谓词名称，因为它表示一个操作，即使它不是英语中的谓词。

## <a name="verb-naming-rules"></a>谓词命名规则

以下列表提供了在为 cmdlet 名称选择谓词时应考虑的准则：

* 指定谓词时，建议使用 PowerShell 提供的预定义谓词名称之一（下面的表中包含这些预定义谓词的别名）。
  使用预定义的谓词时，请确保你创建的 cmdlet、PowerShell 提供的 cmdlet 以及其他人设计的 cmdlet 之间的一致性。

* 使用预定义的谓词描述操作的一般作用域，并使用参数进一步优化 cmdlet 的操作。

* 若要在 cmdlet 之间强制一致性，请不要使用已批准谓词的同义词。

* 仅使用本主题中列出的每个谓词的形式。
  例如，使用 "Get"，但不要使用 "获取" 或 "获取"。

* 将 Pascal 大小写用于谓词。
  在 Pascal 大小写下，每个单词的首字母大写，如 "ForEach"。

* 不要使用以下保留的谓词或别名。
  这些谓词由 PowerShell 语言或 PowerShell 提供的特殊事例 cmdlet 使用。
  - ForEach （foreach）
  - Format （f）
  - 组（gp）
  - 排序（sr）
  - T （te）
  - Where （符合）

## <a name="similar-verbs-for-different-actions"></a>不同操作的类似谓词

以下类似的谓词表示不同的操作。

### <a name="new-vs-set"></a>新建与设置
`New` 谓词用于创建新的资源。
`Set` 谓词用于修改现有资源，如果该资源不存在，则可以选择创建它，如 `Set-Variable` cmdlet。

### <a name="find-vs-search"></a>查找与搜索
`Find` 谓词用于查找对象。
`Search` 谓词用于创建对容器中资源的引用。

### <a name="get-vs-read"></a>获取与读取
`Get` 谓词用于检索资源，如文件。
`Read` 谓词用于从源（如文件）获取信息。

### <a name="invoke-vs-start"></a>调用与开始
`Invoke` 谓词用于执行通常为同步操作的操作，如运行命令。
`Start` 谓词用于开始通常是异步操作的操作，如启动进程。

### <a name="ping-vs-test"></a>Ping 与测试
使用 `Test` 谓词。

## <a name="common-verbs"></a>常用谓词

PowerShell 使用[VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)枚举类定义适用于几乎任何 cmdlet 的一般操作。
下表列出了大多数定义的谓词。

|谓词（别名）|Action|说明|
|--------------------|------------|--------------|
|[添加](/dotnet/api/System.Management.Automation.VerbsCommon.Add)（a）|将资源添加到容器，或将一个项附加到另一个项。 例如，`Add-Content` cmdlet 将内容添加到文件。 此谓词与 `Remove`配对。|对于此操作，请不要使用 "追加"、"附加"、"连接" 或 "插入" 之类的谓词。|
|[清除](/dotnet/api/System.Management.Automation.VerbsCommon.Clear)（cl）|从容器中移除所有资源，但不删除容器。 例如，`Clear-Content` cmdlet 将删除文件的内容，但不会删除文件。|对于此操作，请勿使用 Flush、Erase、Release、取消标记、未设置或废除等谓词。|
|[关闭](/dotnet/api/System.Management.Automation.VerbsCommon.Close)（cs）|更改资源的状态，使其不可访问、不可用或不可用。 此谓词与 `Open.` 配对||
|[复制](/dotnet/api/System.Management.Automation.VerbsCommon.Copy)（cp）|将一个资源复制到另一个名称或另一个容器。 例如，用于访问存储数据的 `Copy-Item` cmdlet 将项从数据存储中的一个位置复制到另一个位置。|对于此操作，请不要使用 "复制"、"克隆"、"复制" 或 "同步" 等谓词。|
|[Enter](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) （et）|指定允许用户移入资源的操作。 例如，`Enter-PSSession` cmdlet 将用户放在交互式会话中。 此谓词与 `Exit`配对。|对于此操作，请不要使用谓词，如 Push 或 Into。|
|[退出](/dotnet/api/System.Management.Automation.VerbsCommon.Exit)（ex）|将当前环境或上下文设置为最近使用的上下文。 例如，`Exit-PSSession` cmdlet 将用户放在用于启动交互式会话的会话中。 此谓词与 `Enter`配对。|对于此操作，请不要使用诸如 Pop 或 Out 这样的谓词。|
|[查找](/dotnet/api/System.Management.Automation.VerbsCommon.Find)（fd）|查找容器中的对象，该对象是未知的、隐含的、可选的或指定的。||
|[Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) （f）|以指定的窗体或布局排列对象。||
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) （g）|指定用于检索资源的操作。 此谓词与 `Set`配对。|对于此操作，请勿使用 "读取"、"打开"、"猫"、"目录"、"获取"、"转储"、"获取"、"检查"、"查找" 或 "搜索" 等|
|[隐藏](/dotnet/api/System.Management.Automation.VerbsCommon.Hide)（h）|使资源无法检测。 例如，其名称包括隐藏谓词的 cmdlet 可能会隐藏用户的服务。 此谓词与 `Show`配对。|对于此操作，请不要使用谓词，如 Block。|
|[联接](/dotnet/api/System.Management.Automation.VerbsCommon.Join)（j）|将资源合并为一个资源。 例如，`Join-Path` cmdlet 将路径与它的一个子路径组合在一起，以创建单个路径。 此谓词与 `Split`配对。|对于此操作，请不要使用 "组合"、"合并"、"连接" 或 "关联" 这样的谓词。|
|[锁定](/dotnet/api/System.Management.Automation.VerbsCommon.Lock)（lk）|保护资源。 此谓词与 `Unlock`配对。|对于此操作，请不要使用谓词，例如 "限制" 或 "安全"。|
|[移动](/dotnet/api/System.Management.Automation.VerbsCommon.Move)（m）|将资源从一个位置移动到另一个位置。 例如，`Move-Item` cmdlet 将项从数据存储区中的一个位置移动到另一个位置。|对于此操作，请不要使用 "传输"、"名称" 或 "迁移" 之类的动词。|
|[新建](/dotnet/api/System.Management.Automation.VerbsCommon.New)（n）|创建资源。 （创建包含数据的资源时，也可使用 `Set` 谓词，如 `Set-Variable` cmdlet。）|对于此操作，请不要使用谓词，如 Create、Build、Build、Make 或 Allocate。|
|[打开](/dotnet/api/System.Management.Automation.VerbsCommon.Open)（操作）|更改资源的状态，使其可以访问、可用或使用。 此谓词与 `Close`配对。||
|[优化](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize)（om）|提高资源的有效性。||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) （pop）|从堆栈顶部移除一个项。 例如，`Pop-Location` cmdlet 将当前位置更改为最近推入到堆栈中的位置。||
|[推送](/dotnet/api/System.Management.Automation.VerbsCommon.Push)（pu）|向堆栈顶部添加一个项。 例如，`Push-Location` cmdlet 将当前位置推送到堆栈上。||
|[重做](/dotnet/api/System.Management.Automation.VerbsCommon.Redo)（重新）|将资源重置为已撤消的状态。||
|[删除](/dotnet/api/System.Management.Automation.VerbsCommon.Remove)（r）|从容器中删除资源。 例如，`Remove-Variable` cmdlet 删除变量及其值。 此谓词与 `Add`配对。|对于此操作，请不要使用诸如清除、剪切、释放、丢弃或擦除之类的谓词。|
|[重命名](/dotnet/api/System.Management.Automation.VerbsCommon.Rename)（rn）|更改资源的名称。 例如，用于访问存储的数据的 `Rename-Item` cmdlet 将更改数据存储中项的名称。|对于此操作，请不要使用谓词，如 Change。|
|[Reset](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) （rs）|将资源设置回其原始状态。||
|[搜索](/dotnet/api/System.Management.Automation.VerbsCommon.Search)（sr）|创建对容器中资源的引用。|对于此操作，请不要使用谓词，例如 "查找" 或 "定位"。|
|[选择](/dotnet/api/System.Management.Automation.VerbsCommon.Select)（sc）|在容器中查找资源。 例如，`Select-String` cmdlet 将查找字符串和文件中的文本。|对于此操作，请不要使用谓词，例如 "查找" 或 "定位"。|
|[集](/dotnet/api/System.Management.Automation.VerbsCommon.Set)|替换现有资源上的数据或创建包含某些数据的资源。 例如，`Set-Date` cmdlet 将更改本地计算机上的系统时间。 （`New` 谓词还可用于创建资源。）此谓词与 `Get`配对。|对于此操作，请不要使用诸如写入、重置、分配或配置之类的动词。|
|[Show](/dotnet/api/System.Management.Automation.VerbsCommon.Show) （sh）|使资源对用户可见。 此谓词与 `Hide`配对。|对于此操作，请不要使用谓词（如显示或生成）。|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) （sk）|绕过序列中的一个或多个资源或点。|对于此操作，请不要使用动词，如绕过或跳转。|
|[拆分](/dotnet/api/System.Management.Automation.VerbsCommon.Split)（sl）|分隔资源的各个部分。 例如，`Split-Path` cmdlet 返回路径的不同部分。 此谓词与 `Join`配对。|对于此操作，请不要使用单独的谓词。|
|[步骤](/dotnet/api/System.Management.Automation.VerbsCommon.Step)（st）|移动到序列中的下一个点或资源。||
|[交换机](/dotnet/api/System.Management.Automation.VerbsCommon.Switch)（软件）|指定在两个资源之间交替的操作，例如在两个位置、职责或状态之间进行更改。||
|[撤消](/dotnet/api/System.Management.Automation.VerbsCommon.Undo)（取消）|将资源设置为其以前的状态。||
|[解锁](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock)（英国）|释放已锁定的资源。 此谓词与 `Lock`配对。|对于此操作，请不要使用 "发布"、"Unrestrict" 或 "不安全" 这样的谓词。|
|[监视](/dotnet/api/System.Management.Automation.VerbsCommon.Watch)（wc.exe）|持续检查或监视资源的更改。||

## <a name="communications-verbs"></a>通信谓词

PowerShell 使用[VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)类定义适用于通信的操作。
下表列出了大多数定义的谓词。

|谓词（别名）|Action|说明|
|--------------------|------------|--------------|
|[连接](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect)（cc）|创建源和目标之间的链接。 此谓词与 `Disconnect`配对。|对于此操作，请不要使用 Join 或 Telnet 等谓词。|
|[断开连接](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect)（dc）|断开源和目标之间的链接。 此谓词与 `Connect`配对。|对于此操作，请不要使用动词，如中断或注销。|
|[读取](/dotnet/api/System.Management.Automation.VerbsCommunications.Read)（rd）|从源获取信息。 此谓词与 `Write`配对。|对于此操作，请不要使用 "获取"、"提示" 或 "获取" 这样的谓词。|
|[接收](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive)（rc）|接受从源发送的信息。 此谓词与 `Send`配对。|对于此操作，请不要使用 "读取"、"接受" 或 "查看" 之类的动词。|
|[发送](/dotnet/api/System.Management.Automation.VerbsCommunications.Send)（sd）|将信息传递给目标。 此谓词与 `Receive`配对。|对于此操作，请不要使用 Put、广播、邮件或传真等谓词。|
|[写入](/dotnet/api/System.Management.Automation.VerbsCommunications.Write)（wr）|向目标添加信息。 此谓词与 `Read`配对。|对于此操作，请不要使用 Put 或 Print 等谓词。|

## <a name="data-verbs"></a>数据谓词

PowerShell 使用[VerbsData](/dotnet/api/System.Management.Automation.VerbsData)类定义适用于数据处理的操作。
下表列出了大多数定义的谓词。

|谓词名称（别名）|Action|说明|
|-------------------------|------------|--------------|
|[备份](/dotnet/api/System.Management.Automation.VerbsData.Backup)（ba）|通过复制数据来存储数据。|对于此操作，请不要使用 "保存"、"刻录"、"复制" 或 "同步" 等谓词。|
|[检查点](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint)（ch）|创建数据或其配置的当前状态的快照。|对于此操作，请不要使用诸如 Diff 这样的谓词。|
|[比较](/dotnet/api/System.Management.Automation.VerbsData.Compare)（cr）|根据另一资源中的数据对数据进行评估。|对于此操作，请不要使用诸如 Diff 这样的谓词。|
|[压缩](/dotnet/api/System.Management.Automation.VerbsData.Compress)（cm）|压缩资源的数据。 与 `Expand`配对。|对于此操作，请不要使用类似于 Compact 的动词。|
|[转换](/dotnet/api/System.Management.Automation.VerbsData.Convert)（cv）|当 cmdlet 支持双向转换时，或者当 cmdlet 支持多个数据类型之间的转换时，将数据从一种表示形式更改为另一种表示形式。|对于此操作，请不要使用诸如更改、重设大小或重新采样之类的谓词。|
|[Convertfrom-csv](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) （cf）|将输入的一个主要类型（cmdlet 名词指示输入）转换为一个或多个受支持的输出类型。|对于此操作，请不要使用动词，如 Export、Output 或 Out。|
|[Convertto-html](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) （ct）|从一种或多种类型的输入转换为主输出类型（cmdlet 名词指示输出类型）。|对于此操作，请不要使用诸如导入、输入或中的谓词。|
|[卸载](/dotnet/api/System.Management.Automation.VerbsData.Dismount)（dm）|从位置分离命名实体。 此谓词与 `Mount`配对。|对于此操作，请不要使用动词，如卸载或取消链接。|
|[编辑](/dotnet/api/System.Management.Automation.VerbsData.Edit)（ed）|通过添加或删除内容来修改现有数据。|对于此操作，请不要使用 "更改"、"更新" 或 "修改" 这样的谓词。|
|[展开](/dotnet/api/System.Management.Automation.VerbsData.Expand)（en）|将已压缩的资源的数据还原到其原始状态。 此谓词与 `Compress`配对。|对于此操作，请不要使用谓词，如分解或解压缩。|
|[导出](/dotnet/api/System.Management.Automation.VerbsData.Export)（ep）|将主输入封装到持久数据存储区中，如文件或交换格式。 此谓词与 `Import`配对。|对于此操作，请不要使用 "提取" 或 "备份" 等谓词。|
|[组](/dotnet/api/System.Management.Automation.VerbsData.Group)（gp）|排列或关联一个或多个资源。|对于此操作，请不要使用聚合、排列、关联或关联等谓词。|
|[导入](/dotnet/api/System.Management.Automation.VerbsData.Import)（ip）|从存储在持久数据存储区（如文件）或交换格式中的数据创建资源。 例如，`Import-CSV` cmdlet 会将逗号分隔值（CSV）文件中的数据导入到可供其他 cmdlet 使用的对象。 此谓词与 `Export`配对。|对于此操作，请不要使用动词，如 BulkLoad 或 Load。|
|[Initialize](/dotnet/api/System.Management.Automation.VerbsData.Initialize) （在中）|准备要使用的资源，并将其设置为默认状态。|对于此操作，请不要使用诸如清除、初始化、续订、重新生成、重新初始化或安装之类的动词。|
|[限制](/dotnet/api/System.Management.Automation.VerbsData.Limit)（l）|将约束应用于资源。|对于此操作，请不要使用诸如配额之类的谓词。|
|[合并](/dotnet/api/System.Management.Automation.VerbsData.Merge)（mg）|从多个资源创建单个资源。|对于此操作，请不要使用 "组合" 或 "联接" 这样的谓词。|
|[装载](/dotnet/api/System.Management.Automation.VerbsData.Mount)（mt）|将命名实体附加到位置。 此谓词与 `Dismount`配对。|对于此操作，请不要使用 "连接" 谓词。|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) （o）|从环境中发送数据。 例如，`Out-Printer` cmdlet 将数据发送到打印机。||
|[发布](/dotnet/api/System.Management.Automation.VerbsData.Publish)（pb）|向其他人提供资源。 此谓词与 `Unpublish`配对。|对于此操作，请不要使用 "部署"、"发布" 或 "安装" 这样的谓词。|
|[还原](/dotnet/api/System.Management.Automation.VerbsData.Restore)（rr）|将资源设置为预定义状态，如 `Checkpoint`设置的状态。 例如，`Restore-Computer` cmdlet 将在本地计算机上启动系统还原。|对于此操作，请不要使用 "修复"、"返回"、"撤消" 或 "修复" 这样的谓词。|
|[保存](/dotnet/api/System.Management.Automation.VerbsData.Save)（sv）|保留数据以避免丢失。||
|[同步](/dotnet/api/System.Management.Automation.VerbsData.Sync)（sy）|确保两个或更多个资源处于相同的状态。|对于此操作，请不要使用动词，如复制、强制或匹配。|
|[取消发布](/dotnet/api/System.Management.Automation.VerbsData.Unpublish)（ub）|使资源对其他人不可用。 此谓词与 `Publish`配对。|对于此操作，请不要使用动词，如 "卸载"、"还原" 或 "隐藏"。|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update) （ud）|为维护其状态、准确性、一致性或合规性提供最新的资源。 例如，`Update-FormatData` cmdlet 将更新格式设置文件并将其添加到当前 PowerShell 控制台。|对于此操作，请不要使用 "刷新"、"续订"、"重新计算" 或 "重新建立索引" 等动词。|

## <a name="diagnostic-verbs"></a>诊断谓词

PowerShell 使用[VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)类定义适用于诊断的操作。
下表列出了大多数定义的谓词。

|谓词（别名）|Action|说明|
|--------------------|------------|--------------|
|[调试](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug)（db）|检查资源以诊断操作问题。|对于此操作，请不要使用谓词，如诊断。|
|[度量值](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure)（毫秒）|标识指定操作使用的资源，或检索有关资源的统计信息。|对于此操作，请不要使用 "计算"、"确定" 或 "分析" 这样的谓词。|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) （pi）|使用 `Test` 谓词。||
|[修复](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair)（rp）|将资源还原为可用条件|对于此操作，请不要使用谓词，如 "修复" 或 "还原"。|
|[解析](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve)（rv）|将资源的简略表示形式映射到更完整的表示形式。|对于此操作，请不要使用诸如展开或确定之类的谓词。|
|[测试](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test)（t）|验证资源的操作或一致性。|对于此操作，请勿使用诊断、分析、抢救或验证等动词。|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) （tr）|跟踪资源的活动。|对于此操作，请不要使用跟踪、跟随、检查或处理等谓词。|

## <a name="lifecycle-verbs"></a>生命周期谓词

PowerShell 使用[VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类来定义适用于资源生命周期的操作。
下表列出了大多数定义的谓词。

|谓词（别名）|Action|说明|
|--------------------|------------|--------------|
|[批准](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve)（ap）|确认或同意资源或进程的状态。||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) （as）|确认资源的状态。|对于此操作，请不要使用动词，如认证。|
|[生成](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build)（bd）|从一组输入文件（通常是源代码或声明性文档）中创建一个项目（通常是二进制或文档）|已在 PowerShell v6 中添加此谓词|
|[完成](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0)（cp）|结束操作。||
|[确认](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm)（cn）|确认、验证或验证资源或进程的状态。|对于此操作，请不要使用如 "确认"、"同意"、"验证"、"验证" 或 "验证" 之类的动词。|
|[拒绝](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny)（dn）|拒绝、对象、阻止或 opposes 资源或进程的状态。|对于此操作，请不要使用谓词，如 Block、Object、拒绝或拒绝。|
|[部署](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy)（dp）|以这样一种方式将应用程序、网站或解决方案发送到远程目标 [s]，以使该解决方案的使用者能够在部署完成后对其进行访问|已在 PowerShell v6 中添加此谓词|
|[禁用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable)（d）|将资源配置为不可用或非活动状态。 例如，`Disable-PSBreakpoint` cmdlet 会使断点处于非活动状态。 此谓词与 `Enable`配对。|对于此操作，请不要使用谓词，如 "停止" 或 "隐藏"。|
|[启用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable)（e）|将资源配置为可用状态或活动状态。 例如，`Enable-PSBreakpoint` cmdlet 将断点激活。 此谓词与 `Disable`配对。|对于此操作，请不要使用 "启动" 或 "开始" 这样的谓词。|
|[安装](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install)（is）|将资源置于某个位置，并根据需要对其进行初始化。 此谓词与 `Uninstall`配对。|对于此操作，请不要使用谓词，如设置。|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) （i）|执行操作，如运行命令或方法。|对于此操作，请不要使用谓词，如 "运行" 或 "启动"。|
|[注册](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register)（rg）|为存储库（如数据库）中的资源创建一个条目。 此谓词与 `Unregister`配对。||
|[请求](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request)（sysrq）|请求提供资源或请求权限。||
|[重新启动](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart)（rt）|停止操作，然后重新启动。 例如，`Restart-Service` cmdlet 将停止，然后启动服务。|对于此操作，请不要使用谓词，如回收。|
|[恢复](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume)（ru）|启动已挂起的操作。 例如，`Resume-Service` cmdlet 将启动已挂起的服务。 此谓词与 `Suspend`配对。||
|[启动](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start)（sa）|启动操作。 例如，`Start-Service` cmdlet 将启动一个服务。 此谓词与 `Stop`配对。|对于此操作，请不要使用 "启动"、"启动" 或 "启动" 这样的谓词。|
|[停止](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop)（sp）|停止活动。 此谓词与 `Start`配对。|对于此操作，请不要使用 "结束"、"终止"、"终止" 或 "取消" 这样的谓词。|
|[提交](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit)（sb）|显示要审批的资源。|对于此操作，请不要使用 Post 之类的动词。|
|[挂起](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend)（ss）|暂停活动。 例如，`Suspend-Service` cmdlet 将暂停服务。 此谓词与 `Resume`配对。|对于此操作，请不要使用谓词，例如 Pause。|
|[卸载](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall)（us）|从指示的位置删除资源。 此谓词与 `Install`配对。||
|[取消注册](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister)（您的）|从存储库中删除资源的条目。 此谓词与 `Register`配对。|对于此操作，请不要使用动词，如 Remove。|
|[等待](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait)（w）|暂停操作，直到发生指定的事件。 例如，`Wait-Job` cmdlet 将暂停操作，直到一个或多个后台作业完成。|对于此操作，请不要使用动作，如睡眠或暂停。|

## <a name="security-verbs"></a>安全谓词

PowerShell 使用[VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)类定义适用于安全的操作。
下表列出了大多数定义的谓词。

|谓词（别名）|Action|说明|
|--------------------|------------|--------------|
|[块](/dotnet/api/System.Management.Automation.VerbsSecurity.Block)（bl）|限制对资源的访问。 此谓词与 `Unblock`配对。|对于此操作，请不要使用谓词，如 "阻止"、"限制" 或 "拒绝"。|
|[授权](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant)（gr）|允许访问资源。 此谓词与 `Revoke`配对。|对于此操作，请不要使用 "允许" 或 "启用" 等谓词。|
|[保护](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect)（pt）|保护资源免受攻击或丢失。 此谓词与 `Unprotect`配对。|对于此操作，请不要使用 "加密"、"安全" 或 "密封" 等动词。|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) （rk）|指定不允许访问资源的操作。 此谓词与 `Grant`配对。|对于此操作，请不要使用动词，如删除或禁用。|
|[取消阻止](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock)（ul）|删除对资源的限制。 此谓词与 `Block`配对。|对于此操作，请不要使用动词，如 Clear 或 Allow。|
|[取消保护](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect)（向上）|删除已添加的资源的安全措施，防止其受到攻击或丢失。 此谓词与 `Protect`配对。|对于此操作，请不要使用动词，如解密或解封。|

## <a name="other-verbs"></a>其他谓词

PowerShell 使用[VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)类来定义不适合特定谓词名称类别的规范谓词名称，如公用、通信、数据、生命周期或安全谓词名称谓词。

|谓词（别名）|Action|说明|
|--------------------|------------|--------------|
|[使用](/dotnet/api/System.Management.Automation.VerbsOther.Use)（u）|使用或包含资源来执行某些操作。||

## <a name="see-also"></a>另请参阅

[System.web. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.web. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.web. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.web. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.web. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.web. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.web. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet 声明](./cmdlet-class-declaration.md)

[Windows PowerShell 程序员指南](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
