---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Publish-Module
ms.openlocfilehash: 53fca3d6756ebf698023152ce5b58b45eb0ef757
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="publish-module"></a><span data-ttu-id="26190-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="26190-103">Publish-Module</span></span>

<span data-ttu-id="26190-104">将指定模块从本机计算机发布到联机库。</span><span class="sxs-lookup"><span data-stu-id="26190-104">Publishes a specified module from the local computer to an online gallery.</span></span>

## <a name="description"></a><span data-ttu-id="26190-105">说明</span><span class="sxs-lookup"><span data-stu-id="26190-105">Description</span></span>

<span data-ttu-id="26190-106">**Publish-Module** cmdlet 使用 API 密钥（作为用户配置文件的一部分存储于库中）将模块发布到基于 NuGet 的联机库。</span><span class="sxs-lookup"><span data-stu-id="26190-106">The **Publish-Module** cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="26190-107">可根据模块的名称或包含模块的文件夹路径指定要发布的模块。</span><span class="sxs-lookup"><span data-stu-id="26190-107">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="26190-108">根据名称指定模块时，**Publish-Module** 将发布通过运行 `Get-Module -ListAvailable <Name>` 发现的第一个模块。</span><span class="sxs-lookup"><span data-stu-id="26190-108">When you specify a module by name, **Publish-Module** publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="26190-109">如果指定了要发布的模块的最低版本，**Publish-Module** 将发布其版本大于或等于指定的最小版本的第一个模块。</span><span class="sxs-lookup"><span data-stu-id="26190-109">If you specify a minimum version of a module to publish, **Publish-Module** publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="26190-110">发布模块需要在库页面显示的模块的元数据。</span><span class="sxs-lookup"><span data-stu-id="26190-110">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="26190-111">所需元数据包括模块名称、版本、说明和作者。</span><span class="sxs-lookup"><span data-stu-id="26190-111">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="26190-112">尽管大多数元数据都是从模块清单获取的，但某些元数据必须在 **Publish-Module** 参数中指定，如 *、ReleaseNote、IconUri、ProjectUri* 和 *LicenseUri*，因为这些参数与基于 NuGet 的库中的字段相匹配。</span><span class="sxs-lookup"><span data-stu-id="26190-112">Although most metadata is taken from the module manifest, some metadata must be specified in **Publish-Module** parameters, such as *Tag, ReleaseNote, IconUri, ProjectUri,* and *LicenseUri*, because these parameters match fields in a NuGet-based gallery.</span></span>

<span data-ttu-id="26190-113">RequiredVersion 参数允许指定要发布的模块的确切版本。</span><span class="sxs-lookup"><span data-stu-id="26190-113">The RequiredVersion parameter allows you to specify the exact version of a module to be published.</span></span>
<span data-ttu-id="26190-114">Path 参数也支持具有版本文件夹的模块基准路径。</span><span class="sxs-lookup"><span data-stu-id="26190-114">The Path parameter also supports the module base path with the version folder.</span></span>
<span data-ttu-id="26190-115">Publish-Module cmdlet 上的 Force 开关参数会在不提示的情况下启动 NuGet.exe。</span><span class="sxs-lookup"><span data-stu-id="26190-115">The Force switch parameter on Publish-Module cmdlet bootstraps the NuGet.exe without prompting.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="26190-116">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="26190-116">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Publish-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="26190-117">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="26190-117">Cmdlet online help reference</span></span>

[<span data-ttu-id="26190-118">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="26190-118">Publish-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398575)

## <a name="example-commands"></a><span data-ttu-id="26190-119">示例命令</span><span class="sxs-lookup"><span data-stu-id="26190-119">Example commands</span></span>

```powershell
ContosoServer module with different versions to be published.
PS C:\\windows\\system32> Get-Module -Name ContosoServer -ListAvailable
Directory: C:\\Program Files\\WindowsPowerShell\\Modules
ModuleType Version Name ExportedCommands
---------- ------- ---- ----------------
Manifest 2.8 ContosoServer Get-ContosoServer
Manifest 2.0 ContosoServer Get-ContosoServer
Manifest 1.5 ContosoServer Get-ContosoServer
Manifest 1.0 ContosoServer Get-ContosoServer
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.0 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.5 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Path "C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0" -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
_------ ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
2.0 ContosoServer LocalRepo ContosoServer module
```

## <a name="publishing-a-module-with-dependencies"></a><span data-ttu-id="26190-120">发布模块及其依赖项</span><span class="sxs-lookup"><span data-stu-id="26190-120">Publishing a module with dependencies</span></span>

### <a name="create-a-module-with-dependencies-and-version-range-specified-in-requiredmodules-property-of-its-module-manifest"></a><span data-ttu-id="26190-121">创建一个模块，其依赖项和版本范围在其模块清单的 RequiredModules 属性中指定。</span><span class="sxs-lookup"><span data-stu-id="26190-121">Create a module with dependencies and version range specified in RequiredModules property of its module manifest.</span></span>

<span data-ttu-id="26190-122">**注意：**</span><span class="sxs-lookup"><span data-stu-id="26190-122">**Note:**</span></span>
  - <span data-ttu-id="26190-123">\* 仅在 MaximumVersion 中受支持，并且还应处于版本字符串的末尾处。</span><span class="sxs-lookup"><span data-stu-id="26190-123">\* is supported only in MaximumVersion and also it should be at the end of version string.</span></span> 
  - <span data-ttu-id="26190-124">\* 在版本对象中由 999999999 替代。</span><span class="sxs-lookup"><span data-stu-id="26190-124">\* is replaced with 999999999 in the version object.</span></span>

