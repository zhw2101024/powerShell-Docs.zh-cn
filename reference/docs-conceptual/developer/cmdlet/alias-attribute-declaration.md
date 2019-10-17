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
# <a name="alias-attribute-declaration"></a><span data-ttu-id="66474-102">别名属性声明</span><span class="sxs-lookup"><span data-stu-id="66474-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="66474-103">Alias 属性允许用户为 cmdlet 参数指定不同的名称。</span><span class="sxs-lookup"><span data-stu-id="66474-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="66474-104">可以使用别名提供参数名称的快捷方式，也可以提供适用于不同方案的不同名称。</span><span class="sxs-lookup"><span data-stu-id="66474-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="66474-105">语法</span><span class="sxs-lookup"><span data-stu-id="66474-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="66474-106">参数</span><span class="sxs-lookup"><span data-stu-id="66474-106">Parameters</span></span>

<span data-ttu-id="66474-107">需要 `aliasName` （String []）。</span><span class="sxs-lookup"><span data-stu-id="66474-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="66474-108">指定 cmdlet 参数的一组以逗号分隔的别名。</span><span class="sxs-lookup"><span data-stu-id="66474-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="66474-109">备注</span><span class="sxs-lookup"><span data-stu-id="66474-109">Remarks</span></span>

- <span data-ttu-id="66474-110">当指定 cmdlet 参数时，会将 Alias 特性与参数特性一起使用。</span><span class="sxs-lookup"><span data-stu-id="66474-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="66474-111">有关如何声明这些属性的详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="66474-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="66474-112">每个别名在 cmdlet 中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="66474-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="66474-113">Windows PowerShell 不会检查是否存在重复的别名。</span><span class="sxs-lookup"><span data-stu-id="66474-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="66474-114">为 cmdlet 中的每个参数使用一次 Alias 特性。</span><span class="sxs-lookup"><span data-stu-id="66474-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="66474-115">Alias 特性是由[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)类定义的。</span><span class="sxs-lookup"><span data-stu-id="66474-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="66474-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66474-116">See Also</span></span>

[<span data-ttu-id="66474-117">参数别名</span><span class="sxs-lookup"><span data-stu-id="66474-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="66474-118">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="66474-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
