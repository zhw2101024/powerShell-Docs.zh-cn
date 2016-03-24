# 使用 PowerShell 类编写自定义 DSC 资源

> 适用于：Windows PowerShell 5.0

了解了在 Windows PowerShell 5.0 中使用 PowerShell 类的简介后，现在你可以通过创建一个类来定义 DSC 资源。 类可以同时定义资源的架构和实现，因此无需创建单独的 MOF 文件。 因为无需 **DSCResources** 文件夹，基于类的资源的文件夹结构也得以简化。

在基于类的 DSC 资源中，架构被定义为类的属性，可通过特性对其进行修改来指定属性类型。 资源通过 **Get()**、**Set()** 和 **Test()** 的方法得到实现（相当于脚本资源中的 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 函数）。

在本主题中，我们将创建一个名为 **FileResource** 的简单资源来管理指定路径中的文件。

有关 DSC 资源的详细信息，请参阅[构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)。

## 类资源的文件夹结构

想要使用 PowerShell 类实现 DSC 自定义资源，请创建下列文件夹结构。 在 **MyDscResource.psm1** 中定义类，并且在 **MyDscResource.psd1** 中定义模块清单。

```
$env: psmodulepath (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

### 嵌套模块

或者你可以跨多个 `.psm1` 文件拆分资源，并将他们归结到嵌套模块中。
当你有大量资源时，将所有资源放在一个文件中会很难管理，因此这个做法是合理的。

```
$env: psmodulepath (folder)
    |- MyDscResource (folder)
        |- MyDscResourceA.psm1
           MyDscResourceB.psm1 
           MyDscResource.psd1 
```

你可以每个文件放一个类，也可以几个文件放一个类。 
通过嵌套模块内的子区域来对资源进行分组，这样简单有效。
从用户角度来看，使用起来也没有任何差别。
所有资源将都显示在 `MyDscResource` 模块。
考虑将这些嵌套模块当做实现的细节，让其简化你的工作。

## 创建类

使用类关键字创建 PowerShell 类。 使用 **DscResource()** 特性来指定类是 DSC 资源。 类的名称就是 DSC 资源的名称。

```powershell
[DscResource()]
class FileResource {
}
```

### 声明属性

DSC 资源架构被定义为类的属性。 我们声明下列三个属性。

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

请注意，属性通过特性进行修改。 特性的含义如下：

- **DscProperty(Key)**：属性是必需的。 属性为键。 所有被标记为键的属性的值必须接合以唯一地标识配置内的资源实例。
- **DscProperty(Mandatory)**：属性是必需的。
- **DscProperty(NotConfigurable)**：属性为只读属性。 使用此特性标记的属性不能通过配置进行设置，但出现时使用 **Get()** 方法进行填充。
- **DscProperty()**：属性可配置，但不是必需的。

**$Path** 和 **$SourcePath** 属性都是字符串。 **$CreationTime** 是一个 [DateTime](https://technet.microsoft.com/en-us/library/system.datetime.aspx) 属性。 **$Ensure** 属性是枚举类，定义如下。

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### 实现该方法

**Get()**、**Set()** 和 **Test()** 方法类似于脚本资源中的 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 函数。

此代码还包括 CopyFile() 函数，是一个可将文件从 **$SourcePath** 复制到 **$Path** 的 helper 函数。 

```powershell

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### 完整文件
完整类文件如下。

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```


## 创建清单

想要让基于类的资源对 DSC 引擎可用，必须在清单文件中包含一个 **DscResourcesToExport** 声明，指示模块导出资源。 

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = @('FileResource')

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
} 
```

如果使用**Nested modules** 将资源拆分成几个文件，则应该将嵌套模块的列表放在 `NestedModules` 键

```powershell
@{

# Don't specify RootModule

# Script module or binary module file associated with this manifest.
NestedModules = @('MyDscResourceA.psm1', 'MyDscResourceB.psm1')

DscResourcesToExport = @('MyDscResourceA', 'MyDscResourceB')

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
} 
```

## 测试资源

如前面所述，将类和清单文件保存到文件夹结构中之后，就可以创建一个使用新资源的配置。 有关如何运行 DSC 配置的信息，请参阅[执行配置](enactingConfigurations.md)。 下面的配置将检查 `c:\test\test.txt` 的文件是否存在，如果不存在，则会从 `c:\test.txt` 进行复制（运行配置前应先创建 `c:\test.txt`）。

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    } 
}
Test
Start-DscConfiguration -Wait -Force Test
```

## 另请参阅
### 概念
[构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)
<!--HONumber=Mar16_HO1-->
