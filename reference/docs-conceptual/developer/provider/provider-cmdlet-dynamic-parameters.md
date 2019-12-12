---
title: 提供程序 cmdlet 动态参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359946"
---
# <a name="provider-cmdlet-dynamic-parameters"></a><span data-ttu-id="57331-102">提供程序 cmdlet 动态参数</span><span class="sxs-lookup"><span data-stu-id="57331-102">Provider cmdlet dynamic parameters</span></span>

<span data-ttu-id="57331-103">当用户为 cmdlet 的一个静态参数指定特定值时，提供程序可以定义添加到提供程序 cmdlet 的动态参数。</span><span class="sxs-lookup"><span data-stu-id="57331-103">Providers can define dynamic parameters that are added to a provider cmdlet when the user specifies a certain value for one of the static parameters of the cmdlet.</span></span> <span data-ttu-id="57331-104">例如，提供程序可以根据用户在调用 `Get-Item` 或 `Set-Item` 提供程序 cmdlet 时指定的路径来添加不同的动态参数。</span><span class="sxs-lookup"><span data-stu-id="57331-104">For example, a provider can add different dynamic parameters based on what path the user specifies when they call the `Get-Item` or `Set-Item` provider cmdlets.</span></span>

## <a name="dynamic-parameter-methods"></a><span data-ttu-id="57331-105">动态参数方法</span><span class="sxs-lookup"><span data-stu-id="57331-105">Dynamic Parameter Methods</span></span>

