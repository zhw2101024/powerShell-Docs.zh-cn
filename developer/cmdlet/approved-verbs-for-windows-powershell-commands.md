---
title: PowerShell 命令的批准的动词 |Microsoft Docs
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
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293344"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell 命令的已批准的谓词

PowerShell cmdlet 的名称以及其派生的 Microsoft.NET Framework 类使用的动词-名词对。
例如，`Get-Command`提供的 PowerShell cmdlet 用于检索在 PowerShell 中注册的所有命令。
名称的动词部分标识该 cmdlet 将执行的操作。
名称的名词部分标识对其执行操作的实体。

> [!NOTE]
> PowerShell 使用术语*谓词*来描述意味着某项操作，即使该单词不是标准谓词的英语语言中的字词。
> 例如，词*新建*是有效的 PowerShell 动词名称，因为它意味着操作，即使它不是英语语言中的动词，也是如此。

## <a name="verb-naming-rules"></a>谓词命名规则

以下列表提供了您选择的谓词的 cmdlet 名称时要考虑的准则：

* 当指定谓词时，我们建议使用提供的 PowerShell 的预定义的动词名称之一 （下表中包含这些预定义的谓词的别名）。
  当你使用预定义的谓词时，可确保您创建的 cmdlet、 提供的 PowerShell cmdlet 和其他人设计的 cmdlet 之间的一致性。

* 使用预定义的谓词来描述常规范围的操作，并使用参数来进一步优化该 cmdlet 的操作。

* 若要强制在 cmdlet 之间的一致性，不要使用已批准的动词的同义词。

* 使用本主题中列出每个谓词形式。
  例如，使用"Get"，但不要使用"获取"获取"。

* 使用 Pascal 大小写的谓词。
  在采用 Pascal 大小写的每个单词的首字母是采用大写形式，例如"ForEach"。

* 不允许使用以下保留的谓词或别名。
  通过 PowerShell 语言中，或通过 PowerShell 提供的特殊 case cmdlet 使用这些谓词。
  - ForEach (foreach)
  - 格式 (f)
  - 组 (gp)
  - 排序 (sr)
  - Tee （测试）
  - 其中 （以下值时）

## <a name="similar-verbs-for-different-actions"></a>不同的操作的类似谓词

以下类似谓词表示不同的操作。

### <a name="new-vs-set"></a>新 vs。Set
`New`谓词用于创建新的资源。
`Set`谓词用于修改现有资源，（可选） 创建资源，如果它不存在，例如`Set-Variable`cmdlet。

### <a name="find-vs-search"></a>找到 vs。搜索
`Find`谓词用于查找对象。
`Search`谓词用于在容器中创建对资源的引用。

### <a name="get-vs-read"></a>获取 vs。读取
`Get`谓词用于检索资源，例如文件。
`Read`谓词用于从一个源，如文件中获取信息。

### <a name="invoke-vs-start"></a>调用 vs。以管理员身份启动
`Invoke`谓词用于执行通常是一个同步操作，例如运行命令的操作。
`Start`谓词用于开始通常是一个异步操作，如启动进程的操作。

### <a name="ping-vs-test"></a>Ping vs。测试
使用`Test`谓词。

## <a name="common-verbs"></a>常见谓词

使用 PowerShell [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)枚举类定义可应用于几乎任何 cmdlet 的通用操作。
下表列出了大多数定义的谓词。

