# 使用 MOF 编写自定义 DSC 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

在本主题中，我们将在 MOF 文件中定义 Windows PowerShell Desired State Configuration (DSC) 自定义资源的架构，并在 Windows PowerShell 脚本文件中实现资源。 此自定义资源被用于创建和维护网站。

## 创建 MOF 架构

架构定义可通过 DSC 配置脚本进行配置的资源的资源的属性。

### MOF 资源的文件夹结构

想要使用 MOF 架构实现 DSC 自定义资源，请创建下列文件夹结构。 在 Demo_IISWebsite.schema.mof 文件中定义 MOF 架构，并在 Demo_IISWebsite.ps1 中定义资源脚本。 或者你也可以创建一个模块清单 (psd1) 文件。

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

请注意，你需要在顶级文件夹下创建一个名为 DSCResources 的文件夹，并且每个资源的文件夹都必须与资源名称一致。

### MOF 文件的内容

下面是一个可用于自定义网站资源的示例 MOF 文件。 要执行此示例操作，请将此架构保存至文件，并调用文件 *Demo_IISWebsite.schema.mof*。

```
[ClassVersion("1.0.0"), FriendlyName("Website")] 
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

请注意下列有关之前代码的信息：

* `FriendlyName` 定义一个名称，你可以将其用来在 DSC 配置脚本中指代此自定义资源。 在此示例中，`Website` 相当于内置存档资源的友好名称 `Archive`。
* 为自定义资源定义的类必须派生自 `OMI_BaseResource`。
* 属性上的类型限定符 `[Key]` 表示此属性将唯一地标识资源实例。 也需要一个 `[Key]` 属性。
* `[Required]` 限定符表示属性是必需的（在使用此资源的任何配置脚本中都必须指定值）。
* `[write]` 限定符表示在配置脚本中使用自定义资源时，此属性是可选的。 `[read]` 限定符表示不能通过配置来设置属性，属性只用于报告目的。
* `Values` 按照 `ValueMap` 中定义的值的列表限制分配给属性的值。 有关详细信息，请参阅 [ValueMap 和值限定符](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx)。
* 建议在资源中包含一个名为 `Ensure` 的属性，以便与内置 DSC 资源保持一致。
* 如下所示命名自定义资源的架构文件：`classname.schema.mof`，其中 `classname` 是遵循架构定义中 `class` 关键字的标识符。

### 编写资源脚本

资源脚本实现资源的逻辑。 在此模块中必须包含三个分别名为 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 的函数。 三个函数采用的参数集都必须与你为资源创建的 MOF 架构中定义的属性集一致。 在此文档中，这组属性被称为“资源属性”。 将这三个函数保存在名为 <ResourceName>.psm1 的文件中。 在以下示例中，函数被保存在名为 Demo_IISWebsite.psm1 的文件中。

> **请注意**：在资源上多次运行相同的配置脚本时，你应该不会收到错误报告，并且资源应该与运行一次脚本保持同样的状态。 要达到此目的，请确保 **Get-TargetResource** 和 **Test-TargetResource** 函数没有改变资源，并且确保在具有相同参数值的序列中多次调用 **Set-TargetResource** 函数始终等效于调用其一次。

在 **Get-TargetResource** 函数的实现中，使用作为参数而提供的键资源属性值来检查指定资源实例的状态。 此函数必须返回列举了所有作为键的资源属性的哈希表，并返回这些属性的实际值作为对应值。 以下代码是一个示例。

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource 
{
    param 
    (       
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name; 
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }
  
        $getTargetResourceResult;
}
```

根据配置脚本中为资源属性指定的值，**Set-TargetResource** 必须执行下列操作之一：

* 创建一个新网站
* 更新现有网站
* 删除现有网站

下面的示例对此进行了演示。

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine. 
function Set-TargetResource 
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param 
    (       
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )
 
    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

最后，**Test-TargetResource** 函数必须采用与 **Get-TargetResource** 和 **Set-TargetResource** 相同的参数集。 在 **Test-TargetResource** 的实现中，检查在键参数中指定的资源实例的状态。 如果资源实例的实际状态与在参数集中指定的值不匹配，则返回 **$false**。 否则返回 **$true**。

下面的代码实现 **Test-TargetResource** 函数。

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to 
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result 
}
```

**请注意**：为方便调试，请在上述三个函数的实现中使用 **Write-Verbose** cmdlet。 此 cmdlet 将文本写入详细消息流。 默认情况下，不显示详细消息流，但你可以通过更改 **$VerbosePreference** 变量的值或通过在 DSC cmdlets = new 中使用 **Verbose** 参数来显示该流。

### 创建模块清单

最后，使用 **New-ModuleManifest** cmdlet 来为自定义资源模块定义一个 <ResourceName>.psd1 文件。 调用此 cmdlet 时，引用上一节中所介绍的脚本模块 (.psm1) 文件。 将 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 包括在要导出的函数列表中。 以下是一个示例清单文件。

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```<!--HONumber=Feb16_HO4-->