<span data-ttu-id="57331-106">动态参数是通过实现某个动态参数方法（例如[Itemcmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)和[Itemcmdletprovider. Setitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s 方法）来定义的，该方法是。</span><span class="sxs-lookup"><span data-stu-id="57331-106">Dynamic parameters are defined by implementing one of the dynamic parameter methods, such as the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s methods.</span></span> <span data-ttu-id="57331-107">这些方法返回一个对象，该对象具有使用类似于独立 cmdlet 的特性修饰的公共属性。</span><span class="sxs-lookup"><span data-stu-id="57331-107">These methods return an object that has public properties that are decorated with attributes similar to those of stand-alone cmdlets.</span></span> <span data-ttu-id="57331-108">下面是从证书提供程序中获取的[Itemcmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法的实现示例：</span><span class="sxs-lookup"><span data-stu-id="57331-108">Here is an example of an implementation of the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method taken from the Certificate provider:</span></span>

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

<span data-ttu-id="57331-109">与提供程序 cmdlet 的静态参数不同，可以指定这些参数的特征，方法与在独立 cmdlet 中定义参数的方式相同。</span><span class="sxs-lookup"><span data-stu-id="57331-109">Unlike the static parameters of provider cmdlets, you can specify the characteristics of these parameters in the same way that parameters are defined in stand-alone cmdlets.</span></span> <span data-ttu-id="57331-110">下面是从证书提供程序获取的动态参数类的示例：</span><span class="sxs-lookup"><span data-stu-id="57331-110">Here is an example of a dynamic parameter class taken from the Certificate provider:</span></span>

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a><span data-ttu-id="57331-111">动态参数</span><span class="sxs-lookup"><span data-stu-id="57331-111">Dynamic Parameters</span></span>

<span data-ttu-id="57331-112">下面是可用于添加动态参数的静态参数的列表。</span><span class="sxs-lookup"><span data-stu-id="57331-112">Here is a list of the static parameters that can be used to add dynamic parameters.</span></span>

<span data-ttu-id="57331-113">`Clear-Content` cmdlet，通过实现 Clearcontentdynamicparameters \* 方法，你可以定义由 Clear cmdlet 的 `Path` 参数触发的动态参数。 " [\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) " 方法。</span><span class="sxs-lookup"><span data-stu-id="57331-113">`Clear-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the Clear-Clear cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method.</span></span>

<span data-ttu-id="57331-114">`Clear-Item` cmdlet，你可以通过实现[Clearitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法来定义由 `Clear-Item` cmdlet 的 `Path` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-114">`Clear-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) method.</span></span>

<span data-ttu-id="57331-115">`Clear-ItemProperty` cmdlet，你可以通过实现[Clearpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法来定义由 `Clear-ItemProperty` cmdlet 的 `Path` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-115">`Clear-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="57331-116">`Copy-Item` cmdlet，你可以通过实现[Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法，定义由 `Copy-Item` cmdlet 的 `Path`、`Destination`和 `Recurse` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-116">`Copy-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Destination`, and `Recurse` parameters of the `Copy-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method.</span></span>

<span data-ttu-id="57331-117">ChildItems cmdlet 可以通过实现 Containercmdletprovider 和 Getchilditemsdynamicparameters \* 方法，定义由 `Get-ChildItem` cmdlet 的 `Path` 和 `Recurse` 参数触发的动态参数。 [\* 和](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) [\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。），可以定义这些参数。</span><span class="sxs-lookup"><span data-stu-id="57331-117">Get-ChildItems cmdlet You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Get-ChildItem` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) and [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methods.</span></span>

<span data-ttu-id="57331-118">`Get-Content` cmdlet，你可以通过实现[Getcontentreaderdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法来定义由 `Get-Content` cmdlet 的 `Path` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-118">`Get-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span>

<span data-ttu-id="57331-119">`Get-Item` cmdlet，你可以通过实现[Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法来定义由 `Get-Item` cmdlet 的 `Path` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-119">`Get-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method.</span></span>

<span data-ttu-id="57331-120">`Get-ItemProperty` cmdlet，你可以通过实现[Getpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法来定义由 `Get-ItemProperty` cmdlet 的 `Path` 和 `Name` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-120">`Get-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Get-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="57331-121">`Invoke-Item` cmdlet，你可以通过实现[Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法来定义由 `Invoke-Item` cmdlet 的 `Path` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-121">`Invoke-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Invoke-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

<span data-ttu-id="57331-122">`Move-Item` cmdlet，你可以通过实现[Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法来定义由 `Move-Item` cmdlet 的 `Path` 和 `Destination` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-122">`Move-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Destination` parameters of the `Move-Item` cmdlet by implementing the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="57331-123">`New-Item` cmdlet，你可以通过实现[Newitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法，定义由 `New-Item` cmdlet 的 `Path`、`ItemType`和 `Value` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-123">`New-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `ItemType`, and `Value` parameters of the `New-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span>

<span data-ttu-id="57331-124">`New-ItemProperty` cmdlet，你可以通过实现[Newpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法，定义由 `Value` cmdlet 的 `Path`、`Name`、`PropertyType`和 `New-ItemProperty` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-124">`New-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Name`, `PropertyType`, and `Value` parameters of the `New-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="57331-125">`New-PSDrive` cmdlet，可以定义由 `New-PSDrive` cmdlet 返回的即 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 对象所触发的动态参数，方法是实现 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 方法。</span><span class="sxs-lookup"><span data-stu-id="57331-125">`New-PSDrive` cmdlet You can define dynamic parameters that are triggered by the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object returned by the `New-PSDrive` cmdlet by implementing the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span>

<span data-ttu-id="57331-126">`Remove-Item` 你可以通过实现[Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法来定义由 `Remove-Item` cmdlet 的 `Path` 和 `Recurse` 参数触发的动态参数，则为。</span><span class="sxs-lookup"><span data-stu-id="57331-126">`Remove-Item` You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Remove-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="57331-127">`Remove-ItemProperty` 你可以通过实现[Removepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法来定义由 `Remove-ItemProperty` cmdlet 的 `Path` 和 `Name` 参数触发的动态参数，则为。</span><span class="sxs-lookup"><span data-stu-id="57331-127">`Remove-ItemProperty` You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Remove-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="57331-128">`Rename-Item` cmdlet，你可以通过实现[Renameitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法来定义由 `Rename-Item` cmdlet 的 `Path` 和 `NewName` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-128">`Rename-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `NewName` parameters of the `Rename-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span>

<span data-ttu-id="57331-129">`Rename-ItemProperty` 可以通过实现[Renamepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法来定义由 `Rename-ItemProperty` cmdlet 的 `Path`、`Name`和 `NewName` 参数触发的动态参数。 ""。</span><span class="sxs-lookup"><span data-stu-id="57331-129">`Rename-ItemProperty` You can define dynamic parameters that are triggered by the `Path`, `Name`, and `NewName` parameters of the `Rename-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="57331-130">`Set-Content` cmdlet，你可以通过实现[Getcontentwriterdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法来定义由 `Set-Content` cmdlet 的 `Path` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-130">`Set-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Set-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method.</span></span>

<span data-ttu-id="57331-131">`Set-Item` cmdlet，你可以通过实现[Setitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法来定义由 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-131">`Set-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) method.</span></span>

<span data-ttu-id="57331-132">`Set-ItemProperty` cmdlet，你可以通过实现[Setpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法来定义由 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-132">`Set-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="57331-133">`Test-Path` cmdlet，你可以通过实现[Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法来定义由 `Test-Path` cmdlet 的 `Path` 参数触发的动态参数。 "</span><span class="sxs-lookup"><span data-stu-id="57331-133">`Test-Path` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Test-Path` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

## <a name="see-also"></a><span data-ttu-id="57331-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57331-134">See Also</span></span>

[<span data-ttu-id="57331-135">编写 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="57331-135">Writing a Windows PowerShell Provider</span></span>](./writing-a-windows-powershell-provider.md)