|谓词 （别名）|操作|说明|
|--------------------|------------|--------------|
|[添加](/dotnet/api/System.Management.Automation.VerbsCommon.Add)(a)|将资源添加到容器，或将项附加到另一个项。 例如， `Add-Content` cmdlet 将内容添加到一个文件。 此谓词搭配`Remove`。|对于此操作，请勿使用动词，如追加，附加，Concatenate 或插入。|
|[清除](/dotnet/api/System.Management.Automation.VerbsCommon.Clear)(cl)|从容器中删除所有资源，但不会删除该容器。 例如， `Clear-Content` cmdlet 删除文件的内容，但不会删除该文件。|对于此操作，不要使用动词，如刷新、 擦除、 发布、 取消标记、 未进行设置或 Nullify。|
|[关闭](/dotnet/api/System.Management.Automation.VerbsCommon.Close)(cs)|更改资源，使其不可访问，不可用，或不可用状态。 此谓词配对使用 `Open.`||
|[复制](/dotnet/api/System.Management.Automation.VerbsCommon.Copy)(cp)|将资源复制到另一个名称或另一个容器。 例如，`Copy-Item`用于访问存储的数据的 cmdlet 将项从数据存储区中的一个位置复制到另一个位置。|对于此操作，不要使用动词，如重复、 克隆、 复制或同步。|
|[输入](/dotnet/api/System.Management.Automation.VerbsCommon.Enter)(et)|指定允许用户将移动到资源的操作。 例如， `Enter-PSSession` cmdlet 将用户放在某个交互式会话。 此谓词搭配`Exit`。|对于此操作，不要使用谓词推送如或。|
|[退出](/dotnet/api/System.Management.Automation.VerbsCommon.Exit)(ex)|将当前的环境或上下文设置为最近使用的上下文。 例如， `Exit-PSSession` cmdlet 将用户放在用于启动交互式会话的会话中。 此谓词搭配`Enter`。|对于此操作，不要使用如 Pop 或缩小的谓词。|
|[查找](/dotnet/api/System.Management.Automation.VerbsCommon.Find)(fd)|查找为未知，隐式、 可选的或指定的容器中的对象。||
|[格式](/dotnet/api/System.Management.Automation.VerbsCommon.Format)(f)|排列指定的窗体或布局中的对象。||
|[获取](/dotnet/api/System.Management.Automation.VerbsCommon.Get)(g)|指定检索的资源的操作。 此谓词搭配`Set`。|对于此操作，不要使用动词，如读取、 打开、 猫、 类型、 Dir、 获取、 转储、 采集、 检查、 查找或搜索。|
|[隐藏](/dotnet/api/System.Management.Automation.VerbsCommon.Hide)(h)|使资源无法检测到。 例如，其名称中包含隐藏谓词的 cmdlet 可能会从用户隐藏服务。 此谓词搭配`Show`。|对于此操作，不要使用如阻止谓词。|
|[加入](/dotnet/api/System.Management.Automation.VerbsCommon.Join)(j)|将资源合并到一个资源。 例如， `Join-Path` cmdlet 结合了具有一个其子路径，以创建单一路径的路径。 此谓词搭配`Split`。|对于此操作，不要使用动词，如组合、 Unite、 连接或关联。|
|[锁](/dotnet/api/System.Management.Automation.VerbsCommon.Lock)(lk)|保护资源。 此谓词搭配`Unlock`。|对于此操作，不要使用动词，如限制或 Secure。|
|[移动](/dotnet/api/System.Management.Automation.VerbsCommon.Move)(m)|将资源从一个位置移动到另一个。 例如， `Move-Item` cmdlet 将项从数据存储区中的一个位置移动到另一个位置。|对于此操作，不要使用动词，如传输、 名称或迁移。|
|[新](/dotnet/api/System.Management.Automation.VerbsCommon.New)(n)|创建资源。 (`Set`时创建资源，包括数据，例如，还可以使用谓词`Set-Variable`cmdlet。)|对于此操作，不要使用动词，如创建、 生成、 生成、 Make 或分配。|
|[打开](/dotnet/api/System.Management.Automation.VerbsCommon.Open)(op)|要使其可访问、 可用，或可用的资源的状态更改。 此谓词搭配`Close`。||
|[优化](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize)(om)|提高资源效率。||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|从堆栈的顶部移除的项。 例如， `Pop-Location` cmdlet 将当前位置更改到最近推入堆栈的位置。||
|[推送](/dotnet/api/System.Management.Automation.VerbsCommon.Push)(pu)|将项添加到堆栈的顶部。 例如， `Push-Location` cmdlet 将当前位置到堆栈上的。||
|[重做](/dotnet/api/System.Management.Automation.VerbsCommon.Redo)(re)|将资源重置为次撤消的操作的状态。||
|[删除](/dotnet/api/System.Management.Automation.VerbsCommon.Remove)(r)|从容器中删除资源。 例如， `Remove-Variable` cmdlet 删除变量及其值。 此谓词搭配`Add`。|对于此操作，不要使用谓词此类称为明文、 剪切、 释放，放弃时，或清除。|
|[重命名](/dotnet/api/System.Management.Automation.VerbsCommon.Rename)(rn)|更改资源的名称。 例如， `Rename-Item` cmdlet，后者用于访问存储的数据更改的数据存储区中的项名称。|对于此操作，不要使用如更改谓词。|
|[重置](/dotnet/api/System.Management.Automation.VerbsCommon.Reset)(rs)|将资源设置回其原始状态。||
|[搜索](/dotnet/api/System.Management.Automation.VerbsCommon.Search)(sr)|在容器中创建对资源的引用。|对于此操作，不要使用动词，如查找或定位。|
|[选择](/dotnet/api/System.Management.Automation.VerbsCommon.Select)(sc)|在容器中查找资源。 例如， `Select-String` cmdlet 来查找在字符串和文件中的文本。|对于此操作，不要使用动词，如查找或定位。|
|[设置](/dotnet/api/System.Management.Automation.VerbsCommon.Set)(s)|替换现有的资源上的数据或创建资源，其中包含一些数据。 例如， `Set-Date` cmdlet 更改本地计算机上的系统时间。 (`New`谓词还可用于创建资源。)此谓词搭配`Get`。|对于此操作，不要使用动词，如写入、 重置、 分配或配置。|
|[显示](/dotnet/api/System.Management.Automation.VerbsCommon.Show)(sh)|使资源对用户可见。 此谓词搭配`Hide`。|对于此操作，不要使用如显示器或生成的谓词。|
|[跳过](/dotnet/api/System.Management.Automation.VerbsCommon.Skip)(sk)|绕过一个或多个资源或序列中的不同点。|对于此操作，不要使用动词如跳过或跳转。|
|[拆分](/dotnet/api/System.Management.Automation.VerbsCommon.Split)(sl)|用于分隔资源的部件。 例如， `Split-Path` cmdlet 将返回路径的不同部分。 此谓词搭配`Join`。|对于此操作，不要使用谓词单独的此类。|
|[步骤](/dotnet/api/System.Management.Automation.VerbsCommon.Step)(st)|移动到下一步的点或序列中的资源。||
|[交换机](/dotnet/api/System.Management.Automation.VerbsCommon.Switch)(sw)|指定之间交替两个资源，如更改两个位置，职责或状态之间的操作。||
|[撤消](/dotnet/api/System.Management.Automation.VerbsCommon.Undo)(un)|将资源设置为其以前的状态。||
|[解锁](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock)（英国）|释放已锁定的资源。 此谓词搭配`Lock`。|对于此操作，不要使用动词，如版本、 Unrestrict 或不安全。|
|[观看](/dotnet/api/System.Management.Automation.VerbsCommon.Watch)(wc)|持续检查或监视更改的资源。||

