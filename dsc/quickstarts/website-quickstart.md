---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 快速入门 - 使用 DSC 创建网站
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079110"
---
> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>快速入门 - 使用 DSC 创建网站

本练习演示创建和应用 Desired State Configuration (DSC) 配置的完整过程。
我们使用的示例可确保服务器启用了 `Web-Server`(IIS) 功能，并且该服务器的 `inetpub\wwwroot` 目录中存在一个简单“Hello World”网站的内容。

有关什么是 DSC 及其工作原理的概述，请参阅[适用于决策者的 Desired State Configuration 概述](../overview/decisionMaker.md)。

## <a name="requirements"></a>要求

要运行此示例，需要运行 Windows Server 201 2或更高版本以及 PowerShell 4.0 或更高版本的计算机。

## <a name="write-and-place-the-indexhtm-file"></a>编写并放置 index.htm 文件

首先，创建用作网站内容的 HTML 文件。

在根文件夹中，创建名为 `test` 的文件夹。

在文本编辑器中键入以下文本：

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

在之前创建的 `test` 文件夹中将它另存为 `index.htm`。

## <a name="write-the-configuration"></a>写入配置

[DSC 配置](../configurations/configurations.md)是一个特殊的 PowerShell 功能，可定义用于配置一个或多个目标计算机（节点）的方式。

在 PowerShell ISE 中键入以下内容：

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

将该文件另存为 `WebsiteTest.ps1`。

你会发现它类似于 PowerShell 函数，在函数名称之前添加了关键字 **Configuration**。

**节点**块指定要配置的目标节点，在本示例中为 `localhost`。

此配置调用两个 [resource](../resources/resources.md)、**WindowsFeature** 和 **File**。
资源负责确保目标节点处于由配置定义的状态。

## <a name="compile-the-configuration"></a>编译配置

对于要应用于节点的 DSC 配置，必须首先将其编译为 MOF 文件。
为此，你可以如运行功能一样运行配置。
在 PowerShell 控制台中，导航到保存配置的同一文件夹，并运行以下命令将配置编译为 MOF 文件：

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

此操作生成以下输出：

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

第一行使配置功能在控制台中可用。
第二行运行配置。
结果是创建了一个名为 `WebsiteTest` 的新文件夹作为当前文件夹的子文件夹。
`WebsiteTest` 文件夹包含一个名为 `localhost.mof` 的文件。
然后可将此文件应用于目标节点。

## <a name="apply-the-configuration"></a>应用配置

现在你已编译好 MOF，可以通过调用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 将配置应用于目标节点（在本例中为本地计算机）。

`Start-DscConfiguration` cmdlet 通知作为 DSC 引擎的[本地配置管理器 (LCM)](../managing-nodes/metaConfig.md)应用配置。
LCM 的工作是调用 DSC 资源以应用配置。

在 PowerShell 控制台中，导航到保存配置的同一文件夹，并运行以下命令：

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>测试配置

你可以调用 [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet 查看配置是否成功。

此外，还可以直接测试结果，在本例中可通过浏览 Web 浏览器中的 `http://localhost/` 进行测试。
你将看到在本示例的第一步中所创建的“Hello World”HTML 页面。

## <a name="next-steps"></a>后续步骤

- 在 [DSC 配置](../configurations/configurations.md)中了解有关 DSC 配置的详细信息。
- 查看哪些 DSC 资源可用，以及如何在 [DSC 资源](../resources/resources.md)中创建自定义 DSC 资源。
- 在 [PowerShell 库](https://www.powershellgallery.com/)中查找 DSC 配置和资源。
