---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188902"
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="e7fad-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e7fad-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="e7fad-104">简述</span><span class="sxs-lookup"><span data-stu-id="e7fad-104">SYNOPSIS</span></span>

<span data-ttu-id="e7fad-105">返回一组 Windows PowerShell® Web 访问的授权规则。</span><span class="sxs-lookup"><span data-stu-id="e7fad-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7fad-106">语法</span><span class="sxs-lookup"><span data-stu-id="e7fad-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="e7fad-107">ID</span><span class="sxs-lookup"><span data-stu-id="e7fad-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="e7fad-108">名称</span><span class="sxs-lookup"><span data-stu-id="e7fad-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="e7fad-109">说明</span><span class="sxs-lookup"><span data-stu-id="e7fad-109">DESCRIPTION</span></span>

<span data-ttu-id="e7fad-110">Get-PswaAuthorizationRule cmdlet 将返回一组 Windows PowerShell® Web 访问授权规则。</span><span class="sxs-lookup"><span data-stu-id="e7fad-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="e7fad-111">如果既没指定 Id 参数，也没指定 RuleName 参数，则此 cmdlet 将列出所有规则。</span><span class="sxs-lookup"><span data-stu-id="e7fad-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="e7fad-112">可使用 Id 参数筛选结果。</span><span class="sxs-lookup"><span data-stu-id="e7fad-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="e7fad-113">参数</span><span class="sxs-lookup"><span data-stu-id="e7fad-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="e7fad-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="e7fad-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="e7fad-115">指定此 cmdlet 应获取的规则标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="e7fad-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="e7fad-116">如果不指定任何 ID，则此 cmdlet 将返回所有授权规则。</span><span class="sxs-lookup"><span data-stu-id="e7fad-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="e7fad-117">别名</span><span class="sxs-lookup"><span data-stu-id="e7fad-117">Aliases</span></span>                              | <span data-ttu-id="e7fad-118">无</span><span class="sxs-lookup"><span data-stu-id="e7fad-118">none</span></span>                                 |
| <span data-ttu-id="e7fad-119">是否必需？</span><span class="sxs-lookup"><span data-stu-id="e7fad-119">Required?</span></span>                            | <span data-ttu-id="e7fad-120">false</span><span class="sxs-lookup"><span data-stu-id="e7fad-120">false</span></span>                                |
| <span data-ttu-id="e7fad-121">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="e7fad-121">Position?</span></span>                            | <span data-ttu-id="e7fad-122">2</span><span class="sxs-lookup"><span data-stu-id="e7fad-122">2</span></span>                                    |
| <span data-ttu-id="e7fad-123">默认值</span><span class="sxs-lookup"><span data-stu-id="e7fad-123">Default Value</span></span>                        | <span data-ttu-id="e7fad-124">无</span><span class="sxs-lookup"><span data-stu-id="e7fad-124">none</span></span>                                 |
| <span data-ttu-id="e7fad-125">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="e7fad-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e7fad-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="e7fad-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="e7fad-127">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="e7fad-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e7fad-128">false</span><span class="sxs-lookup"><span data-stu-id="e7fad-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="e7fad-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="e7fad-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="e7fad-130">指定要检索的授权规则名称。</span><span class="sxs-lookup"><span data-stu-id="e7fad-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="e7fad-131">此参数将返回与此数组中的字符串规则名称完全匹配的任何规则。</span><span class="sxs-lookup"><span data-stu-id="e7fad-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="e7fad-132">别名</span><span class="sxs-lookup"><span data-stu-id="e7fad-132">Aliases</span></span>                              | <span data-ttu-id="e7fad-133">无</span><span class="sxs-lookup"><span data-stu-id="e7fad-133">none</span></span>                                 |
| <span data-ttu-id="e7fad-134">是否必需？</span><span class="sxs-lookup"><span data-stu-id="e7fad-134">Required?</span></span>                            | <span data-ttu-id="e7fad-135">true</span><span class="sxs-lookup"><span data-stu-id="e7fad-135">true</span></span>                                 |
| <span data-ttu-id="e7fad-136">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="e7fad-136">Position?</span></span>                            | <span data-ttu-id="e7fad-137">2</span><span class="sxs-lookup"><span data-stu-id="e7fad-137">2</span></span>                                    |
| <span data-ttu-id="e7fad-138">默认值</span><span class="sxs-lookup"><span data-stu-id="e7fad-138">Default Value</span></span>                        | <span data-ttu-id="e7fad-139">无</span><span class="sxs-lookup"><span data-stu-id="e7fad-139">none</span></span>                                 |
| <span data-ttu-id="e7fad-140">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="e7fad-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e7fad-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="e7fad-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="e7fad-142">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="e7fad-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e7fad-143">false</span><span class="sxs-lookup"><span data-stu-id="e7fad-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="e7fad-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="e7fad-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="e7fad-145">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="e7fad-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="e7fad-146">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e7fad-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="e7fad-147">输入</span><span class="sxs-lookup"><span data-stu-id="e7fad-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="e7fad-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="e7fad-148">int\[\]</span></span>

<span data-ttu-id="e7fad-149">此 cmdlet 接受整数数组或字符串值数组作为输入。</span><span class="sxs-lookup"><span data-stu-id="e7fad-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="e7fad-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="e7fad-150">String\[\]</span></span>

<span data-ttu-id="e7fad-151">此 cmdlet 接受整数数组或字符串值数组作为输入。</span><span class="sxs-lookup"><span data-stu-id="e7fad-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="e7fad-152">输出</span><span class="sxs-lookup"><span data-stu-id="e7fad-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="e7fad-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="e7fad-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="e7fad-154">此 cmdlet 将生成一个 PswaAuthorizationRule 对象作为输出。</span><span class="sxs-lookup"><span data-stu-id="e7fad-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="e7fad-155">示例</span><span class="sxs-lookup"><span data-stu-id="e7fad-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="e7fad-156">示例 1</span><span class="sxs-lookup"><span data-stu-id="e7fad-156">EXAMPLE 1</span></span>

<span data-ttu-id="e7fad-157">此示例将获取所有规则。</span><span class="sxs-lookup"><span data-stu-id="e7fad-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="e7fad-158">示例 2</span><span class="sxs-lookup"><span data-stu-id="e7fad-158">EXAMPLE 2</span></span>

<span data-ttu-id="e7fad-159">此示例获取 ID 为 2 的规则。</span><span class="sxs-lookup"><span data-stu-id="e7fad-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="e7fad-160">示例 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="e7fad-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="e7fad-161">此示例介绍 cmdlet 如何从管道接受值。</span><span class="sxs-lookup"><span data-stu-id="e7fad-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="e7fad-162">使用此 cmdlet 传递规则 ID 和规则名称。</span><span class="sxs-lookup"><span data-stu-id="e7fad-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="e7fad-163">相关主题</span><span class="sxs-lookup"><span data-stu-id="e7fad-163">Related topics</span></span>

- [<span data-ttu-id="e7fad-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e7fad-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="e7fad-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e7fad-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="e7fad-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e7fad-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="e7fad-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="e7fad-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)