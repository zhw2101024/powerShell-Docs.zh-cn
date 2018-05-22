---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的内置 Desired State Configuration 资源
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="3c8c0-103">适用于 Linux 的内置 Desired State Configuration 资源</span><span class="sxs-lookup"><span data-stu-id="3c8c0-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="3c8c0-104">资源是可用于编写 PowerShell Desired State Configuration (DSC) 脚本的构建基块。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="3c8c0-105">适用于 Linux 的 DSC 附带了一套用于配置资源（如文件和文件夹、程序包、环境变量、服务和进程）的内置功能。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="3c8c0-106">内置资源</span><span class="sxs-lookup"><span data-stu-id="3c8c0-106">Built-in resources</span></span>

<span data-ttu-id="3c8c0-107">下表提供了关于主题的资源和链接列表，其中进行了详细介绍。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="3c8c0-108">[nxArchive 资源](lnxArchiveResource.md)--提供了用于在特定路径解压存档文件（.tar、.zip）的机制。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="3c8c0-109">[nxEnvironment 资源](lnxEnvironmentResource.md)--管理目标节点上的环境变量。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="3c8c0-110">[nxFile 资源](lnxFileResource.md)--管理 Linux 文件和目录。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="3c8c0-111">[nxFileLine 资源](lnxFileLineResource.md)--管理 Linux 文件中的各个行。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="3c8c0-112">[nxGroup 资源](lnxGroupResource.md)--管理本地 Linux 组。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="3c8c0-113">[nxPackage 资源](lnxPackageResource.md) - 管理 Linux 节点上的包。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="3c8c0-114">[nxScript 资源](lnxScriptResource.md) - 在目标节点上运行脚本。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="3c8c0-115">[nxService 资源](lnxServiceResource.md)--管理 Linux 服务（守护程序）。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="3c8c0-116">[nxSshAuthorizedKeys 资源](lnxSshAuthorizedKeysResource.md)--为 Linux 用户管理公共 ssh 密钥。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="3c8c0-117">[nxUser 资源](lnxUserResource.md)--管理本地 Linux 用户。</span><span class="sxs-lookup"><span data-stu-id="3c8c0-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>