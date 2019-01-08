---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 使用 PowerShell 类编写自定义 DSC 资源
ms.openlocfilehash: 0759685b04688f574d72b62a15833832ad19e816
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400817"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="d3ce8-103">使用 PowerShell 类编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="d3ce8-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="d3ce8-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d3ce8-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d3ce8-105">了解了在 Windows PowerShell 5.0 中使用 PowerShell 类的简介后，现在你可以通过创建一个类来定义 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="d3ce8-106">类可以同时定义资源的架构和实现，因此无需创建单独的 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="d3ce8-107">因为无需 **DSCResources** 文件夹，基于类的资源的文件夹结构也得以简化。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="d3ce8-108">在基于类的 DSC 资源中，架构被定义为类的属性，可通过特性对其进行修改来指定属性类型。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="d3ce8-109">资源通过 **Get()**、**Set()** 和 **Test()** 的方法得到实现（相当于脚本资源中的 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 函数）。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="d3ce8-110">在本主题中，我们将创建一个名为 **FileResource** 的简单资源来管理指定路径中的文件。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="d3ce8-111">有关 DSC 资源的详细信息，请参阅[构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="d3ce8-112">**注意：** 在基于类的资源中不支持泛型集合。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="d3ce8-113">类资源的文件夹结构</span><span class="sxs-lookup"><span data-stu-id="d3ce8-113">Folder structure for a class resource</span></span>

<span data-ttu-id="d3ce8-114">想要使用 PowerShell 类实现 DSC 自定义资源，请创建下列文件夹结构。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="d3ce8-115">在 **MyDscResource.psm1** 中定义类，并且在 **MyDscResource.psd1** 中定义模块清单。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="d3ce8-116">创建类</span><span class="sxs-lookup"><span data-stu-id="d3ce8-116">Create the class</span></span>

<span data-ttu-id="d3ce8-117">使用类关键字创建 PowerShell 类。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="d3ce8-118">使用 **DscResource()** 特性来指定类是 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="d3ce8-119">类的名称就是 DSC 资源的名称。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="d3ce8-120">声明属性</span><span class="sxs-lookup"><span data-stu-id="d3ce8-120">Declare properties</span></span>

<span data-ttu-id="d3ce8-121">DSC 资源架构被定义为类的属性。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="d3ce8-122">我们声明下列三个属性。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-122">We declare three properties as follows.</span></span>

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

<span data-ttu-id="d3ce8-123">请注意，属性通过特性进行修改。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="d3ce8-124">特性的含义如下：</span><span class="sxs-lookup"><span data-stu-id="d3ce8-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="d3ce8-125">**Dscproperty （key)**:该属性是必需的。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="d3ce8-126">属性为键。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-126">The property is a key.</span></span> <span data-ttu-id="d3ce8-127">所有被标记为键的属性的值必须接合以唯一地标识配置内的资源实例。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="d3ce8-128">**Dscproperty （mandatory)**:该属性是必需的。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="d3ce8-129">**Dscproperty （notconfigurable)**:此属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="d3ce8-130">使用此特性标记的属性不能通过配置进行设置，但出现时使用 **Get()** 方法进行填充。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="d3ce8-131">**Dscproperty （)**:该属性可配置，但不需要。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="d3ce8-132">**$Path** 和 **$SourcePath** 属性都是字符串。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="d3ce8-133">**$CreationTime** 是一个 [DateTime](/dotnet/api/system.datetime) 属性。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="d3ce8-134">**$Ensure** 属性是枚举类，定义如下。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="d3ce8-135">实现该方法</span><span class="sxs-lookup"><span data-stu-id="d3ce8-135">Implementing the methods</span></span>

<span data-ttu-id="d3ce8-136">**Get()**、**Set()** 和 **Test()** 方法类似于脚本资源中的 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 函数。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="d3ce8-137">此代码还包括 CopyFile() 函数，是一个可将文件从 **$SourcePath** 复制到 **$Path** 的 helper 函数。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

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

