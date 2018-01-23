---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "删除 pswaauthorizationrule"
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="b6f95-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b6f95-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="b6f95-104">简述</span><span class="sxs-lookup"><span data-stu-id="b6f95-104">SYNOPSIS</span></span>

<span data-ttu-id="b6f95-105">从 Windows PowerShell® Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="b6f95-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6f95-106">语法</span><span class="sxs-lookup"><span data-stu-id="b6f95-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="b6f95-107">ID</span><span class="sxs-lookup"><span data-stu-id="b6f95-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="b6f95-108">规则</span><span class="sxs-lookup"><span data-stu-id="b6f95-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="b6f95-109">说明</span><span class="sxs-lookup"><span data-stu-id="b6f95-109">DESCRIPTION</span></span>

<span data-ttu-id="b6f95-110">从 Windows PowerShell Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="b6f95-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="b6f95-111">参数</span><span class="sxs-lookup"><span data-stu-id="b6f95-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="b6f95-112">-Force</span><span class="sxs-lookup"><span data-stu-id="b6f95-112">-Force</span></span>

<span data-ttu-id="b6f95-113">在不提示确认的情况下运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6f95-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="b6f95-114">默认情况下，cmdlet 在继续之前将向你确认。</span><span class="sxs-lookup"><span data-stu-id="b6f95-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="b6f95-115">别名</span><span class="sxs-lookup"><span data-stu-id="b6f95-115">Aliases</span></span>                              | <span data-ttu-id="b6f95-116">无</span><span class="sxs-lookup"><span data-stu-id="b6f95-116">none</span></span>                                 |
| <span data-ttu-id="b6f95-117">是否必需？</span><span class="sxs-lookup"><span data-stu-id="b6f95-117">Required?</span></span>                            | <span data-ttu-id="b6f95-118">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-118">false</span></span>                                |
| <span data-ttu-id="b6f95-119">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="b6f95-119">Position?</span></span>                            | <span data-ttu-id="b6f95-120">named</span><span class="sxs-lookup"><span data-stu-id="b6f95-120">named</span></span>                                |
| <span data-ttu-id="b6f95-121">默认值</span><span class="sxs-lookup"><span data-stu-id="b6f95-121">Default Value</span></span>                        | <span data-ttu-id="b6f95-122">无</span><span class="sxs-lookup"><span data-stu-id="b6f95-122">none</span></span>                                 |
| <span data-ttu-id="b6f95-123">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="b6f95-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b6f95-124">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-124">false</span></span>                                |
| <span data-ttu-id="b6f95-125">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="b6f95-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b6f95-126">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="b6f95-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="b6f95-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="b6f95-128">指定要删除的一个或多个规则的标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="b6f95-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="b6f95-129">别名</span><span class="sxs-lookup"><span data-stu-id="b6f95-129">Aliases</span></span>                              | <span data-ttu-id="b6f95-130">无</span><span class="sxs-lookup"><span data-stu-id="b6f95-130">none</span></span>                                 |
| <span data-ttu-id="b6f95-131">是否必需？</span><span class="sxs-lookup"><span data-stu-id="b6f95-131">Required?</span></span>                            | <span data-ttu-id="b6f95-132">true</span><span class="sxs-lookup"><span data-stu-id="b6f95-132">true</span></span>                                 |
| <span data-ttu-id="b6f95-133">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="b6f95-133">Position?</span></span>                            | <span data-ttu-id="b6f95-134">2</span><span class="sxs-lookup"><span data-stu-id="b6f95-134">2</span></span>                                    |
| <span data-ttu-id="b6f95-135">默认值</span><span class="sxs-lookup"><span data-stu-id="b6f95-135">Default Value</span></span>                        | <span data-ttu-id="b6f95-136">无</span><span class="sxs-lookup"><span data-stu-id="b6f95-136">none</span></span>                                 |
| <span data-ttu-id="b6f95-137">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="b6f95-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b6f95-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="b6f95-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="b6f95-139">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="b6f95-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b6f95-140">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="b6f95-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="b6f95-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="b6f95-142">指定要删除的规则。</span><span class="sxs-lookup"><span data-stu-id="b6f95-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="b6f95-143">别名</span><span class="sxs-lookup"><span data-stu-id="b6f95-143">Aliases</span></span>                              | <span data-ttu-id="b6f95-144">无</span><span class="sxs-lookup"><span data-stu-id="b6f95-144">none</span></span>                                 |
| <span data-ttu-id="b6f95-145">是否必需？</span><span class="sxs-lookup"><span data-stu-id="b6f95-145">Required?</span></span>                            | <span data-ttu-id="b6f95-146">true</span><span class="sxs-lookup"><span data-stu-id="b6f95-146">true</span></span>                                 |
| <span data-ttu-id="b6f95-147">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="b6f95-147">Position?</span></span>                            | <span data-ttu-id="b6f95-148">2</span><span class="sxs-lookup"><span data-stu-id="b6f95-148">2</span></span>                                    |
| <span data-ttu-id="b6f95-149">默认值</span><span class="sxs-lookup"><span data-stu-id="b6f95-149">Default Value</span></span>                        | <span data-ttu-id="b6f95-150">无</span><span class="sxs-lookup"><span data-stu-id="b6f95-150">none</span></span>                                 |
| <span data-ttu-id="b6f95-151">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="b6f95-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b6f95-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="b6f95-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="b6f95-153">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="b6f95-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b6f95-154">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="b6f95-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b6f95-155">-Confirm</span></span>