## <a name="communications-verbs"></a>通信谓词

使用 PowerShell [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)类来定义可应用于通信的操作。
下表列出了大多数定义的谓词。

|谓词 （别名）|操作|说明|
|--------------------|------------|--------------|
|[连接](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect)(cc)|创建源和目标之间的链接。 此谓词搭配`Disconnect`。|对于此操作，不要使用动词，如联接或 Telnet。|
|[断开连接](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect)(dc)|断开源和目标之间的链接。 此谓词搭配`Connect`。|对于此操作，不要使用动词，如中断或注销。|
|[读取](/dotnet/api/System.Management.Automation.VerbsCommunications.Read)(rd)|获取来自源的信息。 此谓词搭配`Write`。|对于此操作，不要使用动词，如采集提示，或获取。|
|[接收](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive)(rc)|接受从源发送的信息。 此谓词搭配`Send`。|对于此操作，请勿使用动词，如读取、 接受，或查看。|
|[发送](/dotnet/api/System.Management.Automation.VerbsCommunications.Send)(sd)|可以将信息传送到目标。 此谓词搭配`Receive`。|对于此操作，不要使用动词，如 Put、 广播、 邮件或传真。|
|[编写](/dotnet/api/System.Management.Automation.VerbsCommunications.Write)(wr)|将信息添加到的目标。 此谓词搭配`Read`。|对于此操作，不要使用动词，如 Put 或打印。|

