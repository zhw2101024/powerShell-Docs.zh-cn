---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 复合资源--将 DSC 配置用作资源
ms.openlocfilehash: 7fa6ee56d4706b96fb47123c7aa00c4df6256492
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73933827"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="08453-103">复合资源：将 DSC 配置用作资源</span><span class="sxs-lookup"><span data-stu-id="08453-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="08453-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="08453-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="08453-105">在实际情况中，配置可能会变得长而复杂，调用许多不同的资源，并设置大量的属性。</span><span class="sxs-lookup"><span data-stu-id="08453-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="08453-106">将 Windows PowerShell Desired State Configuration (DSC) 配置用作其他配置的资源可以解决复杂性的问题。</span><span class="sxs-lookup"><span data-stu-id="08453-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="08453-107">我们把它叫做复合资源。</span><span class="sxs-lookup"><span data-stu-id="08453-107">We call this a composite resource.</span></span> <span data-ttu-id="08453-108">复合资源是使用参数的 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="08453-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="08453-109">配置的参数充当资源的属性。</span><span class="sxs-lookup"><span data-stu-id="08453-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="08453-110">将配置保存为带有 **.schema.psm1** 扩展名的文件，它代替了典型 DSC 资源中的 MOF 架构和资源脚本（有关 DSC 资源的详细信息，请参阅 [Windows PowerShell Desired State Configuration 资源](resources.md)）。</span><span class="sxs-lookup"><span data-stu-id="08453-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="08453-111">创建复合资源</span><span class="sxs-lookup"><span data-stu-id="08453-111">Creating the composite resource</span></span>

<span data-ttu-id="08453-112">在示例中，我们创建了一个调用多个现有资源的配置来配置虚拟机。</span><span class="sxs-lookup"><span data-stu-id="08453-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="08453-113">配置采用了大量之后将在配置块中使用的参数，而没有指定应该在配置块中设置的值。</span><span class="sxs-lookup"><span data-stu-id="08453-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="08453-114">将配置保存为复合资源</span><span class="sxs-lookup"><span data-stu-id="08453-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="08453-115">要将参数化配置用作 DSC 资源，请将其保存至与其他基于 MOF 资源的目录结构相类似的目录结构下，并以 **.schema.psm1** 扩展名命名。</span><span class="sxs-lookup"><span data-stu-id="08453-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="08453-116">在此示例中，我们将文件命名为 **xVirtualMachine.schema.psm1**。</span><span class="sxs-lookup"><span data-stu-id="08453-116">For this example, we'll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="08453-117">你还需要创建一个名为 **xVirtualMachine.psd1** 并包含下列行的的清单。</span><span class="sxs-lookup"><span data-stu-id="08453-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="08453-118">请注意，这是除 **MyDscResources.psd1**（位于 **MyDscResources** 文件夹下所有资源的模块清单）之外的另一个清单。</span><span class="sxs-lookup"><span data-stu-id="08453-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="08453-119">完成操作后，文件夹结构应如下所示。</span><span class="sxs-lookup"><span data-stu-id="08453-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="08453-120">现在可以使用 Get-DscResource cmdlet 找到资源，并且可以使用该 cmdlet 或者使用 Windows PowerShell ISE 中的 **Ctrl+Space** 自动完成找到其属性。</span><span class="sxs-lookup"><span data-stu-id="08453-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="08453-121">使用复合资源</span><span class="sxs-lookup"><span data-stu-id="08453-121">Using the composite resource</span></span>

<span data-ttu-id="08453-122">接下来我们将创建一个调用复合资源的配置。</span><span class="sxs-lookup"><span data-stu-id="08453-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="08453-123">此配置调用 xVirtualMachine 复合资源来创建一个虚拟机，然后调用 **xComputer** 资源重命名虚拟机。</span><span class="sxs-lookup"><span data-stu-id="08453-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

<span data-ttu-id="08453-124">通过将 VM 名称数组传入 xVirtualMachine 资源，你还可以使用此资源创建多个 VM。</span><span class="sxs-lookup"><span data-stu-id="08453-124">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="08453-125">支持 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="08453-125">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="08453-126">PsDscRunAsCredential  在 PowerShell 5.0 及更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="08453-126">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="08453-127">可以在 [DSC 配置](../configurations/configurations.md)资源块中使用 PsDscRunAsCredential  属性，以指定应使用指定的一组凭据运行资源。</span><span class="sxs-lookup"><span data-stu-id="08453-127">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="08453-128">有关详细信息，请参阅[使用用户凭据运行 DSC](../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="08453-128">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="08453-129">若要从自定义资源访问用户上下文，可以使用自动变量 `$PsDscContext`。</span><span class="sxs-lookup"><span data-stu-id="08453-129">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="08453-130">例如，下面的代码会将用于运行资源的用户上下文写入详细输出流：</span><span class="sxs-lookup"><span data-stu-id="08453-130">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="08453-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08453-131">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="08453-132">概念</span><span class="sxs-lookup"><span data-stu-id="08453-132">Concepts</span></span>
* [<span data-ttu-id="08453-133">使用 MOF 编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="08453-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="08453-134">Windows PowerShell Desired State Configuration 入门</span><span class="sxs-lookup"><span data-stu-id="08453-134">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
