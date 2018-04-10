---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: DSC 资源
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="0792d-103">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="0792d-103">DSC Resources</span></span>

><span data-ttu-id="0792d-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0792d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0792d-105">Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。</span><span class="sxs-lookup"><span data-stu-id="0792d-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="0792d-106">资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。</span><span class="sxs-lookup"><span data-stu-id="0792d-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="0792d-107">资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。</span><span class="sxs-lookup"><span data-stu-id="0792d-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="0792d-108">资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。</span><span class="sxs-lookup"><span data-stu-id="0792d-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="0792d-109">以下主题介绍了 DSC 资源：</span><span class="sxs-lookup"><span data-stu-id="0792d-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="0792d-110">内置 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="0792d-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="0792d-111">构建自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="0792d-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="0792d-112">适用于 Linux 的内置 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="0792d-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)