## <a name="data-verbs"></a>数据谓词

使用 PowerShell [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)类定义将应用于数据处理的操作。
下表列出了大多数定义的谓词。

|谓词名称 （别名）|操作|说明|
|-------------------------|------------|--------------|
|[备份](/dotnet/api/System.Management.Automation.VerbsData.Backup)(ba)|将数据存储复制。|对于此操作，不要使用如保存 Burn、 复制或同步的谓词。|
|[检查点](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint)(ch)|创建的数据，或者其配置的当前状态的快照。|对于此操作，不要使用动词如差异|
|[比较](/dotnet/api/System.Management.Automation.VerbsData.Compare)(cr)|根据另一个资源中的数据的一个资源中的数据的计算结果。|对于此操作，不要使用动词如差异|
|[压缩](/dotnet/api/System.Management.Automation.VerbsData.Compress)(cm)|将压缩的数据的资源。 对与`Expand`。|对于此操作，不要如 Compact 使用谓词。|
|[将转换](/dotnet/api/System.Management.Automation.VerbsData.Convert)(cv)|更改的数据从一种表示形式之间或该 cmdlet 支持多个数据类型之间进行转换时该 cmdlet 支持双向转换。|对于此操作，不要使用动词，如重设大小、 更改或重新抽样。|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|将一种主要类型的输入 （cmdlet 名词指示输入） 转换为一个或多个支持的输出类型。|对于此操作，不要使用动词，如导出、 输出或扩展。|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|将转换从一个或多个类型的输入 （cmdlet 名词指示输出类型） 的主输出类型。|对于此操作，不要使用动词，如导入，输入，或在。|
|[卸除](/dotnet/api/System.Management.Automation.VerbsData.Dismount)(dm)|分离的命名的实体从一个位置。 此谓词搭配`Mount`。|对于此操作，不要使用动词，如卸载或取消链接。|
|[编辑](/dotnet/api/System.Management.Automation.VerbsData.Edit)(ed)|通过添加或删除内容修改现有数据。|对于此操作，不要使用动词，如更改、 更新或修改。|
|[展开](/dotnet/api/System.Management.Automation.VerbsData.Expand)(en)|将压缩的资源的数据还原到其原始状态。 此谓词搭配`Compress`。|对于此操作，不要使用动词，如分解或 Uncompress。|
|[导出](/dotnet/api/System.Management.Automation.VerbsData.Export)(ep)|封装的主要输入到永久性数据存储，如文件或交换格式。 此谓词搭配`Import`。|对于此操作，不要使用动词，如提取或备份。|
|[组](/dotnet/api/System.Management.Automation.VerbsData.Group)(gp)|排列，或将一个或多个资源相关联。|对于此操作，不要使用动词，如聚合，准备、 关联或关联。|
|[导入](/dotnet/api/System.Management.Automation.VerbsData.Import)(ip)|从存储在永久性数据存储 （如文件） 或交换格式的数据创建一个资源。 例如， `Import-CSV` cmdlet 将数据从逗号分隔值 (CSV) 文件导入可供其他 cmdlet 的对象。 此谓词搭配`Export`。|对于此操作，不要使用如 BulkLoad 或负载的谓词。|
|[初始化](/dotnet/api/System.Management.Automation.VerbsData.Initialize)（中）|准备一个资源供使用，并将其设置为默认状态。|对于此操作，不要使用动词，如擦除，Init、 续订、 重新生成、 重新初始化或安装程序。|
|[限制](/dotnet/api/System.Management.Automation.VerbsData.Limit)(l)|适用于资源的约束。|对于此操作，不要使用动词如配额。|
|[合并](/dotnet/api/System.Management.Automation.VerbsData.Merge)(mg)|从多个资源创建单个资源。|对于此操作，不要使用如合并或联接的谓词。|
|[装载](/dotnet/api/System.Management.Automation.VerbsData.Mount)(mt)|将命名的实体附加到的位置。 此谓词搭配`Dismount`。|对于此操作，不要使用的谓词连接。|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|将从环境的数据发送。 例如， `Out-Printer` cmdlet 将数据发送到打印机。||
|[发布](/dotnet/api/System.Management.Automation.VerbsData.Publish)(pb)|资源使其可供其他人。 此谓词搭配`Unpublish`。|对于此操作，请勿使用动词，如部署、 版本中，或安装。|
|[还原](/dotnet/api/System.Management.Automation.VerbsData.Restore)(rr)|资源设置为预定义的状态，例如通过设置状态`Checkpoint`。 例如， `Restore-Computer` cmdlet 在本地计算机上启动系统还原。|对于此操作，不要使用动词，如修复、 返回、 撤消或修补程序。|
|[保存](/dotnet/api/System.Management.Automation.VerbsData.Save)(sv)|保留数据，以避免丢失。||
|[同步](/dotnet/api/System.Management.Automation.VerbsData.Sync)(sy)|可确保两个或多个资源都处于相同状态。|对于此操作，请勿使用动词，如复制，强制，或与匹配。|
|[取消发布](/dotnet/api/System.Management.Automation.VerbsData.Unpublish)(ub)|使资源无法供其他人。 此谓词搭配`Publish`。|对于此操作，请勿使用动词，如卸载，还原、 或隐藏。|
|[更新](/dotnet/api/System.Management.Automation.VerbsData.Update)(ud)|将最新的以维护其状态、 准确性、 合规性或符合性的资源。 例如， `Update-FormatData` cmdlet 更新并将格式设置文件添加到当前的 PowerShell 控制台。|对于此操作，请勿使用动词，如刷新，续订，重新计算，或重新编制索引。|

