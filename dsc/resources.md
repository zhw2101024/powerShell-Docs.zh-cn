---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC 资源"
ms.openlocfilehash: 0994616673b5e447c69c09154bfdb9b9126a88c8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="dcf4e-103">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="dcf4e-103">DSC Resources</span></span>

><span data-ttu-id="dcf4e-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dcf4e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="dcf4e-105">Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。</span><span class="sxs-lookup"><span data-stu-id="dcf4e-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="dcf4e-106">资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。</span><span class="sxs-lookup"><span data-stu-id="dcf4e-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="dcf4e-107">资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。</span><span class="sxs-lookup"><span data-stu-id="dcf4e-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="dcf4e-108">资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。</span><span class="sxs-lookup"><span data-stu-id="dcf4e-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="dcf4e-109">以下主题介绍了 DSC 资源：</span><span class="sxs-lookup"><span data-stu-id="dcf4e-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="dcf4e-110">内置 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="dcf4e-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="dcf4e-111">构建自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="dcf4e-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="dcf4e-112">适用于 Linux 的内置 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="dcf4e-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

