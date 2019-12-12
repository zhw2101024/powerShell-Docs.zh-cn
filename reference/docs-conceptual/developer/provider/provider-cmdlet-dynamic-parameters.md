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
# <a name="provider-cmdlet-dynamic-parameters"></a>提供程序 cmdlet 动态参数

当用户为 cmdlet 的一个静态参数指定特定值时，提供程序可以定义添加到提供程序 cmdlet 的动态参数。 例如，提供程序可以根据用户在调用 `Get-Item` 或 `Set-Item` 提供程序 cmdlet 时指定的路径来添加不同的动态参数。

## <a name="dynamic-parameter-methods"></a>动态参数方法

动态参数是通过实现某个动态参数方法（例如[Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)和[Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s 方法）来定义的，该方法是。 这些方法返回一个对象，该对象具有使用类似于独立 cmdlet 的特性修饰的公共属性。 下面是从证书提供程序中获取的[Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法的实现示例：

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

`Clear-Content` cmdlet，通过实现 Clearcontentdynamicparameters * 方法，你可以定义由 Clear cmdlet 的 `Path` 参数触发的动态参数。 " [*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) " 方法。

`Clear-Item` cmdlet，你可以通过实现[Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法来定义由 `Clear-Item` cmdlet 的 `Path` 参数触发的动态参数。 "

`Clear-ItemProperty` cmdlet，你可以通过实现[Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法来定义由 `Clear-ItemProperty` cmdlet 的 `Path` 参数触发的动态参数。 "

`Copy-Item` cmdlet，你可以通过实现[Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法，定义由 `Copy-Item` cmdlet 的 `Path`、`Destination`和 `Recurse` 参数触发的动态参数。 "

ChildItems cmdlet 可以通过实现 Containercmdletprovider 和 Getchilditemsdynamicparameters * 方法，定义由 `Get-ChildItem` cmdlet 的 `Path` 和 `Recurse` 参数触发的动态参数。 [* 和](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) [*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。），可以定义这些参数。

`Get-Content` cmdlet，你可以通过实现[Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法来定义由 `Get-Content` cmdlet 的 `Path` 参数触发的动态参数。 "

`Get-Item` cmdlet，你可以通过实现[Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法来定义由 `Get-Item` cmdlet 的 `Path` 参数触发的动态参数。 "

`Get-ItemProperty` cmdlet，你可以通过实现[Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法来定义由 `Get-ItemProperty` cmdlet 的 `Path` 和 `Name` 参数触发的动态参数。 "

`Invoke-Item` cmdlet，你可以通过实现[Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法来定义由 `Invoke-Item` cmdlet 的 `Path` 参数触发的动态参数。 "

`Move-Item` cmdlet，你可以通过实现[Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法来定义由 `Move-Item` cmdlet 的 `Path` 和 `Destination` 参数触发的动态参数。 "

`New-Item` cmdlet，你可以通过实现[Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法，定义由 `New-Item` cmdlet 的 `Path`、`ItemType`和 `Value` 参数触发的动态参数。 "

`New-ItemProperty` cmdlet，你可以通过实现[Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法，定义由 `Value` cmdlet 的 `Path`、`Name`、`PropertyType`和 `New-ItemProperty` 参数触发的动态参数。 "

`New-PSDrive` cmdlet，可以定义由 `New-PSDrive` cmdlet 返回的即 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 对象所触发的动态参数，方法是实现 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 方法。

`Remove-Item` 你可以通过实现[Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法来定义由 `Remove-Item` cmdlet 的 `Path` 和 `Recurse` 参数触发的动态参数，则为。

`Remove-ItemProperty` 你可以通过实现[Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法来定义由 `Remove-ItemProperty` cmdlet 的 `Path` 和 `Name` 参数触发的动态参数，则为。

`Rename-Item` cmdlet，你可以通过实现[Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法来定义由 `Rename-Item` cmdlet 的 `Path` 和 `NewName` 参数触发的动态参数。 "

`Rename-ItemProperty` 可以通过实现[Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法来定义由 `Rename-ItemProperty` cmdlet 的 `Path`、`Name`和 `NewName` 参数触发的动态参数。 ""。

`Set-Content` cmdlet，你可以通过实现[Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法来定义由 `Set-Content` cmdlet 的 `Path` 参数触发的动态参数。 "

`Set-Item` cmdlet，你可以通过实现[Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法来定义由 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数触发的动态参数。 "

`Set-ItemProperty` cmdlet，你可以通过实现[Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法来定义由 `Set-Item` cmdlet 的 `Path` 和 `Value` 参数触发的动态参数。 "

`Test-Path` cmdlet，你可以通过实现[Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法来定义由 `Test-Path` cmdlet 的 `Path` 参数触发的动态参数。 "

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)