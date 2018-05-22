---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用具有多个版本的资源
ms.openlocfilehash: 6400d6506106657ba28fa1f9c83d9f8ee1c93ba3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="0402b-103">使用具有多个版本的资源</span><span class="sxs-lookup"><span data-stu-id="0402b-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="0402b-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0402b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0402b-105">在 PowerShell 5.0 中，DSC 资源可以拥有多个版本，并且这些版本可以并行安装在计算机上。</span><span class="sxs-lookup"><span data-stu-id="0402b-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="0402b-106">这是通过将多个版本的资源模块包含在同一个模块文件夹中实现的。</span><span class="sxs-lookup"><span data-stu-id="0402b-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="0402b-107">并行安装多个资源版本</span><span class="sxs-lookup"><span data-stu-id="0402b-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="0402b-108">可以使用 [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet 的 **MinimumVersion**、**MaximumVersion** 和 **RequiredVersion** 参数来指定要安装的模块版本。</span><span class="sxs-lookup"><span data-stu-id="0402b-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="0402b-109">调用 **Install-Module** 而不指定某个版本安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="0402b-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="0402b-110">例如，存在多个版本的 **xFailOverCluster** 模块，其中每个都包含 **xCluster** 资源。</span><span class="sxs-lookup"><span data-stu-id="0402b-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="0402b-111">调用 **Install-Module** 而不指定版本号的结果如下：</span><span class="sxs-lookup"><span data-stu-id="0402b-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="0402b-112">现在，如果再次调用 **Install-Module**，但指定 1.1.0.0 的 **RequiredVersion**，则结果如下：</span><span class="sxs-lookup"><span data-stu-id="0402b-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="0402b-113">在配置中指定资源版本</span><span class="sxs-lookup"><span data-stu-id="0402b-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="0402b-114">如果已在计算机上安装多个资源，那么在配置中使用资源时，必须指定该资源的版本。</span><span class="sxs-lookup"><span data-stu-id="0402b-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="0402b-115">为此，请指定 **Import-DscResource** 关键字的 **ModuleVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="0402b-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="0402b-116">如果你无法指定已安装多个版本的资源模块的版本，则配置会生成错误。</span><span class="sxs-lookup"><span data-stu-id="0402b-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="0402b-117">下面的配置演示如何指定要调用的资源的版本：</span><span class="sxs-lookup"><span data-stu-id="0402b-117">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="0402b-118">注意：Import-DscResource 的 ModuleVersion 参数在 PowerShell 4.0 中不可用。</span><span class="sxs-lookup"><span data-stu-id="0402b-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="0402b-119">在 PowerShell 4.0 中，你可以将模块规范对象传递到 Import-DscResource 的 ModuleName 参数，从而指定模块版本。</span><span class="sxs-lookup"><span data-stu-id="0402b-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="0402b-120">模块规范对象是包含 ModuleName 和 RequiredVersion 键的哈希表。</span><span class="sxs-lookup"><span data-stu-id="0402b-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="0402b-121">例如：</span><span class="sxs-lookup"><span data-stu-id="0402b-121">For example:</span></span>

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

<span data-ttu-id="0402b-122">此操作在 PowerShell 5.0 中也有效，但建议使用 **ModuleVersion** 参数。</span><span class="sxs-lookup"><span data-stu-id="0402b-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="0402b-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0402b-123">See also</span></span>
* [<span data-ttu-id="0402b-124">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="0402b-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="0402b-125">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="0402b-125">DSC Resources</span></span>](resources.md)