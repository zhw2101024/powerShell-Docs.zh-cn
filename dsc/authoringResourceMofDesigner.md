---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "使用资源设计器工具"
ms.openlocfilehash: c39b48f67d3874ee3cd2f2704aeb7390fa186fe4
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="e42ff-103">使用资源设计器工具</span><span class="sxs-lookup"><span data-stu-id="e42ff-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="e42ff-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e42ff-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e42ff-105">资源设计器工具是一组由 **xDscResourceDesigner** 模块公开的 cmdlet，它使 Windows PowerShell Desired State Configuration (DSC) 的创建更加轻松简单。</span><span class="sxs-lookup"><span data-stu-id="e42ff-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="e42ff-106">此资源中的 cmdlet 能帮助你创建新资源的 MOF 架构、脚本模块和目录结构。</span><span class="sxs-lookup"><span data-stu-id="e42ff-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="e42ff-107">有关 DSC 资源的详细信息，请参阅[构建自定义 Windows PowerShell Desired State Configuration 资源](authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="e42ff-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="e42ff-108">在本主题中，我们将创建一个管理 Active Directory 用户的 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="e42ff-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="e42ff-109">使用 [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet 安装 **xDscResourceDesigner** 模块。</span><span class="sxs-lookup"><span data-stu-id="e42ff-109">Use the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="e42ff-110">**请注意**：**Install-Module** 包含在 **PowerShellGet** 模块中，后者纳入 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="e42ff-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="e42ff-111">可在 [PackageManagement PowerShell 模块预览](https://www.microsoft.com/en-us/download/details.aspx?id=49186)中下载适用于 PowerShell 3.0 和 4.0 的 **PowerShellGet**。</span><span class="sxs-lookup"><span data-stu-id="e42ff-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="e42ff-112">创建资源属性</span><span class="sxs-lookup"><span data-stu-id="e42ff-112">Creating resource properties</span></span>
<span data-ttu-id="e42ff-113">我们首先要确定资源将公开的属性。</span><span class="sxs-lookup"><span data-stu-id="e42ff-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="e42ff-114">在此示例中，我们将通过以下属性来定义 Active Directory 用户。</span><span class="sxs-lookup"><span data-stu-id="e42ff-114">For this example, we will define an Active Directory user with the following properties.</span></span>
 
<span data-ttu-id="e42ff-115">参数名称  说明</span><span class="sxs-lookup"><span data-stu-id="e42ff-115">Parameter name  Description</span></span>
* <span data-ttu-id="e42ff-116">**UserName**：唯一标识用户的键属性。</span><span class="sxs-lookup"><span data-stu-id="e42ff-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="e42ff-117">**Ensure**：指定用户帐户应该为 Present 还是 Absent。</span><span class="sxs-lookup"><span data-stu-id="e42ff-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="e42ff-118">此参数只有两个可能的值。</span><span class="sxs-lookup"><span data-stu-id="e42ff-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="e42ff-119">**DomainCredential**：用户的域密码。</span><span class="sxs-lookup"><span data-stu-id="e42ff-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="e42ff-120">**Password**：允许必要时配置对用户密码进行更改所需的用户密码。</span><span class="sxs-lookup"><span data-stu-id="e42ff-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="e42ff-121">我们使用 **New-xDscResourceProperty** cmdlet 来创建属性。</span><span class="sxs-lookup"><span data-stu-id="e42ff-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="e42ff-122">下面的 PowerShell 命令可以创建上述属性。</span><span class="sxs-lookup"><span data-stu-id="e42ff-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="e42ff-123">创建资源</span><span class="sxs-lookup"><span data-stu-id="e42ff-123">Create the resource</span></span>

<span data-ttu-id="e42ff-124">创建好资源属性后，我们就可以调用 **New-xDscResource** cmdlet 来创建资源。</span><span class="sxs-lookup"><span data-stu-id="e42ff-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="e42ff-125">**New-xDscResource** cmdlet 采用了属性列表作为参数。</span><span class="sxs-lookup"><span data-stu-id="e42ff-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="e42ff-126">它还采用了应将模块创建于的路径、新资源的名称以及包含它的模块名称。</span><span class="sxs-lookup"><span data-stu-id="e42ff-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="e42ff-127">下面的 PowerShell 命令可以创建资源。</span><span class="sxs-lookup"><span data-stu-id="e42ff-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="e42ff-128">**New-xDscResource** cmdlet 创建 MOF 架构、主干资源脚本、新资源所需目录结构以及公开新资源的模块清单。</span><span class="sxs-lookup"><span data-stu-id="e42ff-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="e42ff-129">MOF 架构文件位于 **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**，其内容如下。</span><span class="sxs-lookup"><span data-stu-id="e42ff-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

<span data-ttu-id="e42ff-130">资源脚本位于 **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**。</span><span class="sxs-lookup"><span data-stu-id="e42ff-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="e42ff-131">资源脚本不包含实现资源的实际逻辑，你必须自己添加。</span><span class="sxs-lookup"><span data-stu-id="e42ff-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="e42ff-132">主干脚本的内容如下。</span><span class="sxs-lookup"><span data-stu-id="e42ff-132">The contents of the skeleton script are as follows.</span></span>

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a><span data-ttu-id="e42ff-133">更新资源</span><span class="sxs-lookup"><span data-stu-id="e42ff-133">Updating the resource</span></span>

<span data-ttu-id="e42ff-134">如果需要添加或修改资源的参数列表，可以调用 **Update-xDscResource** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e42ff-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="e42ff-135">该 cmdlet 将使用新参数列表更新资源。</span><span class="sxs-lookup"><span data-stu-id="e42ff-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="e42ff-136">如果你已在资源脚本中添加逻辑，它将保持不变。</span><span class="sxs-lookup"><span data-stu-id="e42ff-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="e42ff-137">例如，假如你想为用户将最新日志包含在资源中。</span><span class="sxs-lookup"><span data-stu-id="e42ff-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="e42ff-138">你可以调用 **New-xDscResourceProperty** 创建新属性，然后调用 **Update-xDscResource** 并将新属性添加到属性列表，而不用重新编写资源。</span><span class="sxs-lookup"><span data-stu-id="e42ff-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="e42ff-139">测试资源架构</span><span class="sxs-lookup"><span data-stu-id="e42ff-139">Testing a resource schema</span></span>

<span data-ttu-id="e42ff-140">资源设计器工具还公开了一个 cmdlet，可用于测试手动编写的 MOF 架构的有效性。</span><span class="sxs-lookup"><span data-stu-id="e42ff-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="e42ff-141">调用 **Test-xDscSchema** cmdlet，将 MOF 资源架构的路径作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="e42ff-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="e42ff-142">该 cmdlet 将输出架构中的任何错误。</span><span class="sxs-lookup"><span data-stu-id="e42ff-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="e42ff-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e42ff-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="e42ff-144">概念</span><span class="sxs-lookup"><span data-stu-id="e42ff-144">Concepts</span></span>
[<span data-ttu-id="e42ff-145">构建自定义 Windows PowerShell Desired State Configuration 资源</span><span class="sxs-lookup"><span data-stu-id="e42ff-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="e42ff-146">其他资源</span><span class="sxs-lookup"><span data-stu-id="e42ff-146">Other Resources</span></span>
[<span data-ttu-id="e42ff-147">xDscResourceDesigner 模块</span><span class="sxs-lookup"><span data-stu-id="e42ff-147">xDscResourceDesigner Module</span></span>](https://powershellgallery.com/packages/xDscResourceDesigner)