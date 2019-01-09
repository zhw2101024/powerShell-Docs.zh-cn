---
ms.date: 12/12/2018
keywords: dsc，powershell、 配置、 服务、 安装程序
title: 编写、编译和应用配置
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400407"
---
> 适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>编写、编译和应用配置

本练习演示创建和应用 Desired State Configuration (DSC) 配置的完整过程。
在以下示例中，您将学习如何编写和应用非常简单的配置。 配置将确保在本地计算机上存在的"HelloWorld.txt"文件。 如果您删除该文件，DSC 将重新创建它的下一步的时间，它会更新。

什么是 DSC 及其工作原理的概述，请参阅[面向开发人员 Desired State Configuration 概述](../overview/overview.md)。

## <a name="requirements"></a>要求

若要运行此示例中，将需要运行 PowerShell 4.0 或更高版本的计算机。

## <a name="write-the-configuration"></a>写入配置

DSC [配置](configurations.md)是一个特殊的 PowerShell 功能，可定义用于配置一个或多个目标计算机（节点）的方式。

在 PowerShell ISE 中或其他 PowerShell 编辑器中，键入以下命令：

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

将文件另存"HelloWorld.ps1"。

定义配置就像定义函数。 **节点**块指定要配置的目标节点，在本示例中为 `localhost`。

配置调用其中一个[资源](../resources/resources.md)，则`File`资源。 资源负责确保目标节点处于由配置定义的状态。

## <a name="compile-the-configuration"></a>编译配置

对于要应用于节点的 DSC 配置，必须首先将其编译为 MOF 文件。
运行配置，如某个函数，将编译一个".mof"文件对于定义的每个节点`Node`块。
若要运行此配置，需要对*点获取来源*到当前作用域"HelloWorld.ps1"脚本。
有关详细信息，请参阅[about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)。

*使用点获取来源*通过在你在其中存储它之后, 的路径中键入"HelloWorld.ps1"脚本`. `（点、 空间）。 然后，可以通过调用类似于函数运行您的配置。

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

此操作生成以下输出：

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>应用配置

现在你已编译好 MOF，可以通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将配置应用于目标节点（在本例中为本地计算机）。

`Start-DscConfiguration` Cmdlet 会告诉[本地配置管理器 (LCM)](../managing-nodes/metaConfig.md)，DSC，以应用配置的引擎。
LCM 的工作是调用 DSC 资源以应用配置。

使用下面的代码来执行`Start-DSCConfiguration`cmdlet。 指定的目录路径为存储在"localhost.mof"`-Path`参数。 `Start-DSCConfiguration` Cmdlet 的任何指定的目录中查找"\<computername\>.mof"文件。 `Start-DSCConfiguration` Cmdlet 尝试将会在每个".mof"文件应用于指定的文件名 （"localhost"、"server01"、"dc-02"等） 的计算机名。

> [!NOTE]
> 如果`-Wait`未指定参数，`Start-DSCConfiguration`创建后台作业来执行该操作。 指定`-Verbose`参数，可观看**Verbose**操作的输出。 `-Wait`和`-Verbose`是这两个可选参数。

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>测试配置

一次`Start-DSCConfiguration`cmdlet 完成后，你应看到一个"HelloWorld.txt"文件中指定的位置。 你可以验证包含内容[Get-content](/powershell/module/microsoft.powershell.management/get-content) cmdlet。

此外可以*测试*使用当前状态[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。

如果节点是当前符合应用的配置，输出应为"True"。

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>重新应用配置

若要查看您再次获取应用的配置，可以删除您的配置创建的文本文件。 使用`Start-DSCConfiguration`cmdlet 与`-UseExisting`参数。 `-UseExisting`参数指示`Start-DSCConfiguration`重新应用"current.mof"文件，它表示最新成功应用配置。

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>后续步骤

- 在 [DSC 配置](configurations.md)中了解有关 DSC 配置的详细信息。
- 查看哪些 DSC 资源可用，以及如何在 [DSC 资源](../resources/resources.md)中创建自定义 DSC 资源。
- 在 [PowerShell 库](https://www.powershellgallery.com/)中查找 DSC 配置和资源。
