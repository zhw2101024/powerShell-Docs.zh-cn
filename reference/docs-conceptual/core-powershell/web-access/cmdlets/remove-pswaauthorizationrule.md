---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="12c8a-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="12c8a-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="12c8a-104">简述</span><span class="sxs-lookup"><span data-stu-id="12c8a-104">SYNOPSIS</span></span>

<span data-ttu-id="12c8a-105">从 Windows PowerShell® Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="12c8a-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="12c8a-106">语法</span><span class="sxs-lookup"><span data-stu-id="12c8a-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="12c8a-107">ID</span><span class="sxs-lookup"><span data-stu-id="12c8a-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="12c8a-108">规则</span><span class="sxs-lookup"><span data-stu-id="12c8a-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="12c8a-109">说明</span><span class="sxs-lookup"><span data-stu-id="12c8a-109">DESCRIPTION</span></span>

<span data-ttu-id="12c8a-110">从 Windows PowerShell Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="12c8a-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="12c8a-111">参数</span><span class="sxs-lookup"><span data-stu-id="12c8a-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="12c8a-112">-Force</span><span class="sxs-lookup"><span data-stu-id="12c8a-112">-Force</span></span>

<span data-ttu-id="12c8a-113">在不提示确认的情况下运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12c8a-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="12c8a-114">默认情况下，cmdlet 在继续之前将向你确认。</span><span class="sxs-lookup"><span data-stu-id="12c8a-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="12c8a-115">别名</span><span class="sxs-lookup"><span data-stu-id="12c8a-115">Aliases</span></span>                              | <span data-ttu-id="12c8a-116">无</span><span class="sxs-lookup"><span data-stu-id="12c8a-116">none</span></span>                                 |
| <span data-ttu-id="12c8a-117">是否必需？</span><span class="sxs-lookup"><span data-stu-id="12c8a-117">Required?</span></span>                            | <span data-ttu-id="12c8a-118">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-118">false</span></span>                                |
| <span data-ttu-id="12c8a-119">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="12c8a-119">Position?</span></span>                            | <span data-ttu-id="12c8a-120">named</span><span class="sxs-lookup"><span data-stu-id="12c8a-120">named</span></span>                                |
| <span data-ttu-id="12c8a-121">默认值</span><span class="sxs-lookup"><span data-stu-id="12c8a-121">Default Value</span></span>                        | <span data-ttu-id="12c8a-122">无</span><span class="sxs-lookup"><span data-stu-id="12c8a-122">none</span></span>                                 |
| <span data-ttu-id="12c8a-123">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="12c8a-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="12c8a-124">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-124">false</span></span>                                |
| <span data-ttu-id="12c8a-125">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="12c8a-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="12c8a-126">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="12c8a-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="12c8a-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="12c8a-128">指定要删除的一个或多个规则的标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="12c8a-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="12c8a-129">别名</span><span class="sxs-lookup"><span data-stu-id="12c8a-129">Aliases</span></span>                              | <span data-ttu-id="12c8a-130">无</span><span class="sxs-lookup"><span data-stu-id="12c8a-130">none</span></span>                                 |
| <span data-ttu-id="12c8a-131">是否必需？</span><span class="sxs-lookup"><span data-stu-id="12c8a-131">Required?</span></span>                            | <span data-ttu-id="12c8a-132">true</span><span class="sxs-lookup"><span data-stu-id="12c8a-132">true</span></span>                                 |
| <span data-ttu-id="12c8a-133">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="12c8a-133">Position?</span></span>                            | <span data-ttu-id="12c8a-134">2</span><span class="sxs-lookup"><span data-stu-id="12c8a-134">2</span></span>                                    |
| <span data-ttu-id="12c8a-135">默认值</span><span class="sxs-lookup"><span data-stu-id="12c8a-135">Default Value</span></span>                        | <span data-ttu-id="12c8a-136">无</span><span class="sxs-lookup"><span data-stu-id="12c8a-136">none</span></span>                                 |
| <span data-ttu-id="12c8a-137">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="12c8a-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="12c8a-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="12c8a-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="12c8a-139">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="12c8a-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="12c8a-140">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="12c8a-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="12c8a-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="12c8a-142">指定要删除的规则。</span><span class="sxs-lookup"><span data-stu-id="12c8a-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="12c8a-143">别名</span><span class="sxs-lookup"><span data-stu-id="12c8a-143">Aliases</span></span>                              | <span data-ttu-id="12c8a-144">无</span><span class="sxs-lookup"><span data-stu-id="12c8a-144">none</span></span>                                 |
| <span data-ttu-id="12c8a-145">是否必需？</span><span class="sxs-lookup"><span data-stu-id="12c8a-145">Required?</span></span>                            | <span data-ttu-id="12c8a-146">true</span><span class="sxs-lookup"><span data-stu-id="12c8a-146">true</span></span>                                 |
| <span data-ttu-id="12c8a-147">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="12c8a-147">Position?</span></span>                            | <span data-ttu-id="12c8a-148">2</span><span class="sxs-lookup"><span data-stu-id="12c8a-148">2</span></span>                                    |
| <span data-ttu-id="12c8a-149">默认值</span><span class="sxs-lookup"><span data-stu-id="12c8a-149">Default Value</span></span>                        | <span data-ttu-id="12c8a-150">无</span><span class="sxs-lookup"><span data-stu-id="12c8a-150">none</span></span>                                 |
| <span data-ttu-id="12c8a-151">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="12c8a-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="12c8a-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="12c8a-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="12c8a-153">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="12c8a-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="12c8a-154">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="12c8a-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12c8a-155">-Confirm</span></span>

