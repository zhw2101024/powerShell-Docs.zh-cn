---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: 卸载 pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 139c8358a24e54dec630f8c78737728330ba4aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="9fa3c-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9fa3c-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="9fa3c-104">简述</span><span class="sxs-lookup"><span data-stu-id="9fa3c-104">SYNOPSIS</span></span>

<span data-ttu-id="9fa3c-105">卸载 Windows PowerShell® Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="9fa3c-106">语法</span><span class="sxs-lookup"><span data-stu-id="9fa3c-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="9fa3c-107">默认值</span><span class="sxs-lookup"><span data-stu-id="9fa3c-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="9fa3c-108">说明</span><span class="sxs-lookup"><span data-stu-id="9fa3c-108">DESCRIPTION</span></span>

<span data-ttu-id="9fa3c-109">Uninstall-PswaWebApplication cmdlet 将卸载 Windows PowerShell Web 应用程序，并从 IIS 删除该网站。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="9fa3c-110">该 cmdlet 不会卸载 IIS 或任何其他已安装的功能，因为它们是 Windows PowerShell 运行所必需的。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="9fa3c-111">参数</span><span class="sxs-lookup"><span data-stu-id="9fa3c-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="9fa3c-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="9fa3c-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="9fa3c-113">指示由 Install\_PswaWebApplication cmdlet（包含 UseTestCertificate 参数）创建的测试证书已被删除。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="9fa3c-114">仅删除与 Install-PswaWebApplication 创建的 cmdlet 具有相同名称的测试证书。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="9fa3c-115">别名</span><span class="sxs-lookup"><span data-stu-id="9fa3c-115">Aliases</span></span>                              | <span data-ttu-id="9fa3c-116">无</span><span class="sxs-lookup"><span data-stu-id="9fa3c-116">none</span></span>                                 |
| <span data-ttu-id="9fa3c-117">是否必需？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-117">Required?</span></span>                            | <span data-ttu-id="9fa3c-118">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-118">false</span></span>                                |
| <span data-ttu-id="9fa3c-119">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-119">Position?</span></span>                            | <span data-ttu-id="9fa3c-120">named</span><span class="sxs-lookup"><span data-stu-id="9fa3c-120">named</span></span>                                |
| <span data-ttu-id="9fa3c-121">默认值</span><span class="sxs-lookup"><span data-stu-id="9fa3c-121">Default Value</span></span>                        | <span data-ttu-id="9fa3c-122">true</span><span class="sxs-lookup"><span data-stu-id="9fa3c-122">true</span></span>                                 |
| <span data-ttu-id="9fa3c-123">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9fa3c-124">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-124">false</span></span>                                |
| <span data-ttu-id="9fa3c-125">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9fa3c-126">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="9fa3c-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9fa3c-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="9fa3c-128">指定要卸载的 Web 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="9fa3c-129">别名</span><span class="sxs-lookup"><span data-stu-id="9fa3c-129">Aliases</span></span>                              | <span data-ttu-id="9fa3c-130">无</span><span class="sxs-lookup"><span data-stu-id="9fa3c-130">none</span></span>                                 |
| <span data-ttu-id="9fa3c-131">是否必需？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-131">Required?</span></span>                            | <span data-ttu-id="9fa3c-132">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-132">false</span></span>                                |
| <span data-ttu-id="9fa3c-133">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-133">Position?</span></span>                            | <span data-ttu-id="9fa3c-134">1</span><span class="sxs-lookup"><span data-stu-id="9fa3c-134">1</span></span>                                    |
| <span data-ttu-id="9fa3c-135">默认值</span><span class="sxs-lookup"><span data-stu-id="9fa3c-135">Default Value</span></span>                        | <span data-ttu-id="9fa3c-136">pswa</span><span class="sxs-lookup"><span data-stu-id="9fa3c-136">pswa</span></span>                                 |
| <span data-ttu-id="9fa3c-137">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9fa3c-138">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-138">false</span></span>                                |
| <span data-ttu-id="9fa3c-139">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9fa3c-140">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="9fa3c-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9fa3c-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="9fa3c-142">指定安装 Web 应用程序的网站的名称。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="9fa3c-143">别名</span><span class="sxs-lookup"><span data-stu-id="9fa3c-143">Aliases</span></span>                              | <span data-ttu-id="9fa3c-144">无</span><span class="sxs-lookup"><span data-stu-id="9fa3c-144">none</span></span>                                 |
| <span data-ttu-id="9fa3c-145">是否必需？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-145">Required?</span></span>                            | <span data-ttu-id="9fa3c-146">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-146">false</span></span>                                |
| <span data-ttu-id="9fa3c-147">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-147">Position?</span></span>                            | <span data-ttu-id="9fa3c-148">named</span><span class="sxs-lookup"><span data-stu-id="9fa3c-148">named</span></span>                                |
| <span data-ttu-id="9fa3c-149">默认值</span><span class="sxs-lookup"><span data-stu-id="9fa3c-149">Default Value</span></span>                        | <span data-ttu-id="9fa3c-150">默认网站</span><span class="sxs-lookup"><span data-stu-id="9fa3c-150">Default Web Site</span></span>                     |
| <span data-ttu-id="9fa3c-151">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9fa3c-152">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-152">false</span></span>                                |
| <span data-ttu-id="9fa3c-153">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9fa3c-154">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="9fa3c-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9fa3c-155">-Confirm</span></span>

