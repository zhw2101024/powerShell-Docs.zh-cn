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
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853843"
---
# <a name="cmdlet-parameters"></a>Cmdlet 参数

Cmdlet 参数提供的机制，用于接受输入的 cmdlet。 参数可以接受输入直接从命令行中，或通过管道参数传递给 cmdlet 的对象 (也称为*值*) 的这些参数可以指定该 cmdlet 接受，输入方式cmdlet 应执行的操作，以及该 cmdlet 将返回到管道的数据。

## <a name="in-this-section"></a>本节内容

[声明属性作为参数](./declaring-properties-as-parameters.md)提供声明的参数的 cmdlet 之前，您必须了解的基本信息。

[Cmdlet 参数的类型](./types-of-cmdlet-parameters.md)介绍不同类型的参数可以声明在 cmdlet 中。

[Cmdlet 参数名称和功能的指导原则](./standard-cmdlet-parameter-names-and-types.md)Discuses 名称，建议的数据类型和功能的标准参数。

[参数别名](./parameter-aliases.md)讨论你可以为参数定义的别名。

[常见的参数名称](./common-parameter-names.md)本主题介绍 Windows PowerShell 将添加到 cmdlet 的参数。

[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)讨论了如何参数集，您可以编写的单个 cmdlet，可以执行不同的操作为不同的方案。

[Cmdlet 的动态参数](./cmdlet-dynamic-parameters.md)讨论了可供用户在特殊情况下的参数。

[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)介绍如何设计一个 cmdlet，将针对资源组的运行时的通配符字符提供支持。

[验证参数输入](./validating-parameter-input.md)描述了 Windows PowerShell 如何验证传递给 cmdlet 参数的参数。

[输入筛选器参数](./input-filter-parameters.md)讨论`Filter`， `Include`，和`Exclude`筛选会影响该 cmdlet 的输入对象的集合的参数。

## <a name="related-sections"></a>相关章节

[如何验证参数输入](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>另请参阅

[参数特性声明](./parameter-attribute-declaration.md)

[Windows PowerShell Cmdlets](./cmdlet-overview.md)
