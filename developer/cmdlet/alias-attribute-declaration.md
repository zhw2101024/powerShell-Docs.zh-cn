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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068703"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="83118-102">别名属性声明</span><span class="sxs-lookup"><span data-stu-id="83118-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="83118-103">Alias 特性允许用户指定不同的 cmdlet 参数名称。</span><span class="sxs-lookup"><span data-stu-id="83118-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="83118-104">别名可用于输入参数名称时，提供快捷方式或它们可以提供不同适用于不同方案的名称。</span><span class="sxs-lookup"><span data-stu-id="83118-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="83118-105">语法</span><span class="sxs-lookup"><span data-stu-id="83118-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="83118-106">参数</span><span class="sxs-lookup"><span data-stu-id="83118-106">Parameters</span></span>

<span data-ttu-id="83118-107">`aliasName` (String]必填。</span><span class="sxs-lookup"><span data-stu-id="83118-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="83118-108">指定一组 cmdlet 参数的逗号分隔的别名名称。</span><span class="sxs-lookup"><span data-stu-id="83118-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="83118-109">备注</span><span class="sxs-lookup"><span data-stu-id="83118-109">Remarks</span></span>

- <span data-ttu-id="83118-110">Alias 特性用于指定 cmdlet 参数时的参数属性。</span><span class="sxs-lookup"><span data-stu-id="83118-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="83118-111">有关如何声明这些属性的详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="83118-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="83118-112">每个别名名称必须是在 cmdlet 中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="83118-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="83118-113">Windows PowerShell 不会检查重复的别名名称。</span><span class="sxs-lookup"><span data-stu-id="83118-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="83118-114">Alias 特性置于某个 cmdlet 中的每个参数的使用一次。</span><span class="sxs-lookup"><span data-stu-id="83118-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="83118-115">Alias 特性定义由[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="83118-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="83118-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83118-116">See Also</span></span>

[<span data-ttu-id="83118-117">参数的别名</span><span class="sxs-lookup"><span data-stu-id="83118-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="83118-118">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="83118-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
