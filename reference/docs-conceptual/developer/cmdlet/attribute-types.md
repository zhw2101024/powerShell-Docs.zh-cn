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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364576"
---
# <a name="attribute-types"></a>属性类型

Cmdlet 属性可以按功能分组。
以下各节介绍了可用的属性，并说明了在调用特性时运行时的作用。

## <a name="cmdlet-attributes"></a>Cmdlet 属性

### <a name="cmdlet"></a>Cmdlet

将 .NET Framework 类标识为 cmdlet。
这是必需的基本属性。
有关详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。

## <a name="parameter-attributes"></a>Parameter 特性

### <a name="parameter"></a>参数

将 cmdlet 类中的公共属性标识为 cmdlet 参数。
有关详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。

### <a name="alias"></a>Alias

指定参数的一个或多个别名。
有关详细信息，请参阅[Alias 特性声明](./alias-attribute-declaration.md)。

## <a name="argument-validation-attributes"></a>参数验证特性

### <a name="validatecount"></a>ValidateCount

指定 cmdlet 参数允许的最小和最大参数数量。
有关详细信息，请参阅[ValidateCount 特性声明](./validatecount-attribute-declaration.md)。

### <a name="validatelength"></a>ValidateLength

指定 cmdlet 参数参数的最小和最大字符数。
有关详细信息，请参阅[ValidateLength 特性声明](./validatelength-attribute-declaration.md)。

### <a name="validatepattern"></a>ValidatePattern

指定 cmdlet 参数参数必须匹配的正则表达式模式。
有关详细信息，请参阅[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)。

### <a name="validaterange"></a>ValidateRange

指定 cmdlet 参数参数的最小值和最大值。
有关详细信息，请参阅[ValidateRange 特性声明](./validaterange-attribute-declaration.md)。

### <a name="validateset"></a>ValidateSet

为 cmdlet 参数参数指定一组有效值。
有关详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)
