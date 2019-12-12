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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365336"
---
# <a name="outputtype-attribute-declaration"></a>OutputType 属性声明

`OutputType` 属性标识由 cmdlet、函数或脚本返回的 .NET Framework 类型。

## <a name="syntax"></a>语法

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>参数

需要键入（`string[]` 或 `Type[]`）。 指定由 cmdlet 函数或脚本返回的类型。

ParameterSetName （string []）可选。 指定返回在 `type` 参数中指定的类型的参数集。

providerCmdlet 可选。 指定提供程序 cmdlet，该 cmdlet 返回在 `type` 参数中指定的类型。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
