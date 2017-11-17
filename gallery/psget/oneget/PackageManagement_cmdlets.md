---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: PackageManagement_cmdlets
ms.openlocfilehash: aca4f461ff0e51aa812f8219c74bd7d85d1e7b2d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="2bbf0-103">PackageManagement Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-103">PackageManagement Cmdlets</span></span>
<span data-ttu-id="2bbf0-104">这是 PackageManagement 用以支持软件发现、安装和盘存 (SDII) 的核心。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-104">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="2bbf0-105">尝试进行这些操作试用以下 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="2bbf0-105">Try out the cmdlets for these operations:</span></span>
-   <span data-ttu-id="2bbf0-106">Find-Package</span><span class="sxs-lookup"><span data-stu-id="2bbf0-106">Find-Package</span></span>
-   <span data-ttu-id="2bbf0-107">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="2bbf0-107">Find-PackageProvider</span></span>
-   <span data-ttu-id="2bbf0-108">Get-Package</span><span class="sxs-lookup"><span data-stu-id="2bbf0-108">Get-Package</span></span>
-   <span data-ttu-id="2bbf0-109">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="2bbf0-109">Get-PackageProvider</span></span>
-   <span data-ttu-id="2bbf0-110">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2bbf0-110">Get-PackageSource</span></span>
-   <span data-ttu-id="2bbf0-111">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="2bbf0-111">Import-PackageProvider</span></span>
-   <span data-ttu-id="2bbf0-112">Install-Package</span><span class="sxs-lookup"><span data-stu-id="2bbf0-112">Install-Package</span></span>
-   <span data-ttu-id="2bbf0-113">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="2bbf0-113">Install-PackageProvider</span></span>
-   <span data-ttu-id="2bbf0-114">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2bbf0-114">Register-PackageSource</span></span>
-   <span data-ttu-id="2bbf0-115">Save-Package</span><span class="sxs-lookup"><span data-stu-id="2bbf0-115">Save-Package</span></span>
-   <span data-ttu-id="2bbf0-116">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2bbf0-116">Set-PackageSource</span></span>
-   <span data-ttu-id="2bbf0-117">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="2bbf0-117">Uninstall-Package</span></span>
-   <span data-ttu-id="2bbf0-118">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2bbf0-118">Unregister-PackageSource</span></span>

<span data-ttu-id="2bbf0-119">由于 PackageManagement 是一个 PowerShell 模块，因此可以执行以下操作来更新 PackageManagement 本身：</span><span class="sxs-lookup"><span data-stu-id="2bbf0-119">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>
```powershell
PS C:\> Install-Module PackageManagement –Force
```
<span data-ttu-id="2bbf0-120">在此示例中，必须重新输入 PowerShell 会话以切换到新版本的 PackageManagement。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-120">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890709aspx"></a>[<span data-ttu-id="2bbf0-121">Find-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-121">Find-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890709.aspx)
<span data-ttu-id="2bbf0-122">此 cmdlet 允许使用已加载的包提供程序发现可用包源中的软件包。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-122">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676544aspx"></a>[<span data-ttu-id="2bbf0-123">Find-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-123">Find-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676544.aspx)
<span data-ttu-id="2bbf0-124">Find-PackageProvider cmdlet 用于查找匹配的 PackageManagement 提供程序，这些提供程序在已向 PowerShellGet 注册的包源中可用。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-124">The Find-PackageProvider cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="2bbf0-125">这些包提供程序都能用 Install-PackageProvider cmdlet 直接进行安装。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-125">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span> <span data-ttu-id="2bbf0-126">默认情况下，这包括 PowerShell 库中带“PackageManagement”和“Provider”标记的可用模块。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-126">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span> 

<span data-ttu-id="2bbf0-127">Find-PackageProvider 还可以查找匹配的 PackageManagement 提供程序，这些提供程序在 PackageManagement Azure Blob 存储区可用，通过该存储区我们可以使用 PackageManagement Boostrapper 提供程序查找并安装它们。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-127">Find-PackageProvider also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"

#For machines without internet, you can download the nuget provider first, put it to you file share and then use the following to install the nuget provider (TP5 or later).

Find-PackageProvider -Source  C:\sharedfolder\Providers\
Install-PackageProvider -Source C:\sharedfolder\Providers\ -Name nuget -force
    
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890704aspx"></a>[<span data-ttu-id="2bbf0-128">Get-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-128">Get-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890704.aspx)
<span data-ttu-id="2bbf0-129">此 cmdlet 可以返回所有已使用 PackageManagement 安装的软件包列表。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-129">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[<span data-ttu-id="2bbf0-130">Get-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-130">Get-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890703.aspx)
<span data-ttu-id="2bbf0-131">可以通过使用 cmdlet 列出已加载并可用于本地计算机的包提供程序清单。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-131">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[<span data-ttu-id="2bbf0-132">Get-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-132">Get-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890705.aspx)
<span data-ttu-id="2bbf0-133">此 cmdlet 用于获取已注册包提供程序的包源列表。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-133">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[<span data-ttu-id="2bbf0-134">Import-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-134">Import-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676545.aspx)
<span data-ttu-id="2bbf0-135">此 cmdlet 用于将 Package Management 包提供程序添加到当前会话。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-135">This cmdlet adds Package Management package providers to the current session.</span></span>
```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force

As of the Windows Server Technical Preview(TP5), Install-PackageProvider does install as well as import the provider. Hence after you run find-packageprovider and install-packageprovider, the provider should be ready to use 
```

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[<span data-ttu-id="2bbf0-136"> Install-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-136"> Install-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890711.aspx)

<span data-ttu-id="2bbf0-137">此 cmdlet 允许使用已加载的包提供程序在可用包源中安装软件包。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-137">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[<span data-ttu-id="2bbf0-138">Install-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-138">Install-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676543.aspx)
<span data-ttu-id="2bbf0-139">此 cmdlet 用于安装一个或多个 Package Management 包提供程序。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-139">This cmdlet installs one or more Package Management package providers.</span></span>
```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[<span data-ttu-id="2bbf0-140">Register-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-140">Register-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890701.aspx)
<span data-ttu-id="2bbf0-141">此 cmdlet 用于为指定的包提供程序添加包源。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-141">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="2bbf0-142">每个 PackageManagement 提供程序可能有一个或多个软件源或存储库。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-142">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="2bbf0-143">PackageManagement 可提供 PowerShell cmdlet 来添加/删除/查询源。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-143">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="2bbf0-144">例如，你可以为 NuGet 提供程序注册包源：</span><span class="sxs-lookup"><span data-stu-id="2bbf0-144">For example, you can register a package source for the NuGet provider:</span></span>
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[<span data-ttu-id="2bbf0-145">Save-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-145">Save-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890708.aspx)
<span data-ttu-id="2bbf0-146">此 cmdlet 用于将包保存到本地计算机，但不安装它们。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-146">This cmdlet saves packages to the local computer without installing them.</span></span>
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[<span data-ttu-id="2bbf0-147">Set-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-147">Set-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890710.aspx)
<span data-ttu-id="2bbf0-148">此 cmdlet 可更改关于现有包源的信息。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-148">This cmdlet changes information about an existing package source.</span></span> 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[<span data-ttu-id="2bbf0-149">Uninstall-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-149">Uninstall-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890702.aspx)
<span data-ttu-id="2bbf0-150">此 cmdlet 可卸载安装在本地计算机上的包。</span><span class="sxs-lookup"><span data-stu-id="2bbf0-150">This cmdlet uninstalls packages installed on the local computer.</span></span>
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[<span data-ttu-id="2bbf0-151">Unregister-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2bbf0-151">Unregister-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

