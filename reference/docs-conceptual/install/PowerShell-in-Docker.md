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
# <a name="using-powershell-in-docker"></a><span data-ttu-id="dcef3-103">在 Docker 中使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dcef3-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="dcef3-104">我们发布了预安装 PowerShell 的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="dcef3-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="dcef3-105">本文介绍如何开始在 Docker 容器中使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dcef3-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="dcef3-106">查找可用映像</span><span class="sxs-lookup"><span data-stu-id="dcef3-106">Finding available images</span></span>

<span data-ttu-id="dcef3-107">已发布的映像需要 Docker 17.05 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="dcef3-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="dcef3-108">还应在没有 `sudo` 或本地管理权限的情况下能够运行 Docker。</span><span class="sxs-lookup"><span data-stu-id="dcef3-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="dcef3-109">请按照 Docker 的官方[说明][install]正确安装 `docker`。</span><span class="sxs-lookup"><span data-stu-id="dcef3-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="dcef3-110">发布容器派生自正式分发映像（如 `centos:7`），然后安装依赖项，最后安装 PowerShell 包。</span><span class="sxs-lookup"><span data-stu-id="dcef3-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="dcef3-111">这些容器位于 [hub.docker.com/r/microsoft/powershell][docker-release]。</span><span class="sxs-lookup"><span data-stu-id="dcef3-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="dcef3-112">有关这些 Docker 映像的详细信息，请访问 GitHub 上的 [PowerShell-Docker][PowerShell-Docker] 存储库。</span><span class="sxs-lookup"><span data-stu-id="dcef3-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="dcef3-113">在容器中使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dcef3-113">Using PowerShell in a container</span></span>

<span data-ttu-id="dcef3-114">以下步骤显示了下载映像和启动交互式 PowerShell 会话所需的 Docker 命令。</span><span class="sxs-lookup"><span data-stu-id="dcef3-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="dcef3-115">在不再需要映像时将其删除</span><span class="sxs-lookup"><span data-stu-id="dcef3-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="dcef3-116">以下命令用于在不再需要 Docker 容器时将其删除。</span><span class="sxs-lookup"><span data-stu-id="dcef3-116">The following command is used to delete the Docker container when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="dcef3-117">法律和授权</span><span class="sxs-lookup"><span data-stu-id="dcef3-117">Legal and Licensing</span></span>

<span data-ttu-id="dcef3-118">PowerShell 根据 [MIT 许可][]获得授权。</span><span class="sxs-lookup"><span data-stu-id="dcef3-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="dcef3-119">Windows Docker 文件和映像许可证</span><span class="sxs-lookup"><span data-stu-id="dcef3-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="dcef3-120">通过请求和使用 Windows 容器的容器 OS 映像，你可以确认、了解并同意 Docker 中心提供的补充许可条款：</span><span class="sxs-lookup"><span data-stu-id="dcef3-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="dcef3-121">[Window Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="dcef3-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="dcef3-122">[Nano Server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="dcef3-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="dcef3-123">遥测</span><span class="sxs-lookup"><span data-stu-id="dcef3-123">Telemetry</span></span>

<span data-ttu-id="dcef3-124">默认情况下，PowerShell 会收集没有个人身份信息的有限遥测，以帮助开发 PowerShell 的未来版本。</span><span class="sxs-lookup"><span data-stu-id="dcef3-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="dcef3-125">若选择不要发送遥测，请在从安装位置启动 PowerShell 之前，创建名为 `POWERSHELL_TELEMETRY_OPTOUT` 且设置为 `1` 值的环境变量。</span><span class="sxs-lookup"><span data-stu-id="dcef3-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="dcef3-126">我们收集的遥测位于 [Microsoft 隐私声明][privacy]中。</span><span class="sxs-lookup"><span data-stu-id="dcef3-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT 许可]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
