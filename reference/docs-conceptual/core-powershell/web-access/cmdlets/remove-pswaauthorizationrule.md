---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: 删除 pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 28dbfe84827d6ccb99dce1ebb520cae66dc8c50e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="02c39-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="02c39-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="02c39-104">简述</span><span class="sxs-lookup"><span data-stu-id="02c39-104">SYNOPSIS</span></span>

<span data-ttu-id="02c39-105">从 Windows PowerShell® Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="02c39-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="02c39-106">语法</span><span class="sxs-lookup"><span data-stu-id="02c39-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="02c39-107">ID</span><span class="sxs-lookup"><span data-stu-id="02c39-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="02c39-108">规则</span><span class="sxs-lookup"><span data-stu-id="02c39-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="02c39-109">说明</span><span class="sxs-lookup"><span data-stu-id="02c39-109">DESCRIPTION</span></span>

<span data-ttu-id="02c39-110">从 Windows PowerShell Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="02c39-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="02c39-111">参数</span><span class="sxs-lookup"><span data-stu-id="02c39-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="02c39-112">-Force</span><span class="sxs-lookup"><span data-stu-id="02c39-112">-Force</span></span>

<span data-ttu-id="02c39-113">在不提示确认的情况下运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="02c39-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="02c39-114">默认情况下，cmdlet 在继续之前将向你确认。</span><span class="sxs-lookup"><span data-stu-id="02c39-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="02c39-115">别名</span><span class="sxs-lookup"><span data-stu-id="02c39-115">Aliases</span></span>                              | <span data-ttu-id="02c39-116">无</span><span class="sxs-lookup"><span data-stu-id="02c39-116">none</span></span>                                 |
| <span data-ttu-id="02c39-117">是否必需？</span><span class="sxs-lookup"><span data-stu-id="02c39-117">Required?</span></span>                            | <span data-ttu-id="02c39-118">false</span><span class="sxs-lookup"><span data-stu-id="02c39-118">false</span></span>                                |
| <span data-ttu-id="02c39-119">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="02c39-119">Position?</span></span>                            | <span data-ttu-id="02c39-120">named</span><span class="sxs-lookup"><span data-stu-id="02c39-120">named</span></span>                                |
| <span data-ttu-id="02c39-121">默认值</span><span class="sxs-lookup"><span data-stu-id="02c39-121">Default Value</span></span>                        | <span data-ttu-id="02c39-122">无</span><span class="sxs-lookup"><span data-stu-id="02c39-122">none</span></span>                                 |
| <span data-ttu-id="02c39-123">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="02c39-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="02c39-124">false</span><span class="sxs-lookup"><span data-stu-id="02c39-124">false</span></span>                                |
| <span data-ttu-id="02c39-125">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="02c39-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="02c39-126">false</span><span class="sxs-lookup"><span data-stu-id="02c39-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="02c39-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="02c39-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="02c39-128">指定要删除的一个或多个规则的标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="02c39-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="02c39-129">别名</span><span class="sxs-lookup"><span data-stu-id="02c39-129">Aliases</span></span>                              | <span data-ttu-id="02c39-130">无</span><span class="sxs-lookup"><span data-stu-id="02c39-130">none</span></span>                                 |
| <span data-ttu-id="02c39-131">是否必需？</span><span class="sxs-lookup"><span data-stu-id="02c39-131">Required?</span></span>                            | <span data-ttu-id="02c39-132">true</span><span class="sxs-lookup"><span data-stu-id="02c39-132">true</span></span>                                 |
| <span data-ttu-id="02c39-133">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="02c39-133">Position?</span></span>                            | <span data-ttu-id="02c39-134">2</span><span class="sxs-lookup"><span data-stu-id="02c39-134">2</span></span>                                    |
| <span data-ttu-id="02c39-135">默认值</span><span class="sxs-lookup"><span data-stu-id="02c39-135">Default Value</span></span>                        | <span data-ttu-id="02c39-136">无</span><span class="sxs-lookup"><span data-stu-id="02c39-136">none</span></span>                                 |
| <span data-ttu-id="02c39-137">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="02c39-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="02c39-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="02c39-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="02c39-139">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="02c39-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="02c39-140">false</span><span class="sxs-lookup"><span data-stu-id="02c39-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="02c39-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="02c39-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="02c39-142">指定要删除的规则。</span><span class="sxs-lookup"><span data-stu-id="02c39-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="02c39-143">别名</span><span class="sxs-lookup"><span data-stu-id="02c39-143">Aliases</span></span>                              | <span data-ttu-id="02c39-144">无</span><span class="sxs-lookup"><span data-stu-id="02c39-144">none</span></span>                                 |
| <span data-ttu-id="02c39-145">是否必需？</span><span class="sxs-lookup"><span data-stu-id="02c39-145">Required?</span></span>                            | <span data-ttu-id="02c39-146">true</span><span class="sxs-lookup"><span data-stu-id="02c39-146">true</span></span>                                 |
| <span data-ttu-id="02c39-147">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="02c39-147">Position?</span></span>                            | <span data-ttu-id="02c39-148">2</span><span class="sxs-lookup"><span data-stu-id="02c39-148">2</span></span>                                    |
| <span data-ttu-id="02c39-149">默认值</span><span class="sxs-lookup"><span data-stu-id="02c39-149">Default Value</span></span>                        | <span data-ttu-id="02c39-150">无</span><span class="sxs-lookup"><span data-stu-id="02c39-150">none</span></span>                                 |
| <span data-ttu-id="02c39-151">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="02c39-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="02c39-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="02c39-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="02c39-153">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="02c39-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="02c39-154">false</span><span class="sxs-lookup"><span data-stu-id="02c39-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="02c39-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="02c39-155">-Confirm</span></span>

