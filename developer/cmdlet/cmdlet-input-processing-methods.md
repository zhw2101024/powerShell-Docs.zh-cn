---
title: Cmdlet 输入处理方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670313"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet 输入处理方法

一个或多个输入处理方法来执行其工作本主题中所述，必须重写 Cmdlet。
这些方法允许 cmdlet 来执行预处理、 输入的处理和后处理操作。
这些方法还允许您停止 cmdlet 处理。
有关如何使用这些方法的更详细的示例，请参阅[SelectStr 教程](selectstr-tutorial.md)。

## <a name="pre-processing-operations"></a>预处理操作

Cmdlet 应重写[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中添加任何有效的该 cmdlet 将更高版本处理的所有记录的预处理操作。
当 PowerShell 处理命令管道时，PowerShell 调用此方法一次管道中的 cmdlet 的每个实例。
有关 PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](/previous-versions/ms714429(v=vs.85))。

下面的代码演示 BeginProcessing 方法的实现。

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>输入处理操作

Cmdlet 可以重写[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法来处理发送到该 cmdlet 的输入。
当 PowerShell 处理命令管道时，PowerShell cmdlet 处理每个输入记录调用此方法。
有关 PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](/previous-versions/ms714429(v=vs.85))。

下面的代码演示 ProcessRecord 方法的实现。

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>后续处理操作

Cmdlet 应重写[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法添加有效的 cmdlet 已处理的所有记录的任何后续处理操作。
例如，你的 cmdlet 可能需要在完成后清理对象变量处理。

当 PowerShell 处理命令管道时，PowerShell 调用此方法一次管道中的 cmdlet 的每个实例。
但是，务必要记住，如果该 cmdlet 将其输入处理通过正中取消或终止错误时该 cmdlet 的任何部分中，PowerShell 运行时将不调用 EndProcessing 方法。
出于此原因，应实现完整的 cmdlet，需要对象清理[System.IDisposable](/dotnet/api/System.IDisposable)模式，包括一个终结器，以便在运行时可以调用这两个 EndProcessing 和[System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose)末尾的处理方法。
有关 PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](/previous-versions/ms714429(v=vs.85))。

下面的代码演示 EndProcessing 方法的实现。

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr 教程](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
