---
title: 提供程序 cmdlet 的动态参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058226"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>提供程序 cmdlet 动态参数

提供程序可以定义当用户指定一个 cmdlet 的静态参数的值会添加到提供程序 cmdlet 的动态参数。 例如，一个提供程序可以添加其他动态参数基于用户指定当调用方法上路径是什么`Get-Item`或`Set-Item`提供程序 cmdlet。

## <a name="dynamic-parameter-methods"></a>动态参数方法

动态参数定义通过实现一种动态参数方法，如[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)和[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)的方法。 这些方法返回具有使用类似于独立 cmdlet 属性修饰的公共属性的对象。 下面是实现的示例[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)取自 Certificate 提供程序的方法：

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

与不同的提供程序 cmdlet 的静态参数，可以与独立 cmdlet 中定义参数的相同的方式指定这些参数的特征。 下面是取自 Certificate 提供程序的动态参数类的示例：

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

`Clear-Content` cmdlet 可以定义由触发的动态参数`Path`清除清除 cmdlet 通过实现参数[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法。

`Clear-Item` cmdlet 可以定义由触发的动态参数`Path`的参数`Clear-Item`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。

`Clear-ItemProperty` cmdlet 可以定义由触发的动态参数`Path`的参数`Clear-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。

`Copy-Item` cmdlet 可以定义由触发的动态参数`Path`， `Destination`，并`Recurse`的参数`Copy-Item`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。

Get ChildItems cmdlet 可以定义由触发的动态参数`Path`并`Recurse`的参数`Get-ChildItem`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)和[System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。

`Get-Content` cmdlet 可以定义由触发的动态参数`Path`的参数`Get-Content`cmdlet 通过实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。

`Get-Item` cmdlet 可以定义由触发的动态参数`Path`的参数`Get-Item`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。

`Get-ItemProperty` cmdlet 可以定义由触发的动态参数`Path`并`Name`的参数`Get-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。

`Invoke-Item` cmdlet 可以定义由触发的动态参数`Path`的参数`Invoke-Item`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法。

`Move-Item` cmdlet 可以定义由触发的动态参数`Path`并`Destination`的参数`Move-Item`cmdlet 通过实现[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法。

`New-Item` cmdlet 可以定义由触发的动态参数`Path`， `ItemType`，并`Value`的参数`New-Item`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。

`New-ItemProperty` cmdlet 可以定义由触发的动态参数`Path`， `Name`， `PropertyType`，和`Value`的参数`New-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。

`New-PSDrive` cmdlet 可以定义由触发的动态参数[即 System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)返回的对象`New-PSDrive`cmdlet 通过实现[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。

`Remove-Item` 您可以定义由触发的动态参数`Path`并`Recurse`的参数`Remove-Item`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法。

`Remove-ItemProperty` 您可以定义由触发的动态参数`Path`并`Name`的参数`Remove-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法。

`Rename-Item` cmdlet 可以定义由触发的动态参数`Path`并`NewName`的参数`Rename-Item`cmdlet 通过实现[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。

`Rename-ItemProperty` 您可以定义由触发的动态参数`Path`， `Name`，并`NewName`的参数`Rename-ItemProperty`cmdlet 通过实现[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法。

`Set-Content` cmdlet 可以定义由触发的动态参数`Path`的参数`Set-Content`cmdlet 通过实现[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法。

`Set-Item` cmdlet 可以定义由触发的动态参数`Path`并`Value`的参数`Set-Item`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。

`Set-ItemProperty` cmdlet 可以定义由触发的动态参数`Path`并`Value`的参数`Set-Item`cmdlet 通过实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。

`Test-Path` cmdlet 可以定义由触发的动态参数`Path`的参数`Test-Path`cmdlet 通过实现[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)