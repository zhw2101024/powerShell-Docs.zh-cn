---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: b839b476bb4ef7f8d73b158d61f0e8cbc1265e60
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="d598c-102">Import-DscResource 关键字支持 -ModuleVersion 参数</span><span class="sxs-lookup"><span data-stu-id="d598c-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="d598c-103">我们向创作 DSC 配置时可用的 `Import-DscResource` 动态关键字添加了一个新参数。</span><span class="sxs-lookup"><span data-stu-id="d598c-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="d598c-104">现在，配置作者可以明确指定从中加载 DSC 资源的模块版本。</span><span class="sxs-lookup"><span data-stu-id="d598c-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="d598c-105">该关键字的新语法为：</span><span class="sxs-lookup"><span data-stu-id="d598c-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="d598c-106">**Name**：要导入的一个或多个资源的名称。</span><span class="sxs-lookup"><span data-stu-id="d598c-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="d598c-107">**ModuleName**：要导入的一个或多个模块的模块名称或 ModuleSpecification 对象。</span><span class="sxs-lookup"><span data-stu-id="d598c-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="d598c-108">**ModuleVersion**：要导入的模块的版本。</span><span class="sxs-lookup"><span data-stu-id="d598c-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="d598c-109">如果使用 ModuleName，则它只能表示一个模块的名称。</span><span class="sxs-lookup"><span data-stu-id="d598c-109">If used, ModuleName must represent only one module by name.</span></span> 

<span data-ttu-id="d598c-110">在 Windows PowerShell ISE 中，它与 IntelliSense 一起出现：</span><span class="sxs-lookup"><span data-stu-id="d598c-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="d598c-111">**注意**：`–ModuleVersion` 参数只能与 `–ModuleName` 参数结合使用。</span><span class="sxs-lookup"><span data-stu-id="d598c-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="d598c-112">它不能与仅使用 `–Name` 参数的资源名称一起使用。</span><span class="sxs-lookup"><span data-stu-id="d598c-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="d598c-113">在此之前，加载 DSC 资源时指定模块版本的唯一方法是通过使用模块规范对象，例如：`–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="d598c-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>

