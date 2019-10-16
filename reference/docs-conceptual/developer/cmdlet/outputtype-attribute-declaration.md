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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365336"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="1f719-102">OutputType 属性声明</span><span class="sxs-lookup"><span data-stu-id="1f719-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="1f719-103">@No__t-0 属性标识由 cmdlet、函数或脚本返回的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="1f719-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f719-104">语法</span><span class="sxs-lookup"><span data-stu-id="1f719-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="1f719-105">参数</span><span class="sxs-lookup"><span data-stu-id="1f719-105">Parameters</span></span>

<span data-ttu-id="1f719-106">需要键入（`string[]` 或 `Type[]`）。</span><span class="sxs-lookup"><span data-stu-id="1f719-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="1f719-107">指定由 cmdlet 函数或脚本返回的类型。</span><span class="sxs-lookup"><span data-stu-id="1f719-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="1f719-108">ParameterSetName （string []）可选。</span><span class="sxs-lookup"><span data-stu-id="1f719-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="1f719-109">指定返回 `type` 参数中指定的类型的参数集。</span><span class="sxs-lookup"><span data-stu-id="1f719-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="1f719-110">providerCmdlet 可选。</span><span class="sxs-lookup"><span data-stu-id="1f719-110">providerCmdlet Optional.</span></span> <span data-ttu-id="1f719-111">指定提供程序 cmdlet，该 cmdlet 返回在 `type` 参数中指定的类型。</span><span class="sxs-lookup"><span data-stu-id="1f719-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f719-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f719-112">See Also</span></span>

[<span data-ttu-id="1f719-113">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1f719-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
