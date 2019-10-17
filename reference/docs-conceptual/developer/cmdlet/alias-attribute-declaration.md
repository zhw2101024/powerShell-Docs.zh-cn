---
title: Alias 属性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370016"
---
# <a name="alias-attribute-declaration"></a>别名属性声明

Alias 属性允许用户为 cmdlet 参数指定不同的名称。 可以使用别名提供参数名称的快捷方式，也可以提供适用于不同方案的不同名称。

## <a name="syntax"></a>语法

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>参数

需要 `aliasName` （String []）。 指定 cmdlet 参数的一组以逗号分隔的别名。

## <a name="remarks"></a>备注

- 当指定 cmdlet 参数时，会将 Alias 特性与参数特性一起使用。 有关如何声明这些属性的详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。

- 每个别名在 cmdlet 中必须是唯一的。 Windows PowerShell 不会检查是否存在重复的别名。

- 为 cmdlet 中的每个参数使用一次 Alias 特性。

- Alias 特性是由[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)类定义的。

## <a name="see-also"></a>另请参阅

[参数别名](./parameter-aliases.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
