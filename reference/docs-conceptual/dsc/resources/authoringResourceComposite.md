---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 复合资源--将 DSC 配置用作资源
ms.openlocfilehash: 79fe94bd5bab8fa460714e5994d2e2487f302410
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/25/2019
ms.locfileid: "75415891"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>复合资源：将 DSC 配置用作资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

在实际情况中，配置可能会变得长而复杂，调用许多不同的资源，并设置大量的属性。 将 Windows PowerShell Desired State Configuration (DSC) 配置用作其他配置的资源可以解决复杂性的问题。 这叫做复合资源。 复合资源是使用参数的 DSC 配置。 配置的参数充当资源的属性。 此配置将另存为带有 `.schema.psm1` 扩展名的文件。 它取代了 MOF 架构和典型 DSC 资源中的资源脚本。 有关 DSC 资源的详细信息，请参阅 [Windows PowerShell Desired State Configuration 资源](resources.md)。

## <a name="creating-the-composite-resource"></a>创建复合资源

在示例中，我们创建了一个调用多个现有资源的配置来配置虚拟机。 配置采用了之后将在配置块中使用的参数，而没有指定应该在配置块中设置的值。

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

    # Create VM specific diff VHD
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

> [!NOTE]
> DSC 目前不支持在复合资源中放置复合资源或嵌套配置。

### <a name="saving-the-configuration-as-a-composite-resource"></a>将配置保存为复合资源

要将参数化配置用作 DSC 资源，请将其保存至与其他基于 MOF 资源的目录结构相类似的目录结构下，并以 `.schema.psm1` 扩展名命名。 在此示例中，我们将文件命名为 `xVirtualMachine.schema.psm1`。 你还需要创建一个名为 `xVirtualMachine.psd1` 并包含下列行的清单。

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> 这是对 `MyDscResources.psd1` 的补充，它是文件夹 `MyDscResources` 下所有资源的模块清单。

完成操作后，文件夹结构应如下所示。

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

现在可以使用 `Get-DscResource` cmdlet 找到资源，并且可以使用该 cmdlet 或者使用 Windows PowerShell ISE 中的 <kbd>Ctrl</kbd>+<kbd>Space</kbd> 自动完成找到其属性。

## <a name="using-the-composite-resource"></a>使用复合资源

接下来我们将创建一个调用复合资源的配置。 此配置调用 xVirtualMachine 复合资源来创建一个虚拟机，然后调用 **xComputer** 资源重命名虚拟机。

```powershell
configuration RenameVM
{
    Import-DscResource -Module xVirtualMachine
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

通过将 VM 名称数组传入 xVirtualMachine 资源，你还可以使用此资源创建多个 VM。

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a>支持 PsDscRunAsCredential

> [!NOTE]
> PsDscRunAsCredential  在 PowerShell 5.0 及更高版本中受支持。

可以在 [DSC 配置](../configurations/configurations.md)资源块中使用 PsDscRunAsCredential  属性，以指定应使用指定的一组凭据运行资源。 有关详细信息，请参阅[使用用户凭据运行 DSC](../configurations/runAsUser.md)。

若要从自定义资源访问用户上下文，可以使用自动变量 `$PsDscContext`。

例如，下面的代码会将用于运行资源的用户上下文写入详细输出流：

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>另请参阅

### <a name="concepts"></a>概念

- [使用 MOF 编写自定义 DSC 资源](authoringResourceMOF.md)
- [Windows PowerShell Desired State Configuration 入门](../overview/overview.md)