```powershell
PS C:\windows\system32> $requiredModules = @( @{ModuleName = 'RequiredModule1'; ModuleVersion = '0.1'; MaximumVersion = '1.9'; }, @{ModuleName = 'RequiredModule2'; MaximumVersion = '1.*'; })

PS C:\windows\system32> cd C:\MyModules\ModuleWithDependencies

PS C:\MyModules\ModuleWithDependencies> New-ModuleManifest -Path .\ModuleWithDependencies.psd1 -ModuleVersion 1.0 -RequiredModules $requiredModules -Description 'ModuleWithDependencies demo module'
```

### <a name="publish-modulewithdependencies-module-with-dependencies-to-the-repository"></a><span data-ttu-id="26190-125">将 ModuleWithDependencies 模块及其依赖项发布到存储库中。</span><span class="sxs-lookup"><span data-stu-id="26190-125">Publish ModuleWithDependencies module with dependencies to the repository.</span></span>

```powershell
PS C:\MyModules\ModuleWithDependencies> Publish-Module -Path C:\MyModules\ModuleWithDependencies -Repository LocalRepo
```

### <a name="find-modulewithdependencies-module-with-its-dependencies-by-specifying--includedependencies"></a><span data-ttu-id="26190-126">通过指定 -IncludeDependencies 查找 Find ModuleWithDependencies 模块及其依赖项</span><span class="sxs-lookup"><span data-stu-id="26190-126">Find ModuleWithDependencies module with its dependencies by specifying -IncludeDependencies</span></span>

```powershell
PS C:\MyModules\ModuleWithDependencies> Find-Module -Name ModuleWithDependencies -Repository LocalRepo -IncludeDependencies

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="install-the-modulewithdependencies-module-with-dependencies"></a><span data-ttu-id="26190-127">安装 ModuleWithDependencies 模块及其依赖项。</span><span class="sxs-lookup"><span data-stu-id="26190-127">Install the ModuleWithDependencies module with dependencies.</span></span>
<span data-ttu-id="26190-128">注意，依赖项的安装过程中，需遵循版本范围。</span><span class="sxs-lookup"><span data-stu-id="26190-128">Note that version ranges are honored during the dependency installation.</span></span>

```powershell
PS C:\windows\system32> Get-InstalledModule
PS C:\windows\system32>
PS C:\windows\system32> Install-Module -Name ModuleWithDependencies -Repository LocalRepo
PS C:\windows\system32>
PS C:\windows\system32> Get-InstalledModule

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="contents-of-modulewithdependencies2-module-manifest-file"></a><span data-ttu-id="26190-129">ModuleWithDependencies2 模块清单文件的内容</span><span class="sxs-lookup"><span data-stu-id="26190-129">Contents of ModuleWithDependencies2 module manifest file</span></span>

```powershell
@{
# Version number of this module.
ModuleVersion = '2.0'
# ID used to uniquely identify this module
GUID = '0eae34da-99dd-4608-8d28-c614fe7b0841'
# Author of this module
Author = 'manikb'
# Company or vendor of this module
CompanyName = 'Unknown'
# Copyright statement for this module
Copyright = '(c) 2015 manikb. All rights reserved.'
# Description of the functionality provided by this module
Description = 'ModuleWithDependencies2 module'
# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @('RequiredModule1',
@{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'RequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'RequiredModule4'; ModuleVersion = '1.1'; MaximumVersion = '2.0'; },
@{ModuleName = 'RequiredModule5'; MaximumVersion = '1.5'; })
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @('NestedRequiredModule1',
@{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'NestedRequiredModule4'; ModuleVersion = '0.7'; MaximumVersion = '2.4'; },
@{ModuleName = 'NestedRequiredModule5'; MaximumVersion = '1.6'; },'ModuleWithDependencies2.psm1')
# Functions to export from this module
FunctionsToExport = '\*'
# Cmdlets to export from this module
CmdletsToExport = '\*'
# Variables to export from this module
VariablesToExport = '\*'
# Aliases to export from this module
AliasesToExport = '\*'
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
      # Tags applied to this module. These help with module discovery in online galleries.
      Tags = 'Tag1', 'Tag2', 'Tag-ModuleWithDependencies2-2.0'
      # A URL to the license for this module.
      LicenseUri = 'http://modulewithdependencies2.com/license'
      # A URL to the main website for this project.
      ProjectUri = 'http://modulewithdependencies2.com/'
      # A URL to an icon representing this module.
      IconUri = 'http://modulewithdependencies2.com/icon'
      # ReleaseNotes of this module
      ReleaseNotes = 'ModuleWithDependencies2 release notes'
    } # End of PSData hashtable
} # End of PrivateData hashtable
}
```


### <a name="external-dependencies"></a><span data-ttu-id="26190-130">外部依赖关系</span><span class="sxs-lookup"><span data-stu-id="26190-130">External dependencies</span></span>
<span data-ttu-id="26190-131">某些模块依赖项可进行外部托管，在这种情况下应该将它们添加到模块清单 PSData 部分中的 ExternalModuleDependencies 条目中。</span><span class="sxs-lookup"><span data-stu-id="26190-131">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>

<span data-ttu-id="26190-132">如果“SnippetPx”在存储库上不可用，将引发以下错误。</span><span class="sxs-lookup"><span data-stu-id="26190-132">If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
```powershell
Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
```