<span data-ttu-id="02c39-156">运行 cmdlet 之前提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="02c39-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="02c39-157">是否必需？</span><span class="sxs-lookup"><span data-stu-id="02c39-157">Required?</span></span>                            | <span data-ttu-id="02c39-158">false</span><span class="sxs-lookup"><span data-stu-id="02c39-158">false</span></span>                                |
| <span data-ttu-id="02c39-159">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="02c39-159">Position?</span></span>                            | <span data-ttu-id="02c39-160">named</span><span class="sxs-lookup"><span data-stu-id="02c39-160">named</span></span>                                |
| <span data-ttu-id="02c39-161">默认值</span><span class="sxs-lookup"><span data-stu-id="02c39-161">Default Value</span></span>                        | <span data-ttu-id="02c39-162">false</span><span class="sxs-lookup"><span data-stu-id="02c39-162">false</span></span>                                |
| <span data-ttu-id="02c39-163">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="02c39-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="02c39-164">false</span><span class="sxs-lookup"><span data-stu-id="02c39-164">false</span></span>                                |
| <span data-ttu-id="02c39-165">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="02c39-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="02c39-166">false</span><span class="sxs-lookup"><span data-stu-id="02c39-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="02c39-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="02c39-167">-WhatIf</span></span>

<span data-ttu-id="02c39-168">显示如果运行 cmdlet 则会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="02c39-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="02c39-169">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="02c39-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="02c39-170">是否必需？</span><span class="sxs-lookup"><span data-stu-id="02c39-170">Required?</span></span>                            | <span data-ttu-id="02c39-171">false</span><span class="sxs-lookup"><span data-stu-id="02c39-171">false</span></span>                                |
| <span data-ttu-id="02c39-172">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="02c39-172">Position?</span></span>                            | <span data-ttu-id="02c39-173">named</span><span class="sxs-lookup"><span data-stu-id="02c39-173">named</span></span>                                |
| <span data-ttu-id="02c39-174">默认值</span><span class="sxs-lookup"><span data-stu-id="02c39-174">Default Value</span></span>                        | <span data-ttu-id="02c39-175">false</span><span class="sxs-lookup"><span data-stu-id="02c39-175">false</span></span>                                |
| <span data-ttu-id="02c39-176">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="02c39-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="02c39-177">false</span><span class="sxs-lookup"><span data-stu-id="02c39-177">false</span></span>                                |
| <span data-ttu-id="02c39-178">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="02c39-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="02c39-179">false</span><span class="sxs-lookup"><span data-stu-id="02c39-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="02c39-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="02c39-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="02c39-181">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="02c39-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="02c39-182">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="02c39-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="02c39-183">输入</span><span class="sxs-lookup"><span data-stu-id="02c39-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="02c39-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="02c39-184">int\[\]</span></span>

<span data-ttu-id="02c39-185">此 cmdlet 接受整数数组或接受 PswaAuthorizationRule 对象数组。</span><span class="sxs-lookup"><span data-stu-id="02c39-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="02c39-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="02c39-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="02c39-187">此 cmdlet 接受整数数组或接受 PswaAuthorizationRule 对象数组。</span><span class="sxs-lookup"><span data-stu-id="02c39-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="02c39-188">输出</span><span class="sxs-lookup"><span data-stu-id="02c39-188">OUTPUTS</span></span>

<span data-ttu-id="02c39-189">此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="02c39-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="02c39-190">示例</span><span class="sxs-lookup"><span data-stu-id="02c39-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="02c39-191">示例 1</span><span class="sxs-lookup"><span data-stu-id="02c39-191">EXAMPLE 1</span></span>

<span data-ttu-id="02c39-192">此示例将删除 ID 为 2 的授权规则。</span><span class="sxs-lookup"><span data-stu-id="02c39-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="02c39-193">示例 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="02c39-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="02c39-194">此示例将删除所有授权规则，并要求用户进行确认。</span><span class="sxs-lookup"><span data-stu-id="02c39-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="02c39-195">相关主题</span><span class="sxs-lookup"><span data-stu-id="02c39-195">Related topics</span></span>

- [<span data-ttu-id="02c39-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="02c39-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="02c39-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="02c39-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="02c39-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="02c39-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="02c39-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="02c39-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)