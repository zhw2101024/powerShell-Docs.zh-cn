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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359946"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>提供程序 cmdlet 动态参数

当用户为 cmdlet 的一个静态参数指定特定值时，提供程序可以定义添加到提供程序 cmdlet 的动态参数。 例如，提供程序可以根据用户在调用 `Get-Item` 或 `Set-Item` 提供程序 cmdlet 时指定的路径来添加不同的动态参数。

## <a name="dynamic-parameter-methods"></a>动态参数方法

动态参数是通过实现某个动态参数方法（例如[Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)和[）定义的。Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s 方法。 这些方法返回一个对象，该对象具有使用类似于独立 cmdlet 的特性修饰的公共属性。 下面是从证书提供程序中获取的[Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法的实现示例：

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

与提供程序 cmdlet 的静态参数不同，可以指定这些参数的特征，方法与在独立 cmdlet 中定义参数的方式相同。 下面是从证书提供程序获取的动态参数类的示例：

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

## <a name="dynamic-parameters"></a>动态参数

下面是可用于添加动态参数的静态参数的列表。

`Clear-Content` cmdlet，可以通过实现 Clearcontentdynamicparameters 来定义由 Clear cmdlet 的 `Path` 参数触发的动态参数。 [Icontentcmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)付款方式.

`Clear-Item` cmdlet，你可以通过实现[Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法来定义由 `Clear-Item` cmdlet 的 `Path` 参数触发的动态参数。 "

`Clear-ItemProperty` cmdlet，可以通过实现 Clearpropertydynamicparameters * 方法来定义由 `Clear-ItemProperty` cmdlet 的 `Path` 参数触发的动态参数。 [Ipropertycmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法.

`Copy-Item` cmdlet，可以通过实现的[方式定义由 `Copy-Item` cmdlet 的 `Path`、`Destination` 和 `Recurse` 参数触发的动态参数，方法是实现Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。

ChildItems cmdlet 可定义由 `Path` 和 `Recurse` 参数 `Get-ChildItem` 的动态参数，方法是通过实现[Containercmdletprovider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)和[. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法的，它用于实现。

`Get-Content` cmdlet，可以通过实现 Getcontentreaderdynamicparameters 来定义由 `Get-Content` cmdlet 的 `Path` 参数触发的动态参数。 [Icontentcmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)付款方式.

`Get-Item` cmdlet，你可以通过实现[Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法来定义由 `Get-Item` cmdlet 的 `Path` 参数触发的动态参数。 "

`Get-ItemProperty` cmdlet，可以通过实现 Getpropertydynamicparameters 来定义由 `Get-ItemProperty` cmdlet 的 `Path` 和 `Name` 参数触发的动态参数。 [Ipropertycmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。

`Invoke-Item` cmdlet，可以通过实现 Invokedefaultactiondynamicparameters 来定义由 `Invoke-Item` cmdlet 的 `Path` 参数触发的动态参数。 [Itemcmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)付款方式.

`Move-Item` cmdlet，可以通过实现 Moveitemdynamicparameters 来定义由 `Move-Item` cmdlet 的 `Path` 和 `Destination` 参数触发的动态参数。 [Navigationcmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法。

`New-Item` cmdlet，可以通过实现的[方式定义由 `New-Item` cmdlet 的 `Path`、`ItemType` 和 `Value` 参数触发的动态参数，方法是实现Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。

`New-ItemProperty` cmdlet，可以通过实现 `Path` 来定义由 `Value` cmdlet 的、`Name`、`PropertyType` 和 `New-ItemProperty` 参数触发的动态参数，方法是实现[Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。

`New-PSDrive` cmdlet，可以定义由 `New-PSDrive` cmdlet 返回的即 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 对象所触发的动态参数，方法是实现 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 方法。

`Remove-Item` 可以通过实现 Removeitemdynamicparameters 来定义由 `Remove-Item` cmdlet 的 `Path` 和 `Recurse` 参数触发的动态参数。 [Containercmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)付款方式.

`Remove-ItemProperty` 可以定义通过实现的[`Path` 和 `Name` `Remove-ItemProperty` 参数所触发的动态参数，方法是实现Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法。

`Rename-Item` cmdlet，可以通过实现 Renameitemdynamicparameters 来定义由 `Rename-Item` cmdlet 的 `Path` 和 `NewName` 参数触发的动态参数。 [Containercmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。

`Rename-ItemProperty` 可以通过实现 `Rename-ItemProperty` cmdlet 的 `Path`、`Name` 和 `NewName` 参数来定义动态参数，方法是实现[Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法。

`Set-Content` cmdlet，可以通过实现 Getcontentwriterdynamicparameters 来定义由 `Set-Content` cmdlet 的 `Path` 参数触发的动态参数。 [Icontentcmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)付款方式.

`Set-Item` cmdlet，可以通过实现 Setitemdynamicparameters 来定义由 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数触发的动态参数。 [Itemcmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)付款方式.

`Set-ItemProperty` cmdlet，可以通过实现 Setpropertydynamicparameters 来定义由 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数触发的动态参数。 [Ipropertycmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。

`Test-Path` cmdlet，可以通过实现 Invokedefaultactiondynamicparameters 来定义由 `Test-Path` cmdlet 的 `Path` 参数触发的动态参数。 [Itemcmdletprovider. *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)付款方式.

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)