<span data-ttu-id="12c8a-156">运行 cmdlet 之前提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="12c8a-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="12c8a-157">是否必需？</span><span class="sxs-lookup"><span data-stu-id="12c8a-157">Required?</span></span>                            | <span data-ttu-id="12c8a-158">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-158">false</span></span>                                |
| <span data-ttu-id="12c8a-159">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="12c8a-159">Position?</span></span>                            | <span data-ttu-id="12c8a-160">named</span><span class="sxs-lookup"><span data-stu-id="12c8a-160">named</span></span>                                |
| <span data-ttu-id="12c8a-161">默认值</span><span class="sxs-lookup"><span data-stu-id="12c8a-161">Default Value</span></span>                        | <span data-ttu-id="12c8a-162">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-162">false</span></span>                                |
| <span data-ttu-id="12c8a-163">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="12c8a-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="12c8a-164">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-164">false</span></span>                                |
| <span data-ttu-id="12c8a-165">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="12c8a-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="12c8a-166">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="12c8a-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12c8a-167">-WhatIf</span></span>

<span data-ttu-id="12c8a-168">显示如果运行 cmdlet 则会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="12c8a-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="12c8a-169">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="12c8a-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="12c8a-170">是否必需？</span><span class="sxs-lookup"><span data-stu-id="12c8a-170">Required?</span></span>                            | <span data-ttu-id="12c8a-171">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-171">false</span></span>                                |
| <span data-ttu-id="12c8a-172">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="12c8a-172">Position?</span></span>                            | <span data-ttu-id="12c8a-173">named</span><span class="sxs-lookup"><span data-stu-id="12c8a-173">named</span></span>                                |
| <span data-ttu-id="12c8a-174">默认值</span><span class="sxs-lookup"><span data-stu-id="12c8a-174">Default Value</span></span>                        | <span data-ttu-id="12c8a-175">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-175">false</span></span>                                |
| <span data-ttu-id="12c8a-176">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="12c8a-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="12c8a-177">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-177">false</span></span>                                |
| <span data-ttu-id="12c8a-178">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="12c8a-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="12c8a-179">false</span><span class="sxs-lookup"><span data-stu-id="12c8a-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="12c8a-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="12c8a-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="12c8a-181">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="12c8a-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="12c8a-182">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="12c8a-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="12c8a-183">输入</span><span class="sxs-lookup"><span data-stu-id="12c8a-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="12c8a-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="12c8a-184">int\[\]</span></span>

<span data-ttu-id="12c8a-185">此 cmdlet 接受整数数组或接受 PswaAuthorizationRule 对象数组。</span><span class="sxs-lookup"><span data-stu-id="12c8a-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="12c8a-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="12c8a-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="12c8a-187">此 cmdlet 接受整数数组或接受 PswaAuthorizationRule 对象数组。</span><span class="sxs-lookup"><span data-stu-id="12c8a-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="12c8a-188">输出</span><span class="sxs-lookup"><span data-stu-id="12c8a-188">OUTPUTS</span></span>

<span data-ttu-id="12c8a-189">此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="12c8a-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="12c8a-190">示例</span><span class="sxs-lookup"><span data-stu-id="12c8a-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="12c8a-191">示例 1</span><span class="sxs-lookup"><span data-stu-id="12c8a-191">EXAMPLE 1</span></span>

<span data-ttu-id="12c8a-192">此示例将删除 ID 为 2 的授权规则。</span><span class="sxs-lookup"><span data-stu-id="12c8a-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="12c8a-193">示例 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="12c8a-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="12c8a-194">此示例将删除所有授权规则，并要求用户进行确认。</span><span class="sxs-lookup"><span data-stu-id="12c8a-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="12c8a-195">相关主题</span><span class="sxs-lookup"><span data-stu-id="12c8a-195">Related topics</span></span>

- [<span data-ttu-id="12c8a-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="12c8a-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="12c8a-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="12c8a-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="12c8a-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="12c8a-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="12c8a-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="12c8a-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)