## <a name="diagnostic-verbs"></a>诊断谓词

使用 PowerShell [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)类来定义可应用于诊断的操作。
下表列出了大多数定义的谓词。

|谓词 （别名）|操作|说明|
|--------------------|------------|--------------|
|[调试](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug)(db)|检查要诊断操作问题的资源。|对于此操作，不要使用动词如诊断。|
|[度量值](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure)（毫秒）|标识指定的操作，使用的资源或检索的资源相关的统计信息。|对于此操作，不要使用动词，如计算、 确定或分析。|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|使用`Test`谓词。||
|[修复](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair)(rp)|将资源还原到可用状态|对于此操作，不要使用动词，如修复或还原。|
|[解决](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve)(rv)|将资源的速记表示映射到的更完整的表示形式。|对于此操作，不要使用动词，如展开或确定。|
|[测试](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test)(t)|验证操作或资源的一致性。|对于此操作，不要使用动词，如诊断、 分析、 补救目的或验证。|
|[跟踪](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace)(tr)|跟踪资源的活动。|对于此操作，请勿使用动词，如跟踪，请遵循，检查或更深入地介绍。|

## <a name="lifecycle-verbs"></a>生命周期的谓词

使用 PowerShell [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类来定义可应用于资源的生命周期操作。
下表列出了大多数定义的谓词。

|谓词 （别名）|操作|说明|
|--------------------|------------|--------------|
|[批准](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve)(ap)|确认或同意对资源或进程的状态。||
|[断言](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert)（，）|确认资源的状态。|对于此操作，不要使用如 Certify 谓词。|
|[生成](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build)(bd)|创建出一些组输入文件 （通常源代码或声明性文档） 的项目 （通常是一个二进制文件或文档）|在 PowerShell v6 中添加此谓词|
|[完整](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0)(cp)|最后一个操作。||
|[确认](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm)(cn)|确认、 验证或验证资源或进程的状态。|对于此操作，不要使用动词，如确认、 同意、 Certify、 验证、 或验证。|
|[拒绝](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny)(dn)|拒绝，对象，将阻止，或 opposes 资源或进程的状态。|对于此操作，请勿使用动词，如块中，对象，拒绝或拒绝。|
|[部署](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy)(dp)|将应用程序、 网站或解决方案发送到远程目标 [s] 的方式，该解决方案的使用者可以访问它完成部署后|在 PowerShell v6 中添加此谓词|
|[禁用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable)(d)|配置为不可用或非活动状态的资源。 例如， `Disable-PSBreakpoint` cmdlet 使断点处于非活动状态。 此谓词搭配`Enable`。|对于此操作，不要使用动词，如停止或隐藏。|
|[启用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable)(e)|配置为可用或活动状态的资源。 例如， `Enable-PSBreakpoint` cmdlet 使断点处于活动状态。 此谓词搭配`Disable`。|对于此操作，不要使用动词，如启动或开始。|
|[安装](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install)（是）|将资源放在一个位置，并根据需要对其进行初始化。 此谓词搭配`Uninstall`。|此操作，请执行不使用动词如安装程序。|
|[调用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke)(i)|执行操作，如运行命令或方法。|对于此操作，不要使用动词，如运行或开始。|
|[注册](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register)(rg)|例如，数据库的存储库中创建资源条目。 此谓词搭配`Unregister`。||
|[请求](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request)(rq)|资源请求或要求的权限。||
|[重新启动](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart)(rt)|停止操作，然后再次启动它。 例如， `Restart-Service` cmdlet 停止，然后启动服务。|对于此操作，不要使用动词如回收。|
|[恢复](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume)(ru)|启动已挂起的操作。 例如， `Resume-Service` cmdlet 启动已挂起的服务。 此谓词搭配`Suspend`。||
|[启动](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start)(sa)|启动操作。 例如， `Start-Service` cmdlet 启动服务。 此谓词搭配`Stop`。|对于此操作，不要使用动词，如启动、 启动或启动。|
|[停止](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop)(sp)|终止活动。 此谓词搭配`Start`。|对于此操作，请勿使用动词，如结束时，终止，终止或取消。|
|[提交](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit)(sb)|显示用于审批的资源。|对于此操作，不要使用如 Post 谓词。|
|[挂起](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend)(ss)|暂停活动。 例如， `Suspend-Service` cmdlet 可以暂停服务。 此谓词搭配`Resume`。|对于此操作，不要使用动词如暂停。|
|[卸载](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall)（微秒）|从指定的位置中删除资源。 此谓词搭配`Install`。||
|[取消注册](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister)（你）|从存储库中删除的资源条目。 此谓词搭配`Register`。|对于此操作，不要使用如删除谓词。|
|[等待](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait)(w)|暂停操作，直到发生指定的事件。 例如， `Wait-Job` cmdlet 暂停操作，直到一个或多个后台作业已完成。|对于此操作，不要使用如睡眠或暂停的谓词。|

## <a name="security-verbs"></a>安全谓词

使用 PowerShell [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)类来定义可应用于安全的操作。
下表列出了大多数定义的谓词。

|谓词 （别名）|操作|说明|
|--------------------|------------|--------------|
|[块](/dotnet/api/System.Management.Automation.VerbsSecurity.Block)(bl)|限制对资源的访问。 此谓词搭配`Unblock`。|对于此操作，不要使用动词，如阻止、 限制或拒绝。|
|[授予](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant)(gr)|允许对资源的访问。 此谓词搭配`Revoke`。|对于此操作，不要使用动词，如允许或启用。|
|[保护](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect)(pt)|保护资源免受攻击或丢失。 此谓词搭配`Unprotect`。|对于此操作，不要使用动词，如加密、 保护或密封。|
|[撤消](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke)(rk)|指定不允许对资源的访问的操作。 此谓词搭配`Grant`。|对于此操作，不要使用动词，如删除或禁用。|
|[取消阻止](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock)(u l)|删除对资源的限制。 此谓词搭配`Block`。|对于此操作，不要使用如清除或允许的谓词。|
|[取消保护](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect)（最多）|从添加了以防止攻击或丢失的资源中删除的安全措施。 此谓词搭配`Protect`。|对于此操作，不要使用例如解密或 Unseal 谓词。|

## <a name="other-verbs"></a>其他谓词

使用 PowerShell [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)类定义无法容纳到常见、 通信、 数据、 生命周期，如某个特定谓词名称类别的规范的动词名称或安全谓词名称谓词。

|谓词 （别名）|操作|说明|
|--------------------|------------|--------------|
|[使用](/dotnet/api/System.Management.Automation.VerbsOther.Use)(u)|使用或包含要执行某些操作的资源。||

## <a name="see-also"></a>另请参阅

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet 声明](./cmdlet-class-declaration.md)

[Windows PowerShell 程序员指南](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
