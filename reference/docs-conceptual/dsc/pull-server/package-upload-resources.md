---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 打包资源并将其上传到拉取服务器
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954374"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>打包资源并将其上传到拉取服务器

以下部分假定你已设置拉取服务器。 如果尚未设置拉取服务器，则可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。 本文将演示如何上传资源以便下载，以及如何将客户端配置为自动下载资源。 当节点通过“拉取”  或“推送”  (v5) 接收已分配的配置时，将从 LCM 中指定的位置自动下载配置所需的任何资源。

## <a name="package-resource-modules"></a>包资源模块

可供客户端下载的每个资源必须存储在“.zip”文件中。 下面的示例将显示使用 [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) 资源所需的步骤。

> [!NOTE]
> 如果有任何使用 PowerShell 4.0 的客户端，则将需要展开资源文件夹结构并删除任何版本的文件夹。 有关详细信息，请参阅[多个资源版本](../configurations/import-dscresource.md#multiple-resource-versions)。

可以使用喜欢的任何实用工具、脚本或方法压缩资源目录。 在 Windows 中，可以  右键单击“xPSDesiredStateConfiguration”目录，然后依次选择“发送到”和“压缩文件夹”。

![右键单击](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>命名资源存档

资源存档需要采用以下格式命名：

```
{ModuleName}_{Version}.zip
```

在上面的示例中，“xPSDesiredStateConfiguration.zip”应重命名为“xPSDesiredStateConfiguration_8.4.4.0.zip”。

### <a name="create-checksums"></a>创建校验和

压缩并重命名资源模块后，需要创建校验和  。  客户端上的 LCM 使用校验和  来确定该资源是否已更改，以及是否需要重新下载。 可以使用 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet 创建校验和  ，如下面的示例中所示。

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

不会显示任何输出，但现在应看到“xPSDesiredStateConfiguration_8.4.4.0.zip.checksum”。 也可以使用 `-Path` 参数对文件的目录运行 `New-DSCCheckSum`。 如果校验和已存在，则可以强制使用 `-Force` 参数重新创建校验和。

### <a name="where-to-store-resource-archives"></a>存储资源存档的位置

#### <a name="on-a-dsc-http-pull-server"></a>在 DSC HTTP 拉取服务器上

当按照[设置 DSC HTTP 拉取服务器](pullServer.md)中所述设置 HTTP 拉取服务器时，指定 ModulePath  和 ConfigurationPath  键的目录。 ConfigurationPath  键指示应存储任何“.mof”文件的位置。 ModulePath  键指示应存储任何 DSC 资源模块的位置。

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>在 SMB 共享上

如果在设置拉取客户端时指定了 ResourceRepositoryShare  ，则将存档和校验和存储在 ResourceRepositoryShare  块的 SourcePath  目录中。

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

如果在设置拉取客户端时仅指定了 ConfigurationRepositoryShare  ，则将存档和校验和存储在 ConfigurationRepositoryShare  块的 SourcePath  目录中。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>正在更新资源

可以强制节点通过更改存档名称中的版本号或创建新的校验和来更新其资源。 拉取客户端将在 LCM 刷新后检查所需资源的较新版本，以及更新的校验和。

## <a name="see-also"></a>另请参阅

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)
