---
标题：复合资源：将 DSC 配置用作资源 ms.date：2016 年 5 月 16 日 关键字：powershell、DSC 描述：  
ms.topic：文章作者：eslesar 管理员：dongill ms.prod：powershell
---

# 复合资源：将 DSC 配置用作资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

在实际情况中，配置可能会变得长而复杂，调用许多不同的资源，并设置大量的属性。 将 Windows PowerShell Desired State Configuration (DSC) 配置用作其他配置的资源可以解决复杂性的问题。 我们把它叫做复合资源。 复合资源是使用参数的 DSC 配置。 配置的参数充当资源的属性。 将配置保存为带有 **.schema.psm1** 扩展名的文件，它代替了典型 DSC 资源中的 MOF 架构和资源脚本（有关 DSC 资源的详细信息，请参阅 [Windows PowerShell Desired State Configuration 资源](resources.md)）。

## 创建复合资源

在示例中，我们创建了一个调用多个现有资源的配置来配置虚拟机。 配置采用了大量之后将在配置块中使用的参数，而没有指定应该在配置块中设置的值。

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Creae VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### 将配置保存为复合资源

要将参数化配置用作 DSC 资源，请将其保存至与其他基于 MOF 资源的目录结构相类似的目录结构下，并以 **.schema.psm1** 扩展名命名。 在此示例中，我们将文件命名为 **xVirtualMachine.schema.psm1**。 你还需要创建一个名为 **xVirtualMachine.psd1** 并包含下列行的的清单。 请注意，这是除 **MyDscResources.psd1**（位于 **MyDscResources** 文件夹下所有资源的模块清单）之外的另一个清单。

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

完成操作后，文件夹结构应如下所示。

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSC Resources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

现在可以使用 Get-DscResource cmdlet 找到资源，并且可以使用该 cmdlet 或者使用 Windows PowerShell ISE 中的 **Ctrl+Space** 自动完成找到其属性。

## 使用复合资源

接下来我们将创建一个调用复合资源的配置。 此配置调用 xVirtualMachine 复合资源来创建一个虚拟机，然后调用 **xComputer** 资源重命名虚拟机。

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## 另请参阅
### 概念
* [使用 MOF 编写自定义 DSC 资源](authoringResourceMOF.md)
* [Windows PowerShell Desired State Configuration 入门](overview.md)



<!--HONumber=May16_HO3-->


