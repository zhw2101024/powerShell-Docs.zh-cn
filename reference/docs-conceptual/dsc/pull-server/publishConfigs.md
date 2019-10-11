---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 使用配置 ID 发布到拉取服务器 (v4/v5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953594"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>使用配置 ID 发布到拉取服务器 (v4/v5)

以下部分假定你已设置拉取服务器。 如果尚未设置拉取服务器，可以遵循以下指南：

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)

每个目标节点都可以配置为下载配置、资源，甚至是报告其状态。 本文介绍了如何上传资源以供下载，以及如何将客户端配置为自动下载资源。 如果节点通过“拉取”  或“推送”  (v5) 收到分配的配置，便会从本地配置管理器 (LCM) 中指定的位置自动下载配置所需的任何资源。

## <a name="compile-configurations"></a>编译配置

将[配置](../configurations/configurations.md)存储在拉取服务器上的第一步是，将配置编译为 `.mof` 文件。 若要使配置通用并适用于多个客户端，请使用节点块中的 `localhost`。 下面的示例显示使用 `localhost`（而不是特定客户端名称）的配置 Shell。

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

编译通用配置后，应该就会有 `localhost.mof` 文件。

## <a name="renaming-the-mof-file"></a>重命名 MOF 文件

可以按 ConfigurationName  或 ConfigurationID  将配置 `.mof` 文件存储在拉取服务器上。 可以选择下面的部分来正确重命名已编译的 `.mof` 文件，具体视你计划如何设置拉取客户端。

### <a name="configuration-ids-guid"></a>配置 ID (GUID)

需要将 `localhost.mof` 文件重命名为 `<GUID>.mof` 文件。 可以使用以下示例，或使用 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet 创建随机 Guid  。

```powershell
[System.Guid]::NewGuid()
```

示例输出

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

然后，可以使用任何可接受的方法重命名 `.mof` 文件。 以下示例使用 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet。

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

有关在环境中使用 Guid  的详细信息，请参阅[规划 Guid](/powershell/dsc/secureserver#guids)。

### <a name="configuration-names"></a>配置名称

需要将 `localhost.mof` 文件重命名为 `<Configuration Name>.mof` 文件。 在以下示例中，将使用上一节中的配置名称。 然后，可以使用任何可接受的方法重命名 `.mof` 文件。 以下示例使用 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet。

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>创建校验和

拉取服务器上存储的每个 `.mof` 文件或 SMB 共享都需要有关联的 `.checksum` 文件。
借助此文件，客户端可以了解关联的 `.mof` 文件何时发生了更改，以及应何时重新下载它。

可以使用 [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet 创建校验和  。 也可以使用 `-Path` 参数对文件的目录运行 `New-DSCCheckSum`。
如果校验和已存在，则可以强制使用 `-Force` 参数重新创建校验和。 下面的示例指定了包含上一部分中的 `.mof` 文件的目录，并使用 `-Force` 参数。

```powershell
New-DscChecksum -Path '.\' -Force
```

你将不会看到任何输出，但现在应看到 `<GUID or Configuration Name>.mof.checksum` 文件。

## <a name="where-to-store-mof-files-and-checksums"></a>MOF 文件和校验和的存储位置

### <a name="on-a-dsc-http-pull-server"></a>在 DSC HTTP 拉取服务器上

当按照[设置 DSC HTTP 拉取服务器](pullServer.md)中所述设置 HTTP 拉取服务器时，指定 ModulePath  和 ConfigurationPath  键的目录。 ModulePath  键指明了应在哪里存储模块的打包 `.zip` 文件。 ConfigurationPath  键指明了应在哪里存储任何 `.mof` 文件和 `.checksum` 文件。

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>在 SMB 共享上

将拉取客户端设置为使用 SMB 共享时，指定 ConfigurationRepositoryShare  。
所有 `.mof` 文件和 `.checksum` 文件应存储在 ConfigurationRepositoryShare  块的 SourcePath  目录中。

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>后续步骤

接下来，需要将拉取客户端配置为拉取指定配置。 有关详细信息，请参阅以下指南之一：

- [使用配置 ID 设置拉取客户端 (v4)](pullClientConfigId4.md)
- [使用配置 ID 设置拉取客户端 (v5)](pullClientConfigId.md)
- [使用配置名称设置拉取客户端 (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>另请参阅

- [设置 DSC SMB 拉取服务器](pullServerSmb.md)
- [设置 DSC HTTP 拉取服务器](pullServer.md)
- [打包资源并将其上传到拉取服务器](package-upload-resources.md)
