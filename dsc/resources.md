---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC 资源
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219804"
---
# <a name="dsc-resources"></a><span data-ttu-id="a5f2b-103">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a5f2b-103">DSC Resources</span></span>

><span data-ttu-id="a5f2b-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a5f2b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a5f2b-105">Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。</span><span class="sxs-lookup"><span data-stu-id="a5f2b-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="a5f2b-106">资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。</span><span class="sxs-lookup"><span data-stu-id="a5f2b-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="a5f2b-107">资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。</span><span class="sxs-lookup"><span data-stu-id="a5f2b-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="a5f2b-108">资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。</span><span class="sxs-lookup"><span data-stu-id="a5f2b-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="a5f2b-109">以下主题介绍了 DSC 资源：</span><span class="sxs-lookup"><span data-stu-id="a5f2b-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="a5f2b-110">内置 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a5f2b-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="a5f2b-111">构建自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a5f2b-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="a5f2b-112">适用于 Linux 的内置 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="a5f2b-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)