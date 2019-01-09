---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 包和上传到请求服务器的资源
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400395"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>包和上传到请求服务器的资源

以下各节假定您已设置请求服务器。 如果不设置拉取服务器，则可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。 本文将演示如何上传的资源，以便它们可供下载，并配置客户端会自动下载资源。 当该节点的收到的已分配的配置，通过**拉取**或**推送**(v5)，则会自动下载所需的 LCM 中指定的位置中的配置的任何资源。

## <a name="package-resource-modules"></a>包资源模块

可用于客户端要下载每个资源必须存储在".zip"文件。 下面的示例将显示使用所需的步骤[xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0)资源。

> [!NOTE]
> 如果必须使用 PowerShell 4.0 的任何客户端，需要 flaten 资源文件夹结构，并删除任何版本的文件夹。 有关详细信息，请参阅[多个资源版本](../configurations/import-dscresource.md#multiple-resource-versions)。

可以压缩使用任何实用程序、 脚本或您喜欢的方法的资源目录。 在 Windows 中，你可以*右键单击*"xPSDesiredStateConfiguration"目录，然后选择"发送到"，然后"压缩文件夹"。

![右键单击](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>命名资源存档

资源存档需要具有以下格式命名：

```
{ModuleName}_{Version}.zip
```

在上面的示例中，"xPSDesiredStateConfiguration.zip"应为已重命名"xPSDesiredStateConfiguration_8.4.4.0.zip"。

### <a name="create-checksums"></a>创建校验和

一旦已压缩并重命名的资源模块，需要创建**校验和**。  **校验和**使用，通过在客户端上的 LCM 以确定该资源已更改，以及是否需要再次下载。 您可以创建**CheckSum**与[New-dscchecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet，如下面的示例中所示。

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

将显示任何输出，但是现在应看到"xPSDesiredStateConfiguration_8.4.4.0.zip.checksum"。 您还可以运行`New-DSCCheckSum`针对使用的文件的目录`-Path`参数。 如果已存在校验和，可以强制它重新创建与`-Force`参数。

### <a name="where-to-store-resource-archives"></a>存储资源存档位置

#### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP 请求服务器上

当您设置在 HTTP 请求服务器，如中所述[设置 DSC HTTP 请求服务器](pullServer.md)，指定的目录**ModulePath**并**ConfigurationPath**密钥。 **ConfigurationPath**键指示应在其中存储的任何".mof"文件。 **ModulePath**指示应在其中存储任何 DSC 资源模块。

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>在 SMB 共享

如果指定了**ResourceRepositoryShare**，当您请求的客户端，设置存储存档和中的校验和时**SourcePath**目录从**ResourceRepositoryShare**块。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

如果仅指定**ConfigurationRepositoryShare**，当您请求的客户端，设置存储存档和中的校验和时**SourcePath**目录从**ConfigurationRepositoryShare**块。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>正在更新资源

您可以强制的节点，以更新其资源通过更改存档文件的名称中的版本号或创建新的校验和。 请求客户端将检查所需资源的较新版本，以及更新校验和，请在其 LCM 刷新时。

## <a name="see-also"></a>另请参阅

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)
