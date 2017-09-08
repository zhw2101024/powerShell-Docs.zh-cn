---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "安装 pswawebapplication"
ms.technology: powershell
ms.openlocfilehash: c15215935eb70f082d13b93a0bf040aaf00a04de
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
#  <a name="install-pswawebapplication"></a><span data-ttu-id="33829-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="33829-103">Install-PswaWebApplication</span></span>

##  <a name="synopsis"></a><span data-ttu-id="33829-104">简述</span><span class="sxs-lookup"><span data-stu-id="33829-104">SYNOPSIS</span></span>

<span data-ttu-id="33829-105">在 IIS 中配置 Windows PowerShell® Web 访问 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="33829-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="33829-106">语法</span><span class="sxs-lookup"><span data-stu-id="33829-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="33829-107">默认值</span><span class="sxs-lookup"><span data-stu-id="33829-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="33829-108">说明</span><span class="sxs-lookup"><span data-stu-id="33829-108">DESCRIPTION</span></span>

<span data-ttu-id="33829-109">使用 Install-PswaWebApplication cmdlet 来配置 Windows PowerShell Web 访问 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="33829-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="33829-110">此 cmdlet 用于安装 Web 应用程序，并将其与网站相关联，可选择使用 useTestCertificate 参数创建测试 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="33829-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="33829-111">出于安全考虑，Web 管理员不应在生产环境中使用测试证书。</span><span class="sxs-lookup"><span data-stu-id="33829-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="33829-112">参数</span><span class="sxs-lookup"><span data-stu-id="33829-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="33829-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="33829-113">-UseTestCertificate</span></span>

<span data-ttu-id="33829-114">指定已创建测试证书。</span><span class="sxs-lookup"><span data-stu-id="33829-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="33829-115">如果将此参数设置为 true，则此 cmdlet 将创建一个测试证书，并配置 Windows PowerShell Web 访问 Web 应用程序，以使用 HTTPS 请求的证书。</span><span class="sxs-lookup"><span data-stu-id="33829-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="33829-116">如果将此参数设置为 false，则不会创建任何证书或绑定。</span><span class="sxs-lookup"><span data-stu-id="33829-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="33829-117">如果 Windows PowerShell Web 访问使用了另一证书，则将此值设置为 false。</span><span class="sxs-lookup"><span data-stu-id="33829-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="33829-118">别名</span><span class="sxs-lookup"><span data-stu-id="33829-118">Aliases</span></span>                              | <span data-ttu-id="33829-119">无</span><span class="sxs-lookup"><span data-stu-id="33829-119">none</span></span>                                 |
| <span data-ttu-id="33829-120">是否必需？</span><span class="sxs-lookup"><span data-stu-id="33829-120">Required?</span></span>                            | <span data-ttu-id="33829-121">false</span><span class="sxs-lookup"><span data-stu-id="33829-121">false</span></span>                                |
| <span data-ttu-id="33829-122">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="33829-122">Position?</span></span>                            | <span data-ttu-id="33829-123">named</span><span class="sxs-lookup"><span data-stu-id="33829-123">named</span></span>                                |
| <span data-ttu-id="33829-124">默认值</span><span class="sxs-lookup"><span data-stu-id="33829-124">Default Value</span></span>                        | <span data-ttu-id="33829-125">true</span><span class="sxs-lookup"><span data-stu-id="33829-125">true</span></span>                                 |
| <span data-ttu-id="33829-126">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="33829-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="33829-127">false</span><span class="sxs-lookup"><span data-stu-id="33829-127">false</span></span>                                |
| <span data-ttu-id="33829-128">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="33829-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="33829-129">false</span><span class="sxs-lookup"><span data-stu-id="33829-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="33829-130">-WebApplicationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="33829-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="33829-131">指定 Web 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="33829-131">Specifies the name for your web application.</span></span> <span data-ttu-id="33829-132">该名称将显示在 Windows PowerShell Web 访问 URL 的末尾。</span><span class="sxs-lookup"><span data-stu-id="33829-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="33829-133">别名</span><span class="sxs-lookup"><span data-stu-id="33829-133">Aliases</span></span>                              | <span data-ttu-id="33829-134">无</span><span class="sxs-lookup"><span data-stu-id="33829-134">none</span></span>                                 |
| <span data-ttu-id="33829-135">是否必需？</span><span class="sxs-lookup"><span data-stu-id="33829-135">Required?</span></span>                            | <span data-ttu-id="33829-136">false</span><span class="sxs-lookup"><span data-stu-id="33829-136">false</span></span>                                |
| <span data-ttu-id="33829-137">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="33829-137">Position?</span></span>                            | <span data-ttu-id="33829-138">1</span><span class="sxs-lookup"><span data-stu-id="33829-138">1</span></span>                                    |
| <span data-ttu-id="33829-139">默认值</span><span class="sxs-lookup"><span data-stu-id="33829-139">Default Value</span></span>                        | <span data-ttu-id="33829-140">pswa</span><span class="sxs-lookup"><span data-stu-id="33829-140">pswa</span></span>                                 |
| <span data-ttu-id="33829-141">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="33829-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="33829-142">false</span><span class="sxs-lookup"><span data-stu-id="33829-142">false</span></span>                                |
| <span data-ttu-id="33829-143">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="33829-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="33829-144">false</span><span class="sxs-lookup"><span data-stu-id="33829-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="33829-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="33829-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="33829-146">指定要在其上安装此 Windows PowerShell Web 访问 Web 应用程序的 Web 服务器 (IIS) 网站名称。</span><span class="sxs-lookup"><span data-stu-id="33829-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="33829-147">别名</span><span class="sxs-lookup"><span data-stu-id="33829-147">Aliases</span></span>                              | <span data-ttu-id="33829-148">无</span><span class="sxs-lookup"><span data-stu-id="33829-148">none</span></span>                                 |
| <span data-ttu-id="33829-149">是否必需？</span><span class="sxs-lookup"><span data-stu-id="33829-149">Required?</span></span>                            | <span data-ttu-id="33829-150">false</span><span class="sxs-lookup"><span data-stu-id="33829-150">false</span></span>                                |
| <span data-ttu-id="33829-151">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="33829-151">Position?</span></span>                            | <span data-ttu-id="33829-152">named</span><span class="sxs-lookup"><span data-stu-id="33829-152">named</span></span>                                |
| <span data-ttu-id="33829-153">默认值</span><span class="sxs-lookup"><span data-stu-id="33829-153">Default Value</span></span>                        | <span data-ttu-id="33829-154">默认网站</span><span class="sxs-lookup"><span data-stu-id="33829-154">Default Web Site</span></span>                     |
| <span data-ttu-id="33829-155">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="33829-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="33829-156">false</span><span class="sxs-lookup"><span data-stu-id="33829-156">false</span></span>                                |
| <span data-ttu-id="33829-157">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="33829-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="33829-158">false</span><span class="sxs-lookup"><span data-stu-id="33829-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="33829-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="33829-159">-Confirm</span></span>

