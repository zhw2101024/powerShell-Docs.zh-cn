---
title: OutputType 特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067597"
---
# <a name="outputtype-attribute-declaration"></a>OutputType 属性声明

`OutputType`属性标识的 cmdlet、 函数或脚本返回的.NET Framework 类型。

## <a name="syntax"></a>语法

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>参数

类型 (`string[]`或`Type[]`) 所需。 指定 cmdlet 函数或脚本返回的类型。

ParameterSetName (string [] 可选。 指定返回类型中指定的参数集`type`参数。

providerCmdlet 可选。 指定返回类型中指定的提供程序 cmdlet`type`参数。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
