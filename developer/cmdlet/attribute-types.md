---
title: 属性类型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068651"
---
# <a name="attribute-types"></a>属性类型

Cmdlet 属性可以按功能分组。
以下各节描述了可用的属性，并描述调用该属性时，运行时的作用。

## <a name="cmdlet-attributes"></a>Cmdlet 属性

### <a name="cmdlet"></a>Cmdlet

将.NET Framework 类标识为一个 cmdlet。
这是必需的基本属性。
有关详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。

## <a name="parameter-attributes"></a>参数特性

### <a name="parameter"></a>参数

标识作为 cmdlet 参数在 cmdlet 类中的公共属性。
有关详细信息，请参阅[参数特性声明](./parameter-attribute-declaration.md)。

### <a name="alias"></a>Alias

指定为参数的一个或多个别名。
有关详细信息，请参阅[别名属性声明](./alias-attribute-declaration.md)。

## <a name="argument-validation-attributes"></a>参数验证属性

### <a name="validatecount"></a>ValidateCount

指定参数为 cmdlet 参数允许的最小值和最大数目。
有关详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。

### <a name="validatelength"></a>ValidateLength

指定最小和最大的 cmdlet 参数自变量的字符数。
有关详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。

### <a name="validatepattern"></a>ValidatePattern

指定 cmdlet 参数自变量必须与匹配的正则表达式模式。
有关详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。

### <a name="validaterange"></a>ValidateRange

指定 cmdlet 参数自变量的最小和最大值。
有关详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。

### <a name="validateset"></a>ValidateSet

指定一组 cmdlet 参数自变量的有效值。
有关详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)