<span data-ttu-id="33829-160">运行 cmdlet 之前提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="33829-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="33829-161">是否必需？</span><span class="sxs-lookup"><span data-stu-id="33829-161">Required?</span></span>                            | <span data-ttu-id="33829-162">false</span><span class="sxs-lookup"><span data-stu-id="33829-162">false</span></span>                                |
| <span data-ttu-id="33829-163">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="33829-163">Position?</span></span>                            | <span data-ttu-id="33829-164">named</span><span class="sxs-lookup"><span data-stu-id="33829-164">named</span></span>                                |
| <span data-ttu-id="33829-165">默认值</span><span class="sxs-lookup"><span data-stu-id="33829-165">Default Value</span></span>                        | <span data-ttu-id="33829-166">false</span><span class="sxs-lookup"><span data-stu-id="33829-166">false</span></span>                                |
| <span data-ttu-id="33829-167">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="33829-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="33829-168">false</span><span class="sxs-lookup"><span data-stu-id="33829-168">false</span></span>                                |
| <span data-ttu-id="33829-169">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="33829-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="33829-170">false</span><span class="sxs-lookup"><span data-stu-id="33829-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="33829-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="33829-171">-WhatIf</span></span>

<span data-ttu-id="33829-172">显示如果运行 cmdlet 则会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="33829-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="33829-173">cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="33829-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="33829-174">是否必需？</span><span class="sxs-lookup"><span data-stu-id="33829-174">Required?</span></span>                            | <span data-ttu-id="33829-175">false</span><span class="sxs-lookup"><span data-stu-id="33829-175">false</span></span>                                |
| <span data-ttu-id="33829-176">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="33829-176">Position?</span></span>                            | <span data-ttu-id="33829-177">named</span><span class="sxs-lookup"><span data-stu-id="33829-177">named</span></span>                                |
| <span data-ttu-id="33829-178">默认值</span><span class="sxs-lookup"><span data-stu-id="33829-178">Default Value</span></span>                        | <span data-ttu-id="33829-179">false</span><span class="sxs-lookup"><span data-stu-id="33829-179">false</span></span>                                |
| <span data-ttu-id="33829-180">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="33829-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="33829-181">false</span><span class="sxs-lookup"><span data-stu-id="33829-181">false</span></span>                                |
| <span data-ttu-id="33829-182">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="33829-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="33829-183">false</span><span class="sxs-lookup"><span data-stu-id="33829-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="33829-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="33829-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="33829-185">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="33829-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="33829-186">有关详细信息，请参阅 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="33829-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="33829-187">输入</span><span class="sxs-lookup"><span data-stu-id="33829-187">INPUTS</span></span>

<span data-ttu-id="33829-188">此 cmdlet 不接受任何输入。</span><span class="sxs-lookup"><span data-stu-id="33829-188">This cmdlet takes no input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="33829-189">输出</span><span class="sxs-lookup"><span data-stu-id="33829-189">OUTPUTS</span></span>

<span data-ttu-id="33829-190">此 cmdlet 不会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="33829-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="33829-191">示例</span><span class="sxs-lookup"><span data-stu-id="33829-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="33829-192">示例 1</span><span class="sxs-lookup"><span data-stu-id="33829-192">EXAMPLE 1</span></span>

<span data-ttu-id="33829-193">此示例将使用 WebApplicationName (pswa) 的默认值和 WebSiteName（默认网站）参数来安装 PSWA Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="33829-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="33829-194">示例 2</span><span class="sxs-lookup"><span data-stu-id="33829-194">EXAMPLE 2</span></span>

<span data-ttu-id="33829-195">此示例将安装具有测试证书的 PSWA Web 应用程序，并将使用 WebApplicationName 的默认值和 WebSiteName 参数。</span><span class="sxs-lookup"><span data-stu-id="33829-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

##  <a name="related-topics"></a><span data-ttu-id="33829-196">相关主题</span><span class="sxs-lookup"><span data-stu-id="33829-196">Related topics</span></span>

-  [<span data-ttu-id="33829-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="33829-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="33829-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="33829-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="33829-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="33829-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
-  [<span data-ttu-id="33829-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="33829-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
