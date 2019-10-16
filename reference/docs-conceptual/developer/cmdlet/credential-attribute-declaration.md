---
title: Credential 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369886"
---
# <a name="credential-attribute-declaration"></a>凭据属性声明

Credential 特性是一个可选属性，可与类型为[system.object](/dotnet/api/System.Management.Automation.PSCredential)的 Credential 参数一起使用，以便还可以将字符串作为参数传递给参数。 将此特性添加到参数声明中时，Windows PowerShell 会将字符串输入转换为[system.web](/dotnet/api/System.Management.Automation.PSCredential)对象。 例如， [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet 使用此属性使 Windows PowerShell 生成由 cmdlet 返回的 " [system.web](/dotnet/api/System.Management.Automation.PSCredential) " 对象。

## <a name="syntax"></a>语法

```csharp
[Credential]
```

## <a name="remarks"></a>备注

- 通常，此属性由类型为 "system.servicemodel" 的参数[使用，以便](/dotnet/api/System.Management.Automation.PSCredential)还可以将字符串作为参数传递给参数。 当向参数传递了一个[系统管理](/dotnet/api/System.Management.Automation.PSCredential)对象时，Windows PowerShell 不会执行任何操作。

- 创建[system.web](/dotnet/api/System.Management.Automation.PSCredential)对象时，Windows PowerShell 将使用当前主机向用户显示相应的提示。 例如，使用此属性时，默认主机会显示用户名和密码提示。 但是，如果使用定义不同提示符的自定义主机，则会显示该提示。

- 此特性与参数特性一起使用。 有关该属性的详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。

- Credential 特性是由[Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute)类定义的。

## <a name="see-also"></a>另请参阅

[参数别名](./parameter-aliases.md)

[参数属性声明](./parameter-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