<span data-ttu-id="9fa3c-156">运行 cmdlet 之前提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="9fa3c-157">是否必需？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-157">Required?</span></span>                            | <span data-ttu-id="9fa3c-158">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-158">false</span></span>                                |
| <span data-ttu-id="9fa3c-159">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-159">Position?</span></span>                            | <span data-ttu-id="9fa3c-160">named</span><span class="sxs-lookup"><span data-stu-id="9fa3c-160">named</span></span>                                |
| <span data-ttu-id="9fa3c-161">默认值</span><span class="sxs-lookup"><span data-stu-id="9fa3c-161">Default Value</span></span>                        | <span data-ttu-id="9fa3c-162">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-162">false</span></span>                                |
| <span data-ttu-id="9fa3c-163">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9fa3c-164">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-164">false</span></span>                                |
| <span data-ttu-id="9fa3c-165">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9fa3c-166">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="9fa3c-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9fa3c-167">-WhatIf</span></span>

<span data-ttu-id="9fa3c-168">显示如果运行 cmdlet 则会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9fa3c-169">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="9fa3c-170">是否必需？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-170">Required?</span></span>                            | <span data-ttu-id="9fa3c-171">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-171">false</span></span>                                |
| <span data-ttu-id="9fa3c-172">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-172">Position?</span></span>                            | <span data-ttu-id="9fa3c-173">named</span><span class="sxs-lookup"><span data-stu-id="9fa3c-173">named</span></span>                                |
| <span data-ttu-id="9fa3c-174">默认值</span><span class="sxs-lookup"><span data-stu-id="9fa3c-174">Default Value</span></span>                        | <span data-ttu-id="9fa3c-175">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-175">false</span></span>                                |
| <span data-ttu-id="9fa3c-176">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9fa3c-177">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-177">false</span></span>                                |
| <span data-ttu-id="9fa3c-178">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="9fa3c-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9fa3c-179">false</span><span class="sxs-lookup"><span data-stu-id="9fa3c-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="9fa3c-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="9fa3c-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="9fa3c-181">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="9fa3c-182">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="9fa3c-183">输入</span><span class="sxs-lookup"><span data-stu-id="9fa3c-183">INPUTS</span></span>

<span data-ttu-id="9fa3c-184">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="9fa3c-185">输出</span><span class="sxs-lookup"><span data-stu-id="9fa3c-185">OUTPUTS</span></span>

<span data-ttu-id="9fa3c-186">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="9fa3c-187">示例</span><span class="sxs-lookup"><span data-stu-id="9fa3c-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="9fa3c-188">示例 1</span><span class="sxs-lookup"><span data-stu-id="9fa3c-188">EXAMPLE 1</span></span>

<span data-ttu-id="9fa3c-189">此命令将卸载 Windows PowerShell Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="9fa3c-190">如果使用了默认值来安装 Windows PowerShell Web 应用程序，则可使用此 cmdlet 对其进行卸载。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="9fa3c-191">示例 2</span><span class="sxs-lookup"><span data-stu-id="9fa3c-191">EXAMPLE 2</span></span>

<span data-ttu-id="9fa3c-192">此命令将卸载 Windows PowerShell Web 应用程序，并删除与该应用程序相关联的测试证书。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="9fa3c-193">如果使用了默认值来安装 Windows PowerShell Web 应用程序并创建了测试证书，则可使用此 cmdlet 对其进行卸载。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="9fa3c-194">示例 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="9fa3c-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="9fa3c-195">如果在安装过程中指定了自定义网站和应用程序，此命令将卸载 Windows PowerShell Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="9fa3c-196">该命令将删除名为 MySite 的网站及名为 TestApplication 的应用程序，并指定删除与该应用程序相关联的测试证书。</span><span class="sxs-lookup"><span data-stu-id="9fa3c-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="9fa3c-197">相关主题</span><span class="sxs-lookup"><span data-stu-id="9fa3c-197">Related topics</span></span>

- [<span data-ttu-id="9fa3c-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9fa3c-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="9fa3c-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9fa3c-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="9fa3c-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9fa3c-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="9fa3c-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9fa3c-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="9fa3c-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9fa3c-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)