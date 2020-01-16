---
title: Cmdlet 参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: c1d8984f4aad7bae6f9be66a2222e2c74c8afa3d
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022204"
---
# <a name="cmdlet-parameters"></a>Cmdlet 参数

Cmdlet 参数提供允许 cmdlet 接受输入的机制。 参数可以直接从命令行进行输入，也可以从通过管道传递给 cmdlet 的对象接受输入，这些参数的参数（也称为*值*）可以指定 cmdlet 接受的输入、cmdlet 应如何执行其操作以及 cmdlet 返回到管道的数据。

## <a name="in-this-section"></a>本部分内容

将[属性声明为参数](./declaring-properties-as-parameters.md)提供在声明 cmdlet 参数之前必须了解的基本信息。

[Cmdlet 参数的类型](./types-of-cmdlet-parameters.md)描述可在 cmdlet 中声明的不同类型的参数。

[Cmdlet 参数名称和功能指导原则](./standard-cmdlet-parameter-names-and-types.md)讨论了标准参数的名称、建议的数据类型和功能。

[参数别名](./parameter-aliases.md)讨论可以为参数定义的别名。

[常见参数名称](./common-parameter-names.md)本主题介绍 Windows PowerShell 添加到 cmdlet 的参数。

[Cmdlet 参数集](./cmdlet-parameter-sets.md)讨论如何使用参数集编写单个 cmdlet，该 cmdlet 可以针对不同的方案执行不同的操作。

[Cmdlet 动态参数](./cmdlet-dynamic-parameters.md)讨论在特殊条件下可用于用户的参数。

[支持 Cmdlet 参数中的通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)描述在设计将针对一组资源运行的 cmdlet 时，如何提供对通配符字符的支持。

[正在验证参数输入](./validating-parameter-input.md)介绍 Windows PowerShell 如何验证传递给 cmdlet 参数的参数。

[输入筛选器参数](./input-filter-parameters.md)讨论 `Filter`、`Include`和 `Exclude` 参数，这些参数用于筛选 cmdlet 影响的输入对象集。

## <a name="related-sections"></a>相关章节

[如何验证参数输入](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>另请参阅

[参数属性声明](./parameter-attribute-declaration.md)

[Windows PowerShell Cmdlet](./cmdlet-overview.md)
