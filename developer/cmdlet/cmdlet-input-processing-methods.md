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
ms.openlocfilehash: dfaaa19fd3d4eb65a3fd335fb984a69874688f27
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861483"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet 输入处理方法

一个或多个输入处理方法来执行其工作本主题中所述，必须重写 Cmdlet。 这些方法允许 cmdlet 来执行预处理操作、 输入处理操作和后期处理操作。 这些方法还允许您停止 cmdlet 处理。

## <a name="pre-processing-tasks"></a>预处理任务

Cmdlet 应重写[System.Management.Automation.Cmdlet.Beginprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法中添加任何有效的该 cmdlet 将更高版本处理的所有记录的预处理操作。 当 Windows PowerShell 处理命令管道时，Windows PowerShell 调用此方法一次管道中的 cmdlet 的每个实例。 有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。

下面的代码演示一种实现[System.Management.Automation.Cmdlet.Beginprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法。

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

有关如何使用的更多详细示例[System.Management.Automation.Cmdlet.Beginprocessing%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法，请参阅[SelectStr 教程](./selectstr-tutorial.md)。 在本教程中，**选择 Str** cmdlet 使用[System.Management.Automation.Cmdlet.Beginprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)方法生成用于搜索的输入处理记录的正则表达式。

## <a name="input-processing-tasks"></a>输入处理任务

Cmdlet 可以重写[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法来处理发送到该 cmdlet 的输入。 当 Windows PowerShell 处理命令管道时，Windows PowerShell cmdlet 处理每个输入记录调用此方法。 有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。
Cmdlet 可以重写[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法来处理发送到该 cmdlet 的输入。 当 Windows PowerShell 处理命令管道时，Windows PowerShell cmdlet 处理每个输入记录调用此方法。 有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。

下面的代码演示一种实现[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法。

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

有关如何使用的更多详细示例[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法，请参阅[SelectStr 教程](./selectstr-tutorial.md)。

## <a name="post-processing-tasks"></a>后续处理任务

Cmdlet 应重写[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)方法添加有效的 cmdlet 已处理的所有记录的任何后续处理操作。 例如，你的 cmdlet 可能需要在完成后清理对象变量处理。

当 Windows PowerShell 处理命令管道时，Windows PowerShell 调用此方法一次管道中的 cmdlet 的每个实例。 但是，务必记住，Windows PowerShell 运行时将不会调用[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)方法，如果该 cmdlet 通过其输入处理正中取消或如果终止该 cmdlet 的任何部分中会发生错误。 出于此原因，应实现完整的 cmdlet，需要对象清理[System.Idisposable](/dotnet/api/System.IDisposable)模式，包括一个终结器，以便在运行时可以同时调用[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)并[System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose)末尾的处理方法。 有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。
当 Windows PowerShell 处理命令管道时，Windows PowerShell 调用此方法一次管道中的 cmdlet 的每个实例。 但是，务必记住，Windows PowerShell 运行时将不会调用[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)方法，如果该 cmdlet 通过其输入处理正中取消或如果终止该 cmdlet 的任何部分中会发生错误。 出于此原因，应实现完整的 cmdlet，需要对象清理[System.Idisposable](/dotnet/api/System.IDisposable)模式，包括一个终结器，以便在运行时可以同时调用[System.Management.Automation.Cmdlet.Endprocessing%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)并[System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose)末尾的处理方法。 有关 Windows PowerShell 如何调用命令管道的详细信息，请参阅[Cmdlet 处理生命周期](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5)。

下面的代码演示一种实现[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法。

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

有关如何使用的更多详细示例[System.Management.Automation.Cmdlet.Processrecord%2A？Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)方法，请参阅[SelectStr 教程](./selectstr-tutorial.md)。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
