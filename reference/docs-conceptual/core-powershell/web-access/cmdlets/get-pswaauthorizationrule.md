---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "获取 pswaauthorizationrule"
ms.technology: powershell
ms.openlocfilehash: 003195457660a18b9bbed065181b6d8c23835348
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="1478e-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1478e-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="1478e-104">简述</span><span class="sxs-lookup"><span data-stu-id="1478e-104">SYNOPSIS</span></span>

<span data-ttu-id="1478e-105">返回一组 Windows PowerShell® Web 访问的授权规则。</span><span class="sxs-lookup"><span data-stu-id="1478e-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="1478e-106">语法</span><span class="sxs-lookup"><span data-stu-id="1478e-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="1478e-107">ID</span><span class="sxs-lookup"><span data-stu-id="1478e-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="1478e-108">名称</span><span class="sxs-lookup"><span data-stu-id="1478e-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="1478e-109">说明</span><span class="sxs-lookup"><span data-stu-id="1478e-109">DESCRIPTION</span></span>

<span data-ttu-id="1478e-110">Get-PswaAuthorizationRule cmdlet 将返回一组 Windows PowerShell® Web 访问授权规则。</span><span class="sxs-lookup"><span data-stu-id="1478e-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="1478e-111">如果既没指定 Id 参数，也没指定 RuleName 参数，则此 cmdlet 将列出所有规则。</span><span class="sxs-lookup"><span data-stu-id="1478e-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="1478e-112">可使用 Id 参数筛选结果。</span><span class="sxs-lookup"><span data-stu-id="1478e-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="1478e-113">参数</span><span class="sxs-lookup"><span data-stu-id="1478e-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="1478e-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1478e-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="1478e-115">指定此 cmdlet 应获取的规则标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="1478e-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="1478e-116">如果不指定任何 ID，则此 cmdlet 将返回所有授权规则。</span><span class="sxs-lookup"><span data-stu-id="1478e-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="1478e-117">别名</span><span class="sxs-lookup"><span data-stu-id="1478e-117">Aliases</span></span>                              | <span data-ttu-id="1478e-118">无</span><span class="sxs-lookup"><span data-stu-id="1478e-118">none</span></span>                                 |
| <span data-ttu-id="1478e-119">是否必需？</span><span class="sxs-lookup"><span data-stu-id="1478e-119">Required?</span></span>                            | <span data-ttu-id="1478e-120">false</span><span class="sxs-lookup"><span data-stu-id="1478e-120">false</span></span>                                |
| <span data-ttu-id="1478e-121">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="1478e-121">Position?</span></span>                            | <span data-ttu-id="1478e-122">2</span><span class="sxs-lookup"><span data-stu-id="1478e-122">2</span></span>                                    |
| <span data-ttu-id="1478e-123">默认值</span><span class="sxs-lookup"><span data-stu-id="1478e-123">Default Value</span></span>                        | <span data-ttu-id="1478e-124">无</span><span class="sxs-lookup"><span data-stu-id="1478e-124">none</span></span>                                 |
| <span data-ttu-id="1478e-125">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="1478e-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1478e-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1478e-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="1478e-127">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="1478e-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1478e-128">false</span><span class="sxs-lookup"><span data-stu-id="1478e-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="1478e-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1478e-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="1478e-130">指定要检索的授权规则名称。</span><span class="sxs-lookup"><span data-stu-id="1478e-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="1478e-131">此参数将返回与此数组中的字符串规则名称完全匹配的任何规则。</span><span class="sxs-lookup"><span data-stu-id="1478e-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="1478e-132">别名</span><span class="sxs-lookup"><span data-stu-id="1478e-132">Aliases</span></span>                              | <span data-ttu-id="1478e-133">无</span><span class="sxs-lookup"><span data-stu-id="1478e-133">none</span></span>                                 |
| <span data-ttu-id="1478e-134">是否必需？</span><span class="sxs-lookup"><span data-stu-id="1478e-134">Required?</span></span>                            | <span data-ttu-id="1478e-135">true</span><span class="sxs-lookup"><span data-stu-id="1478e-135">true</span></span>                                 |
| <span data-ttu-id="1478e-136">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="1478e-136">Position?</span></span>                            | <span data-ttu-id="1478e-137">2</span><span class="sxs-lookup"><span data-stu-id="1478e-137">2</span></span>                                    |
| <span data-ttu-id="1478e-138">默认值</span><span class="sxs-lookup"><span data-stu-id="1478e-138">Default Value</span></span>                        | <span data-ttu-id="1478e-139">无</span><span class="sxs-lookup"><span data-stu-id="1478e-139">none</span></span>                                 |
| <span data-ttu-id="1478e-140">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="1478e-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1478e-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1478e-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="1478e-142">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="1478e-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1478e-143">false</span><span class="sxs-lookup"><span data-stu-id="1478e-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="1478e-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1478e-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="1478e-145">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="1478e-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="1478e-146">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="1478e-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="1478e-147">输入</span><span class="sxs-lookup"><span data-stu-id="1478e-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="1478e-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="1478e-148">int\[\]</span></span>

<span data-ttu-id="1478e-149">此 cmdlet 接受整数数组或字符串值数组作为输入。</span><span class="sxs-lookup"><span data-stu-id="1478e-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="1478e-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="1478e-150">String\[\]</span></span>

<span data-ttu-id="1478e-151">此 cmdlet 接受整数数组或字符串值数组作为输入。</span><span class="sxs-lookup"><span data-stu-id="1478e-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="1478e-152">输出</span><span class="sxs-lookup"><span data-stu-id="1478e-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="1478e-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="1478e-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="1478e-154">此 cmdlet 将生成一个 PswaAuthorizationRule 对象作为输出。</span><span class="sxs-lookup"><span data-stu-id="1478e-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="1478e-155">示例</span><span class="sxs-lookup"><span data-stu-id="1478e-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="1478e-156">示例 1</span><span class="sxs-lookup"><span data-stu-id="1478e-156">EXAMPLE 1</span></span>

<span data-ttu-id="1478e-157">此示例将获取所有规则。</span><span class="sxs-lookup"><span data-stu-id="1478e-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="1478e-158">示例 2</span><span class="sxs-lookup"><span data-stu-id="1478e-158">EXAMPLE 2</span></span>

<span data-ttu-id="1478e-159">此示例获取 ID 为 2 的规则。</span><span class="sxs-lookup"><span data-stu-id="1478e-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="1478e-160">示例 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="1478e-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="1478e-161">此示例介绍 cmdlet 如何从管道接受值。</span><span class="sxs-lookup"><span data-stu-id="1478e-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="1478e-162">使用此 cmdlet 传递规则 ID 和规则名称。</span><span class="sxs-lookup"><span data-stu-id="1478e-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="1478e-163">相关主题</span><span class="sxs-lookup"><span data-stu-id="1478e-163">Related topics</span></span>

- [<span data-ttu-id="1478e-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1478e-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="1478e-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1478e-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="1478e-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1478e-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="1478e-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="1478e-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
