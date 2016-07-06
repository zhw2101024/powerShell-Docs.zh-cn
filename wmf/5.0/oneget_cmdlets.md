# PackageManagement Cmdlet
这是 PackageManagement 用以支持软件发现、安装和盘存 (SDII) 的核心。 尝试进行这些操作试用以下 cmdlet：
-   Find-Package
-   Find-PackageProvider
-   Get-Package
-   Get-PackageProvider
-   Get-PackageSource
-   Import-PackageProvider
-   Install-Package
-   Install-PackageProvider
-   Register-PackageSource
-   Save-Package
-   Set-PackageSource
-   Uninstall-Package
-   Unregister-PackageSource

由于 PackageManagement 是一个 PowerShell 模块，因此可以执行以下操作来更新 PackageManagement 本身：
```powershell
PS C:\> Install-Module PackageManagement –Force
```
在此示例中，必须重新输入 PowerShell 会话以切换到新版本的 PackageManagement。

## [Find-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890709.aspx)
此 cmdlet 允许使用已加载的包提供程序发现可用包源中的软件包。
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

## [Find-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676544.aspx)
Find-PackageProvider cmdlet 用于查找匹配的 PackageManagement 提供程序，这些提供程序在已向 PowerShellGet 注册的包源中可用。 这些包提供程序都能用 Install-PackageProvider cmdlet 直接进行安装。 默认情况下，这包括 PowerShell 库中带“PackageManagement”和“Provider”标记的可用模块。 

Find-PackageProvider 还可以查找匹配的 PackageManagement 提供程序，这些提供程序在 PackageManagement Azure Blob 存储区可用，通过该存储区我们可以使用 PackageManagement Boostrapper 提供程序查找并安装它们。
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## [Get-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890704.aspx)
此 cmdlet 可以返回所有已使用 PackageManagement 安装的软件包列表。
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## [Get-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/dn890703.aspx)
可以通过使用 cmdlet 列出已加载并可用于本地计算机的包提供程序清单。
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## [Get-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890705.aspx)
此 cmdlet 用于获取已注册包提供程序的包源列表。
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## [Import-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676545.aspx)
此 cmdlet 用于将 Package Management 包提供程序添加到当前会话。
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
```

##[ Install-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890711.aspx)

此 cmdlet 允许使用已加载的包提供程序在可用包源中安装软件包。
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## [Install-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676543.aspx)
此 cmdlet 用于安装一个或多个 Package Management 包提供程序。
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

## [Register-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890701.aspx)
此 cmdlet 用于为指定的包提供程序添加包源。
每个 PackageManagement 提供程序可能有一个或多个软件源或存储库。 PackageManagement 可提供 PowerShell cmdlet 来添加/删除/查询源。 例如，你可以为 NuGet 提供程序注册包源：
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## [Save-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890708.aspx)
此 cmdlet 用于将包保存到本地计算机，但不安装它们。
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## [Set-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890710.aspx)
此 cmdlet 可更改关于现有包源的信息。 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## [Uninstall-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890702.aspx)
此 cmdlet 可卸载安装在本地计算机上的包。
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## [Unregister-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```


<!--HONumber=Jun16_HO4-->


