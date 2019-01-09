---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 导入已安装资源的指定版本
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400372"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="32ca7-103">导入已安装资源的指定版本</span><span class="sxs-lookup"><span data-stu-id="32ca7-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="32ca7-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="32ca7-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="32ca7-105">在 PowerShell 5.0 中，可以并排显示的计算机上安装不同版本的 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="32ca7-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="32ca7-106">资源模块可以存储在名为文件夹的版本的不同版本的资源。</span><span class="sxs-lookup"><span data-stu-id="32ca7-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="32ca7-107">安装单独的资源版本并排显示</span><span class="sxs-lookup"><span data-stu-id="32ca7-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="32ca7-108">可以使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet 的 **MinimumVersion**、**MaximumVersion** 和 **RequiredVersion** 参数来指定要安装的模块版本。</span><span class="sxs-lookup"><span data-stu-id="32ca7-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="32ca7-109">调用 **Install-Module** 而不指定某个版本安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="32ca7-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="32ca7-110">例如，存在多个版本的 xFailOverCluster 模块，其中每个都包含 xCluster 资源。</span><span class="sxs-lookup"><span data-stu-id="32ca7-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="32ca7-111">调用**Install-module**数而不指定版本安装的模块的最新版本。</span><span class="sxs-lookup"><span data-stu-id="32ca7-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="32ca7-112">若要安装特定版本的模块，请指定**RequiredVersion**的 1.1.0.0。</span><span class="sxs-lookup"><span data-stu-id="32ca7-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="32ca7-113">这会安装指定的版本并行安装的版本。</span><span class="sxs-lookup"><span data-stu-id="32ca7-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="32ca7-114">现在，您看到同时使用时会列出的模块版本`Get-DSCResource`。</span><span class="sxs-lookup"><span data-stu-id="32ca7-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="32ca7-115">在配置中指定资源版本</span><span class="sxs-lookup"><span data-stu-id="32ca7-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="32ca7-116">如果已安装的计算机上的单独的资源版本，必须指定该资源的版本，在配置中使用时。</span><span class="sxs-lookup"><span data-stu-id="32ca7-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="32ca7-117">为此，请指定 **Import-DscResource** 关键字的 **ModuleVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="32ca7-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="32ca7-118">如果你无法指定已安装多个版本的资源模块的版本，则配置会生成错误。</span><span class="sxs-lookup"><span data-stu-id="32ca7-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="32ca7-119">下面的配置演示如何指定要调用的资源的版本：</span><span class="sxs-lookup"><span data-stu-id="32ca7-119">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="32ca7-120">注意：Import-dscresource 的 ModuleVersion 参数不是在 PowerShell 4.0 中提供的。</span><span class="sxs-lookup"><span data-stu-id="32ca7-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="32ca7-121">在 PowerShell 4.0 中，你可以将模块规范对象传递到 Import-DscResource 的 ModuleName 参数，从而指定模块版本。</span><span class="sxs-lookup"><span data-stu-id="32ca7-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="32ca7-122">模块规范对象是包含 ModuleName 和 RequiredVersion 键的哈希表。</span><span class="sxs-lookup"><span data-stu-id="32ca7-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="32ca7-123">例如：</span><span class="sxs-lookup"><span data-stu-id="32ca7-123">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="32ca7-124">此操作在 PowerShell 5.0 中也有效，但建议使用 **ModuleVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="32ca7-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="32ca7-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32ca7-125">See also</span></span>

- [<span data-ttu-id="32ca7-126">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="32ca7-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="32ca7-127">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="32ca7-127">DSC Resources</span></span>](../resources/resources.md)
