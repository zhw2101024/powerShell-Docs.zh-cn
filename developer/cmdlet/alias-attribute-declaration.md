---
title: 别名属性声明 |Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855043"
---
# <a name="alias-attribute-declaration"></a>别名属性声明

Alias 特性允许用户指定不同的 cmdlet 参数名称。 别名可用于输入参数名称时，提供快捷方式或它们可以提供不同适用于不同方案的名称。

## <a name="syntax"></a>语法

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>参数

`aliasName` (String]必填。 指定一组 cmdlet 参数的逗号分隔的别名名称。

## <a name="remarks"></a>备注

- Alias 特性用于指定 cmdlet 参数时的参数属性。 有关如何声明这些属性的详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。

- 每个别名名称必须是在 cmdlet 中是唯一的。 Windows PowerShell 不会检查重复的别名名称。

- Alias 特性置于某个 cmdlet 中的每个参数的使用一次。

- Alias 特性定义由[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)类。

## <a name="see-also"></a>另请参阅

[参数的别名](./parameter-aliases.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