<span data-ttu-id="b6f95-156">运行 cmdlet 之前提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="b6f95-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="b6f95-157">是否必需？</span><span class="sxs-lookup"><span data-stu-id="b6f95-157">Required?</span></span>                            | <span data-ttu-id="b6f95-158">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-158">false</span></span>                                |
| <span data-ttu-id="b6f95-159">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="b6f95-159">Position?</span></span>                            | <span data-ttu-id="b6f95-160">named</span><span class="sxs-lookup"><span data-stu-id="b6f95-160">named</span></span>                                |
| <span data-ttu-id="b6f95-161">默认值</span><span class="sxs-lookup"><span data-stu-id="b6f95-161">Default Value</span></span>                        | <span data-ttu-id="b6f95-162">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-162">false</span></span>                                |
| <span data-ttu-id="b6f95-163">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="b6f95-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b6f95-164">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-164">false</span></span>                                |
| <span data-ttu-id="b6f95-165">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="b6f95-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b6f95-166">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="b6f95-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b6f95-167">-WhatIf</span></span>

<span data-ttu-id="b6f95-168">显示如果运行 cmdlet 则会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="b6f95-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b6f95-169">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="b6f95-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="b6f95-170">是否必需？</span><span class="sxs-lookup"><span data-stu-id="b6f95-170">Required?</span></span>                            | <span data-ttu-id="b6f95-171">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-171">false</span></span>                                |
| <span data-ttu-id="b6f95-172">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="b6f95-172">Position?</span></span>                            | <span data-ttu-id="b6f95-173">named</span><span class="sxs-lookup"><span data-stu-id="b6f95-173">named</span></span>                                |
| <span data-ttu-id="b6f95-174">默认值</span><span class="sxs-lookup"><span data-stu-id="b6f95-174">Default Value</span></span>                        | <span data-ttu-id="b6f95-175">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-175">false</span></span>                                |
| <span data-ttu-id="b6f95-176">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="b6f95-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b6f95-177">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-177">false</span></span>                                |
| <span data-ttu-id="b6f95-178">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="b6f95-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b6f95-179">false</span><span class="sxs-lookup"><span data-stu-id="b6f95-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="b6f95-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b6f95-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="b6f95-181">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="b6f95-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="b6f95-182">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b6f95-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="b6f95-183">输入</span><span class="sxs-lookup"><span data-stu-id="b6f95-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="b6f95-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="b6f95-184">int\[\]</span></span>

<span data-ttu-id="b6f95-185">此 cmdlet 接受整数数组或接受 PswaAuthorizationRule 对象数组。</span><span class="sxs-lookup"><span data-stu-id="b6f95-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="b6f95-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="b6f95-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="b6f95-187">此 cmdlet 接受整数数组或接受 PswaAuthorizationRule 对象数组。</span><span class="sxs-lookup"><span data-stu-id="b6f95-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="b6f95-188">输出</span><span class="sxs-lookup"><span data-stu-id="b6f95-188">OUTPUTS</span></span>

<span data-ttu-id="b6f95-189">此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="b6f95-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="b6f95-190">示例</span><span class="sxs-lookup"><span data-stu-id="b6f95-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="b6f95-191">示例 1</span><span class="sxs-lookup"><span data-stu-id="b6f95-191">EXAMPLE 1</span></span>

<span data-ttu-id="b6f95-192">此示例将删除 ID 为 2 的授权规则。</span><span class="sxs-lookup"><span data-stu-id="b6f95-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="b6f95-193">示例 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="b6f95-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="b6f95-194">此示例将删除所有授权规则，并要求用户进行确认。</span><span class="sxs-lookup"><span data-stu-id="b6f95-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="b6f95-195">相关主题</span><span class="sxs-lookup"><span data-stu-id="b6f95-195">Related topics</span></span>

- [<span data-ttu-id="b6f95-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b6f95-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="b6f95-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b6f95-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="b6f95-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="b6f95-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="b6f95-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b6f95-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
