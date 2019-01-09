---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 发布到拉取服务器使用配置 Id (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400420"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>发布到拉取服务器使用配置 Id (v4/v5)

以下各节假定您已设置请求服务器。 如果不设置拉取服务器，则可以使用以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点可以配置为下载的配置，资源，并甚至报告其状态。 本文将演示如何上传的资源，以便它们可供下载，并配置客户端会自动下载资源。 当该节点的收到的已分配的配置，通过**拉取**或**推送**(v5)，则会自动下载所需的 LCM 中指定的位置中的配置的任何资源。

## <a name="compile-configurations"></a>编译配置

存储的第一步[配置](../configurations/configurations.md)拉取服务器上，将其编译为".mof"文件。 若要进行配置，泛型类型，并适用于多个客户端，使用`localhost`节点块中。 下面的示例演示使用的配置 shell`localhost`而不是特定的客户端名称。

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

编译通用配置后，您应该有"localhost.mof"文件。

## <a name="renaming-the-mof-file"></a>重命名的 MOF 文件

可以存储在通过拉服务器配置".mof"文件**ConfigurationName**或**ConfigurationID**。 根据您计划如何设置请求客户端，您可以选择下面正确重命名已编译".mof"文件的一个章节。

### <a name="configuration-ids-guid"></a>配置 Id (GUID)

将需要重命名为"localhost.mof"文件"<GUID>.mof"文件。 您可以创建一个随机**Guid**使用的示例，或通过使用[新建 Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet。

```powershell
[System.Guid]::NewGuid()
```

示例输出

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

然后可以重命名你使用任何可接受的方法的".mof"文件。 以下示例中，使用[重命名项](/powershell/module/microsoft.powershell.management/rename-item)cmdlet。

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

有关使用详细信息**Guid**在环境中，请参阅[规划 Guid](/powershell/dsc/secureserver#guids)。

### <a name="configuration-names"></a>配置名称

将需要重命名为"localhost.mof"文件"<Configuration Name>.mof"文件。 在以下示例中，使用上一节中的配置名称。 然后可以重命名你使用任何可接受的方法的".mof"文件。 以下示例中，使用[重命名项](/powershell/module/microsoft.powershell.management/rename-item)cmdlet。

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>创建校验和

每个".mof"文件存储在请求服务器或 SMB 共享上需要有一个关联".checksum"文件。 此文件可让客户端知道当关联".mof"文件已更改，应重新下载。

您可以创建**CheckSum**与[New-dscchecksum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet。 您还可以运行`New-DSCCheckSum`针对使用的文件的目录`-Path`参数。 如果已存在校验和，可以强制它重新创建与`-Force`参数。 以下示例指定一个包含上一节中的".mof"文件的目录，并使用`-Force`参数。

```powershell
New-DscChecksum -Path '.\' -Force
```

将显示任何输出，但是现在应看到"<GUID or Configuration Name>。 mof.checksum"文件。

## <a name="where-to-store-mof-files-and-checksums"></a>MOF 文件和校验和的存储位置

### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP 请求服务器上

当您设置在 HTTP 请求服务器，如中所述[设置 DSC HTTP 请求服务器](pullServer.md)，指定的目录**ModulePath**并**ConfigurationPath**密钥。 **ConfigurationPath**键指示应在其中存储的任何".mof"文件。 **ConfigurationPath**指示应在其中存储的任何".mof"文件和".checksum"文件。

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>在 SMB 共享

如果您设置了请求的客户端使用 SMB 共享，指定**ConfigurationRepositoryShare**。 所有".mof"文件和".checksum"文件然后应存储在**SourcePath**目录从**ConfigurationRepositoryShare**块。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>后续步骤

接下来，想要配置请求客户端请求指定的配置。 有关详细信息，请参阅以下指南：

- [设置请求客户端使用配置 Id (v4)](pullClientConfigId4.md)
- [设置请求客户端使用配置 Id (v5)](pullClientConfigId.md)
- [设置请求客户端使用配置名称 (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>另请参阅

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)
- [包和上传到请求服务器的资源](package-upload-resources.md)
