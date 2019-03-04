---
title: 凭据属性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: abdd6e915b768b8ac688b6fc8c3194723961765e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863393"
---
# <a name="credential-attribute-declaration"></a>凭据属性声明

凭据属性是一个可选属性，可以用于类型的凭据参数[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)以便字符串向参数还传递作为参数。 当此特性添加到参数声明中时，Windows PowerShell 会将转换到字符串输入[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)对象。 例如， [Get-credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet 使用此属性已生成的 Windows PowerShell [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet 返回的对象。
凭据属性是一个可选属性，可以用于类型的凭据参数[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)以便字符串向参数还传递作为参数。 当此特性添加到参数声明中时，Windows PowerShell 会将转换到字符串输入[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)对象。 例如， [Get-credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet 使用此属性已生成的 Windows PowerShell [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet 返回的对象。

## <a name="syntax"></a>语法

```csharp
[Credential]
```

## <a name="remarks"></a>备注

- 此属性通常由类型的参数[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)以便字符串向参数还传递作为参数。 当[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)对象传递给该参数，Windows PowerShell 不执行任何操作。

- 创建时[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)对象时，Windows PowerShell 使用当前主机来向用户显示相应的提示。 例如，默认主机显示要求提供用户名和密码的提示时使用此特性。 但是，如果正在使用自定义主机，它定义不同的提示，则会显示该提示。

- 此特性使用的参数属性。 有关该属性的详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。

- 凭据属性定义由[System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute)类。

## <a name="see-also"></a>另请参阅

[参数的别名](./parameter-aliases.md)

[参数特性声明](./parameter-attribute-declaration.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
