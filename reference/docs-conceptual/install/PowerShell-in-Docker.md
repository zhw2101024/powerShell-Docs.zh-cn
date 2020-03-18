---
title: 在 Docker 中使用 PowerShell
description: 如何使用预安装在 Docker 映像中的 PowerShell。
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: 771214c719ef01fe2c8bc56a4b26c629fcad3856
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279654"
---
# <a name="using-powershell-in-docker"></a>在 Docker 中使用 PowerShell

我们发布了预安装 PowerShell 的 Docker 映像。 本文介绍如何开始在 Docker 容器中使用 PowerShell。

## <a name="finding-available-images"></a>查找可用映像

已发布的映像需要 Docker 17.05 或更高版本。 还应在没有 `sudo` 或本地管理权限的情况下能够运行 Docker。 请按照 Docker 的官方[说明][install]正确安装 `docker`。

发布容器派生自正式分发映像（如 `centos:7`），然后安装依赖项，最后安装 PowerShell 包。

这些容器位于 [hub.docker.com/r/microsoft/powershell][docker-release]。

有关这些 Docker 映像的详细信息，请访问 GitHub 上的 [PowerShell-Docker][PowerShell-Docker] 存储库。

## <a name="using-powershell-in-a-container"></a>在容器中使用 PowerShell

以下步骤显示了下载映像和启动交互式 PowerShell 会话所需的 Docker 命令。

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>在不再需要映像时将其删除

以下命令用于在不再需要 Docker 容器时将其删除。

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a>法律和授权

PowerShell 根据 [MIT 许可][]获得授权。

### <a name="windows-docker-file-and-image-licenses"></a>Windows Docker 文件和映像许可证

通过请求和使用 Windows 容器的容器 OS 映像，你可以确认、了解并同意 Docker 中心提供的补充许可条款：

- [Window Server Core][Window Server Core]
- [Nano Server][Nano Server]

### <a name="telemetry"></a>遥测

默认情况下，PowerShell 会收集没有个人身份信息的有限遥测，以帮助开发 PowerShell 的未来版本。 若选择不要发送遥测，请在从安装位置启动 PowerShell 之前，创建名为 `POWERSHELL_TELEMETRY_OPTOUT` 且设置为 `1` 值的环境变量。 我们收集的遥测位于 [Microsoft 隐私声明][privacy]中。

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT 许可]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