### <a name="the-complete-file"></a><span data-ttu-id="d3ce8-138">完整文件</span><span class="sxs-lookup"><span data-stu-id="d3ce8-138">The complete file</span></span>
<span data-ttu-id="d3ce8-139">完整类文件如下。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-139">The complete class file follows.</span></span>

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


## <a name="create-a-manifest"></a><span data-ttu-id="d3ce8-140">创建清单</span><span class="sxs-lookup"><span data-stu-id="d3ce8-140">Create a manifest</span></span>

<span data-ttu-id="d3ce8-141">若要让基于类的资源对 DSC 引擎可用，你必须在清单文件中添加 **DscResourcesToExport** 声明，以指示模块导出资源。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="d3ce8-142">我们的清单如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3ce8-142">Our manifest looks like this:</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

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

## <a name="test-the-resource"></a><span data-ttu-id="d3ce8-143">测试资源</span><span class="sxs-lookup"><span data-stu-id="d3ce8-143">Test the resource</span></span>

<span data-ttu-id="d3ce8-144">如前面所述，将类和清单文件保存到文件夹结构中之后，就可以创建一个使用新资源的配置。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="d3ce8-145">有关如何运行 DSC 配置的信息，请参阅[执行配置](../pull-server/enactingConfigurations.md)。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="d3ce8-146">下面的配置将检查 `c:\test\test.txt` 的文件是否存在，如果不存在，则会从 `c:\test.txt` 进行复制（运行配置前应先创建 `c:\test.txt`）。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="d3ce8-147">支持 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d3ce8-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="d3ce8-148">**注意：\*\*\*\*PsDscRunAsCredential** PowerShell 5.0 及更高版本支持。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="d3ce8-149">可以在 [DSC 配置](../configurations/configurations.md)资源块中使用 PsDscRunAsCredential 属性，以指定应使用指定的一组凭据运行资源。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="d3ce8-150">有关详细信息，请参阅[使用用户凭据运行 DSC](../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="d3ce8-151">需要或禁止对资源使用 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d3ce8-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="d3ce8-152">DscResource() 属性需要使用可选的参数 RunAsCredential。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="d3ce8-153">此参数可取以下三个值之一：</span><span class="sxs-lookup"><span data-stu-id="d3ce8-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="d3ce8-154">`Optional` **PsDscRunAsCredential**：对于调用此资源的配置，此为可选值。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="d3ce8-155">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-155">This is the default value.</span></span>
- <span data-ttu-id="d3ce8-156">`Mandatory` **PsDscRunAsCredential**：必须用于调用此资源的所有配置。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="d3ce8-157">`NotSupported`：调用此资源的配置无法使用 PsDscRunAsCredential。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="d3ce8-158">`Default` 与 `Optional` 相同。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="d3ce8-159">例如，使用以下属性指定自定义资源不支持使用 PsDscRunAsCredential：</span><span class="sxs-lookup"><span data-stu-id="d3ce8-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="d3ce8-160">访问用户上下文</span><span class="sxs-lookup"><span data-stu-id="d3ce8-160">Access the user context</span></span>

<span data-ttu-id="d3ce8-161">若要从自定义资源访问用户上下文，可以使用自动变量 `$global:PsDscContext`。</span><span class="sxs-lookup"><span data-stu-id="d3ce8-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="d3ce8-162">例如，下面的代码会将用于运行资源的用户上下文写入详细输出流：</span><span class="sxs-lookup"><span data-stu-id="d3ce8-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="d3ce8-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3ce8-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="d3ce8-164">概念</span><span class="sxs-lookup"><span data-stu-id="d3ce8-164">Concepts</span></span>
[<span data-ttu-id="d3ce8-165">构建自定义 Windows PowerShell Desired State Configuration 资源</span><span class="sxs-lookup"><span data-stu-id="d3ce8-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)