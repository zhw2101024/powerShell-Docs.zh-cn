---
title: 如何替代输入处理方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364466"
---
# <a name="how-to-override-input-processing-methods"></a>如何替代输入处理方法

这些示例演示如何在 cmdlet 中覆盖输入处理方法。 这些方法用于执行以下操作：

- [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法用于执行对 Cmdlet 所处理的所有对象均有效的一次启动操作的启动操作。 Windows PowerShell 运行时只调用一次此方法。

- [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法用来处理传递给 Cmdlet 的对象。）。 Windows PowerShell 运行时为传递到 cmdlet 的每个对象调用此方法。

- 使用的是一次后处理操作的 "[系统管理](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)程序" 方法。 Windows PowerShell 运行时只调用一次此方法。

## <a name="to-override-the-beginprocessing-method"></a>重写 BeginProcessing 方法

- 声明一个受保护的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法重写。

下面的类打印示例消息。 若要使用此类，请更改 Cmdlet 属性中的动词和名词，更改类的名称以反映新的动词和名词，然后将所需的功能添加到[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法的重写。

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>重写 ProcessRecord 方法

- 声明一个受保护的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法重写。

下面的类打印示例消息。 若要使用此类，请更改 Cmdlet 属性中的动词和名词，更改类的名称以反映新的动词和名词，然后将所需的功能添加到[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的重写。

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>重写 EndProcessing 方法

- 声明一个受保护的[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法重写。

下面的类输出示例。 若要使用此类，请更改 Cmdlet 特性中的谓词和名词，更改类的名称以反映新的动词和名词，然后将所需的功能添加到重[写的](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>另请参阅

["BeginProcessing"。](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.web. EndProcessing. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

["ProcessRecord"。](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
