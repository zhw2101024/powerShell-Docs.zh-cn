---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 构建自定义 Windows PowerShell Desired State Configuration 资源
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400389"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="8d285-103">构建自定义 Windows PowerShell Desired State Configuration 资源</span><span class="sxs-lookup"><span data-stu-id="8d285-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="8d285-104">适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8d285-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8d285-105">Windows PowerShell Desired State Configuration (DSC) 具有可用于配置环境的内置资源。</span><span class="sxs-lookup"><span data-stu-id="8d285-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="8d285-106">本主题通过特定信息和示例概述了与主题相关的开发资源和链接。</span><span class="sxs-lookup"><span data-stu-id="8d285-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="8d285-107">DSC 资源组件</span><span class="sxs-lookup"><span data-stu-id="8d285-107">DSC resource components</span></span>

<span data-ttu-id="8d285-108">DSC 资源是一个 Windows PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="8d285-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="8d285-109">该模块既包含资源的架构（可配置属性的定义）又包含资源的实现（执行配置指定的实际工作的代码）。</span><span class="sxs-lookup"><span data-stu-id="8d285-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="8d285-110">可在 MOF 文件中定义 DSC 资源架构，由脚本模块执行实现。</span><span class="sxs-lookup"><span data-stu-id="8d285-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="8d285-111">从版本 5 开始支持 PowerShell 类，因此架构和实现都可以在类中定义。</span><span class="sxs-lookup"><span data-stu-id="8d285-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="8d285-112">以下主题对如何创建 DSC 资源进行了更详细的介绍。</span><span class="sxs-lookup"><span data-stu-id="8d285-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="8d285-113">使用 MOF 编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="8d285-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="8d285-114">在 C# 中实现 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="8d285-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="8d285-115">使用 PowerShell 类编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="8d285-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="8d285-116">复合资源将 DSC 配置用作资源</span><span class="sxs-lookup"><span data-stu-id="8d285-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="8d285-117">使用资源设计器工具</span><span class="sxs-lookup"><span data-stu-id="8d285-117">Using the Resource Designer tool</span></span>](../authoringResourceMofDesigner.md)
