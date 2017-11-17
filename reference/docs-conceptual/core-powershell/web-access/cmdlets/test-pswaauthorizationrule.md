---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "测试 pswaauthorizationrule"
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="bf1a5-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bf1a5-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="bf1a5-104">简述</span><span class="sxs-lookup"><span data-stu-id="bf1a5-104">SYNOPSIS</span></span>

<span data-ttu-id="bf1a5-105">验证是否为特定用户、计算机或终结点设置了规则。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf1a5-106">语法</span><span class="sxs-lookup"><span data-stu-id="bf1a5-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="bf1a5-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="bf1a5-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="bf1a5-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="bf1a5-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="bf1a5-109">说明</span><span class="sxs-lookup"><span data-stu-id="bf1a5-109">DESCRIPTION</span></span>

<span data-ttu-id="bf1a5-110">Test-PswaAuthorizationRule 用于验证是否为特定用户、计算机或终结点设置了规则。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="bf1a5-111">此 cmdlet 还可用于测试授权规则，以验证某个特定用户、计算机或终结点的访问请求是否被授权。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="bf1a5-112">默认情况下，此 cmdlet 评估授权文件中的所有规则。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="bf1a5-113">但是，可指定一个用于测试的规则子集。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="bf1a5-114">可使用此 cmdlet 对身份验证失败进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="bf1a5-115">此 cmdlet 的参数对应于 Windows PowerShell®Web 访问登录页上的字段。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="bf1a5-116">参数</span><span class="sxs-lookup"><span data-stu-id="bf1a5-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="bf1a5-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="bf1a5-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="bf1a5-118">指定要测试的计算机的名称。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="bf1a5-119">别名</span><span class="sxs-lookup"><span data-stu-id="bf1a5-119">Aliases</span></span>                              | <span data-ttu-id="bf1a5-120">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-120">none</span></span>                                 |
| <span data-ttu-id="bf1a5-121">是否必需？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-121">Required?</span></span>                            | <span data-ttu-id="bf1a5-122">true</span><span class="sxs-lookup"><span data-stu-id="bf1a5-122">true</span></span>                                 |
| <span data-ttu-id="bf1a5-123">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-123">Position?</span></span>                            | <span data-ttu-id="bf1a5-124">2</span><span class="sxs-lookup"><span data-stu-id="bf1a5-124">2</span></span>                                    |
| <span data-ttu-id="bf1a5-125">默认值</span><span class="sxs-lookup"><span data-stu-id="bf1a5-125">Default Value</span></span>                        | <span data-ttu-id="bf1a5-126">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-126">none</span></span>                                 |
| <span data-ttu-id="bf1a5-127">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf1a5-128">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-128">false</span></span>                                |
| <span data-ttu-id="bf1a5-129">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf1a5-130">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="bf1a5-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="bf1a5-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="bf1a5-132">指定要测试的 Windows PowerShell 会话配置的名称（又称为终结点或运行空间）。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="bf1a5-133">别名</span><span class="sxs-lookup"><span data-stu-id="bf1a5-133">Aliases</span></span>                              | <span data-ttu-id="bf1a5-134">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-134">none</span></span>                                 |
| <span data-ttu-id="bf1a5-135">是否必需？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-135">Required?</span></span>                            | <span data-ttu-id="bf1a5-136">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-136">false</span></span>                                |
| <span data-ttu-id="bf1a5-137">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-137">Position?</span></span>                            | <span data-ttu-id="bf1a5-138">3</span><span class="sxs-lookup"><span data-stu-id="bf1a5-138">3</span></span>                                    |
| <span data-ttu-id="bf1a5-139">默认值</span><span class="sxs-lookup"><span data-stu-id="bf1a5-139">Default Value</span></span>                        | <span data-ttu-id="bf1a5-140">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-140">none</span></span>                                 |
| <span data-ttu-id="bf1a5-141">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf1a5-142">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-142">false</span></span>                                |
| <span data-ttu-id="bf1a5-143">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf1a5-144">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="bf1a5-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="bf1a5-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="bf1a5-146">指定要测试的连接 URI。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="bf1a5-147">别名</span><span class="sxs-lookup"><span data-stu-id="bf1a5-147">Aliases</span></span>                              | <span data-ttu-id="bf1a5-148">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-148">none</span></span>                                 |
| <span data-ttu-id="bf1a5-149">是否必需？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-149">Required?</span></span>                            | <span data-ttu-id="bf1a5-150">true</span><span class="sxs-lookup"><span data-stu-id="bf1a5-150">true</span></span>                                 |
| <span data-ttu-id="bf1a5-151">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-151">Position?</span></span>                            | <span data-ttu-id="bf1a5-152">2</span><span class="sxs-lookup"><span data-stu-id="bf1a5-152">2</span></span>                                    |
| <span data-ttu-id="bf1a5-153">默认值</span><span class="sxs-lookup"><span data-stu-id="bf1a5-153">Default Value</span></span>                        | <span data-ttu-id="bf1a5-154">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-154">none</span></span>                                 |
| <span data-ttu-id="bf1a5-155">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf1a5-156">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-156">false</span></span>                                |
| <span data-ttu-id="bf1a5-157">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf1a5-158">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="bf1a5-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="bf1a5-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="bf1a5-160">为要用于测试 Windows PowerShell Web 访问授权规则的用户帐户指定 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="bf1a5-161">如果不添加此参数，cmdlet 将使用当前登录的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="bf1a5-162">要获取 PSCredential 对象（用于以远程方式测试授权规则），请运行 [Get-Credential cmdlet](http://go.microsoft.com/fwlink/?LinkID=293936)。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="bf1a5-163">别名</span><span class="sxs-lookup"><span data-stu-id="bf1a5-163">Aliases</span></span>                              | <span data-ttu-id="bf1a5-164">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-164">none</span></span>                                 |
| <span data-ttu-id="bf1a5-165">是否必需？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-165">Required?</span></span>                            | <span data-ttu-id="bf1a5-166">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-166">false</span></span>                                |
| <span data-ttu-id="bf1a5-167">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-167">Position?</span></span>                            | <span data-ttu-id="bf1a5-168">named</span><span class="sxs-lookup"><span data-stu-id="bf1a5-168">named</span></span>                                |
| <span data-ttu-id="bf1a5-169">默认值</span><span class="sxs-lookup"><span data-stu-id="bf1a5-169">Default Value</span></span>                        | <span data-ttu-id="bf1a5-170">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-170">none</span></span>                                 |
| <span data-ttu-id="bf1a5-171">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf1a5-172">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-172">false</span></span>                                |
| <span data-ttu-id="bf1a5-173">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf1a5-174">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="bf1a5-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="bf1a5-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="bf1a5-176">指定要测试的规则子集。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="bf1a5-177">如果此参数未指定，则此 cmdlet 将针对所有授权规则进行测试。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="bf1a5-178">别名</span><span class="sxs-lookup"><span data-stu-id="bf1a5-178">Aliases</span></span>                              | <span data-ttu-id="bf1a5-179">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-179">none</span></span>                                 |
| <span data-ttu-id="bf1a5-180">是否必需？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-180">Required?</span></span>                            | <span data-ttu-id="bf1a5-181">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-181">false</span></span>                                |
| <span data-ttu-id="bf1a5-182">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-182">Position?</span></span>                            | <span data-ttu-id="bf1a5-183">named</span><span class="sxs-lookup"><span data-stu-id="bf1a5-183">named</span></span>                                |
| <span data-ttu-id="bf1a5-184">默认值</span><span class="sxs-lookup"><span data-stu-id="bf1a5-184">Default Value</span></span>                        | <span data-ttu-id="bf1a5-185">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-185">none</span></span>                                 |
| <span data-ttu-id="bf1a5-186">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf1a5-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="bf1a5-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="bf1a5-188">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf1a5-189">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="bf1a5-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="bf1a5-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="bf1a5-191">指定要测试的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="bf1a5-192">别名</span><span class="sxs-lookup"><span data-stu-id="bf1a5-192">Aliases</span></span>                              | <span data-ttu-id="bf1a5-193">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-193">none</span></span>                                 |
| <span data-ttu-id="bf1a5-194">是否必需？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-194">Required?</span></span>                            | <span data-ttu-id="bf1a5-195">true</span><span class="sxs-lookup"><span data-stu-id="bf1a5-195">true</span></span>                                 |
| <span data-ttu-id="bf1a5-196">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-196">Position?</span></span>                            | <span data-ttu-id="bf1a5-197">1</span><span class="sxs-lookup"><span data-stu-id="bf1a5-197">1</span></span>                                    |
| <span data-ttu-id="bf1a5-198">默认值</span><span class="sxs-lookup"><span data-stu-id="bf1a5-198">Default Value</span></span>                        | <span data-ttu-id="bf1a5-199">无</span><span class="sxs-lookup"><span data-stu-id="bf1a5-199">none</span></span>                                 |
| <span data-ttu-id="bf1a5-200">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf1a5-201">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-201">false</span></span>                                |
| <span data-ttu-id="bf1a5-202">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="bf1a5-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf1a5-203">false</span><span class="sxs-lookup"><span data-stu-id="bf1a5-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="bf1a5-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="bf1a5-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="bf1a5-205">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="bf1a5-206">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="bf1a5-207">输入</span><span class="sxs-lookup"><span data-stu-id="bf1a5-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="bf1a5-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="bf1a5-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="bf1a5-209">此 cmdlet 接受一组 PswaAuthorizationRule 对象作为输入。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="bf1a5-210">输出</span><span class="sxs-lookup"><span data-stu-id="bf1a5-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="bf1a5-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="bf1a5-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="bf1a5-212">此 cmdlet 生成一组 PswaAuthorizationRule 对象作为输出。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="bf1a5-213">示例</span><span class="sxs-lookup"><span data-stu-id="bf1a5-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="bf1a5-214">示例 1</span><span class="sxs-lookup"><span data-stu-id="bf1a5-214">EXAMPLE 1</span></span>

<span data-ttu-id="bf1a5-215">此示例测试所有授权规则，以显示所有允许用户 contoso\\mhanson 连接到计算机 srv2 的规则，并使用名为 test 的 Windows PowerShell 会话配置。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="bf1a5-216">示例 2</span><span class="sxs-lookup"><span data-stu-id="bf1a5-216">EXAMPLE 2</span></span>

<span data-ttu-id="bf1a5-217">此示例测试所有授权规则，以检查在用户 contoso\\mhanson 上应用了哪些授权规则。</span><span class="sxs-lookup"><span data-stu-id="bf1a5-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="bf1a5-218">相关主题</span><span class="sxs-lookup"><span data-stu-id="bf1a5-218">Related topics</span></span>

- [<span data-ttu-id="bf1a5-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bf1a5-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="bf1a5-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bf1a5-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="bf1a5-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="bf1a5-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="bf1a5-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bf1a5-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
