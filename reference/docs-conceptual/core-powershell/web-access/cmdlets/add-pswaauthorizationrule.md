---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "添加 pswaauthorizationrule"
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 12f5cc30d4e3f9cfdd739cacbbab96134077e50a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
#  <a name="add-pswaauthorizationrule"></a><span data-ttu-id="15969-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="15969-103">Add-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="15969-104">简述</span><span class="sxs-lookup"><span data-stu-id="15969-104">SYNOPSIS</span></span>

<span data-ttu-id="15969-105">向 Windows PowerShell® Web 访问授权规则集添加新的授权规则。</span><span class="sxs-lookup"><span data-stu-id="15969-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="15969-106">语法</span><span class="sxs-lookup"><span data-stu-id="15969-106">Syntax</span></span>

###  <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="15969-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="15969-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usergroupnamecomputername"></a><span data-ttu-id="15969-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="15969-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputergroupname"></a><span data-ttu-id="15969-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="15969-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputername"></a><span data-ttu-id="15969-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="15969-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="15969-111">说明</span><span class="sxs-lookup"><span data-stu-id="15969-111">DESCRIPTION</span></span>

<span data-ttu-id="15969-112">Add-PswaAuthorizationRule cmdlet 向 Windows PowerShell® Web 访问授权规则集添加新的授权规则。</span><span class="sxs-lookup"><span data-stu-id="15969-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="15969-113">必须为此规则指定用户、计算机和 Windows PowerShell 终结点。</span><span class="sxs-lookup"><span data-stu-id="15969-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="15969-114">既可通过个人用户帐户和计算机名称来指定用户和计算机，也可通过指定组来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="15969-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="15969-115">对于已加入 Active Directory 域的计算机，cmdlet 将使用计算机的安全标识符 (SID) 来创建该规则。</span><span class="sxs-lookup"><span data-stu-id="15969-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="15969-116">这允许你在登录页的“计算机名”字段中使用短名称、完全限定的域名 (FQDN) 或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="15969-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="15969-117">对于未加入 Active Directory 域的计算机，cmdlet 将使用管理员提供的计算机名来创建规则。</span><span class="sxs-lookup"><span data-stu-id="15969-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="15969-118">要成功连接到此计算机，最终用户必须提供与规则中出现的完全一致的计算机名。</span><span class="sxs-lookup"><span data-stu-id="15969-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="15969-119">如果网络上出现多个具有相同名称的计算机，则短名称可解析为多台计算机。</span><span class="sxs-lookup"><span data-stu-id="15969-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="15969-120">这可能在创建连接时造成多义性。</span><span class="sxs-lookup"><span data-stu-id="15969-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="15969-121">例如，如果名为“Server1”的工作组计算机具有一条规则，与此同时，在网络中又加入一个名为 server1.contoso.com 的新计算机，成功通过授权规则进行了验证，且 Windows PowerShell Web 访问尝试与名为“Server1”的计算机创建连接。</span><span class="sxs-lookup"><span data-stu-id="15969-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="15969-122">则无法保证所连接的对象是指定的工作组计算机；该操作有可能连接到工作组，也有可能连接到名为“Server1”的域计算机。</span><span class="sxs-lookup"><span data-stu-id="15969-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="15969-123">要减少多义性，建议尽量为目标计算机使用 FQDN 来创建授权规则。</span><span class="sxs-lookup"><span data-stu-id="15969-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="15969-124">授权规则评估 Windows PowerShell Web 访问用户的主登录凭据，而非备用凭据（有关备用凭据集，请前往登录页中的“可选连接设置”查看）。</span><span class="sxs-lookup"><span data-stu-id="15969-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="15969-125">有关以下内容的示例，请参阅示例 6。</span><span class="sxs-lookup"><span data-stu-id="15969-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="15969-126">参数</span><span class="sxs-lookup"><span data-stu-id="15969-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="15969-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="15969-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="15969-128">指定 Active Directory 域服务 (AD DS) 中计算机组的名称，或指定此规则授予访问权限的本地组名称。</span><span class="sxs-lookup"><span data-stu-id="15969-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="15969-129">别名</span><span class="sxs-lookup"><span data-stu-id="15969-129">Aliases</span></span>                              | <span data-ttu-id="15969-130">无</span><span class="sxs-lookup"><span data-stu-id="15969-130">none</span></span>                                 |
| <span data-ttu-id="15969-131">是否必需？</span><span class="sxs-lookup"><span data-stu-id="15969-131">Required?</span></span>                            | <span data-ttu-id="15969-132">true</span><span class="sxs-lookup"><span data-stu-id="15969-132">true</span></span>                                 |
| <span data-ttu-id="15969-133">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="15969-133">Position?</span></span>                            | <span data-ttu-id="15969-134">named</span><span class="sxs-lookup"><span data-stu-id="15969-134">named</span></span>                                |
| <span data-ttu-id="15969-135">默认值</span><span class="sxs-lookup"><span data-stu-id="15969-135">Default Value</span></span>                        | <span data-ttu-id="15969-136">无</span><span class="sxs-lookup"><span data-stu-id="15969-136">none</span></span>                                 |
| <span data-ttu-id="15969-137">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="15969-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15969-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15969-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15969-139">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="15969-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15969-140">false</span><span class="sxs-lookup"><span data-stu-id="15969-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="15969-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="15969-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="15969-142">指定此规则授予访问权限的计算机名。</span><span class="sxs-lookup"><span data-stu-id="15969-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="15969-143">别名</span><span class="sxs-lookup"><span data-stu-id="15969-143">Aliases</span></span>                              | <span data-ttu-id="15969-144">无</span><span class="sxs-lookup"><span data-stu-id="15969-144">none</span></span>                                 |
| <span data-ttu-id="15969-145">是否必需？</span><span class="sxs-lookup"><span data-stu-id="15969-145">Required?</span></span>                            | <span data-ttu-id="15969-146">true</span><span class="sxs-lookup"><span data-stu-id="15969-146">true</span></span>                                 |
| <span data-ttu-id="15969-147">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="15969-147">Position?</span></span>                            | <span data-ttu-id="15969-148">named</span><span class="sxs-lookup"><span data-stu-id="15969-148">named</span></span>                                |
| <span data-ttu-id="15969-149">默认值</span><span class="sxs-lookup"><span data-stu-id="15969-149">Default Value</span></span>                        | <span data-ttu-id="15969-150">无</span><span class="sxs-lookup"><span data-stu-id="15969-150">none</span></span>                                 |
| <span data-ttu-id="15969-151">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="15969-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15969-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15969-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15969-153">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="15969-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15969-154">false</span><span class="sxs-lookup"><span data-stu-id="15969-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="15969-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="15969-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="15969-156">指定此规则授予访问权限的 Windows PowerShell 会话配置的名称（又称为运行空间）。</span><span class="sxs-lookup"><span data-stu-id="15969-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="15969-157">别名</span><span class="sxs-lookup"><span data-stu-id="15969-157">Aliases</span></span>                              | <span data-ttu-id="15969-158">无</span><span class="sxs-lookup"><span data-stu-id="15969-158">none</span></span>                                 |
| <span data-ttu-id="15969-159">是否必需？</span><span class="sxs-lookup"><span data-stu-id="15969-159">Required?</span></span>                            | <span data-ttu-id="15969-160">true</span><span class="sxs-lookup"><span data-stu-id="15969-160">true</span></span>                                 |
| <span data-ttu-id="15969-161">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="15969-161">Position?</span></span>                            | <span data-ttu-id="15969-162">named</span><span class="sxs-lookup"><span data-stu-id="15969-162">named</span></span>                                |
| <span data-ttu-id="15969-163">默认值</span><span class="sxs-lookup"><span data-stu-id="15969-163">Default Value</span></span>                        | <span data-ttu-id="15969-164">无</span><span class="sxs-lookup"><span data-stu-id="15969-164">none</span></span>                                 |
| <span data-ttu-id="15969-165">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="15969-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15969-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15969-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15969-167">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="15969-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15969-168">false</span><span class="sxs-lookup"><span data-stu-id="15969-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="15969-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="15969-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="15969-170">为要用于更改 Windows PowerShell Web 访问授权规则的用户帐户指定 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="15969-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="15969-171">如果不添加此参数，cmdlet 将使用当前登录的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="15969-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="15969-172">要获取 PSCredential 对象（用于以远程方式添加授权规则），请运行 [Get-Credential cmdlet](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential)。</span><span class="sxs-lookup"><span data-stu-id="15969-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="15969-173">别名</span><span class="sxs-lookup"><span data-stu-id="15969-173">Aliases</span></span>                              | <span data-ttu-id="15969-174">无</span><span class="sxs-lookup"><span data-stu-id="15969-174">none</span></span>                                 |
| <span data-ttu-id="15969-175">是否必需？</span><span class="sxs-lookup"><span data-stu-id="15969-175">Required?</span></span>                            | <span data-ttu-id="15969-176">false</span><span class="sxs-lookup"><span data-stu-id="15969-176">false</span></span>                                |
| <span data-ttu-id="15969-177">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="15969-177">Position?</span></span>                            | <span data-ttu-id="15969-178">named</span><span class="sxs-lookup"><span data-stu-id="15969-178">named</span></span>                                |
| <span data-ttu-id="15969-179">默认值</span><span class="sxs-lookup"><span data-stu-id="15969-179">Default Value</span></span>                        | <span data-ttu-id="15969-180">无</span><span class="sxs-lookup"><span data-stu-id="15969-180">none</span></span>                                 |
| <span data-ttu-id="15969-181">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="15969-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15969-182">false</span><span class="sxs-lookup"><span data-stu-id="15969-182">false</span></span>                                |
| <span data-ttu-id="15969-183">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="15969-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15969-184">false</span><span class="sxs-lookup"><span data-stu-id="15969-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="15969-185">-Force</span><span class="sxs-lookup"><span data-stu-id="15969-185">-Force</span></span>

<span data-ttu-id="15969-186">强制运行命令而不要求用户确认。</span><span class="sxs-lookup"><span data-stu-id="15969-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="15969-187">此外，在输入简单或短计算机名时（例如不是域名的名称，或不是完全限定的名称），系统还会出现确认提示。</span><span class="sxs-lookup"><span data-stu-id="15969-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="15969-188">该确认请求旨在保证安全，仅当计算机在工作组中时，才可使用简单名称来添加计算机。</span><span class="sxs-lookup"><span data-stu-id="15969-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="15969-189">别名</span><span class="sxs-lookup"><span data-stu-id="15969-189">Aliases</span></span>                              | <span data-ttu-id="15969-190">无</span><span class="sxs-lookup"><span data-stu-id="15969-190">none</span></span>                                 |
| <span data-ttu-id="15969-191">是否必需？</span><span class="sxs-lookup"><span data-stu-id="15969-191">Required?</span></span>                            | <span data-ttu-id="15969-192">false</span><span class="sxs-lookup"><span data-stu-id="15969-192">false</span></span>                                |
| <span data-ttu-id="15969-193">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="15969-193">Position?</span></span>                            | <span data-ttu-id="15969-194">named</span><span class="sxs-lookup"><span data-stu-id="15969-194">named</span></span>                                |
| <span data-ttu-id="15969-195">默认值</span><span class="sxs-lookup"><span data-stu-id="15969-195">Default Value</span></span>                        | <span data-ttu-id="15969-196">无</span><span class="sxs-lookup"><span data-stu-id="15969-196">none</span></span>                                 |
| <span data-ttu-id="15969-197">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="15969-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15969-198">false</span><span class="sxs-lookup"><span data-stu-id="15969-198">false</span></span>                                |
| <span data-ttu-id="15969-199">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="15969-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15969-200">false</span><span class="sxs-lookup"><span data-stu-id="15969-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="15969-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="15969-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="15969-202">为此规则指定友好名称。</span><span class="sxs-lookup"><span data-stu-id="15969-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="15969-203">别名</span><span class="sxs-lookup"><span data-stu-id="15969-203">Aliases</span></span>                              | <span data-ttu-id="15969-204">无</span><span class="sxs-lookup"><span data-stu-id="15969-204">none</span></span>                                 |
| <span data-ttu-id="15969-205">是否必需？</span><span class="sxs-lookup"><span data-stu-id="15969-205">Required?</span></span>                            | <span data-ttu-id="15969-206">false</span><span class="sxs-lookup"><span data-stu-id="15969-206">false</span></span>                                |
| <span data-ttu-id="15969-207">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="15969-207">Position?</span></span>                            | <span data-ttu-id="15969-208">named</span><span class="sxs-lookup"><span data-stu-id="15969-208">named</span></span>                                |
| <span data-ttu-id="15969-209">默认值</span><span class="sxs-lookup"><span data-stu-id="15969-209">Default Value</span></span>                        | <span data-ttu-id="15969-210">无</span><span class="sxs-lookup"><span data-stu-id="15969-210">none</span></span>                                 |
| <span data-ttu-id="15969-211">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="15969-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15969-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15969-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15969-213">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="15969-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15969-214">false</span><span class="sxs-lookup"><span data-stu-id="15969-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="15969-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="15969-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="15969-216">指定 AD DS 中一个或多个用户组的名称，或指定此规则授予访问权限的本地组名称。</span><span class="sxs-lookup"><span data-stu-id="15969-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="15969-217">别名</span><span class="sxs-lookup"><span data-stu-id="15969-217">Aliases</span></span>                              | <span data-ttu-id="15969-218">无</span><span class="sxs-lookup"><span data-stu-id="15969-218">none</span></span>                                 |
| <span data-ttu-id="15969-219">是否必需？</span><span class="sxs-lookup"><span data-stu-id="15969-219">Required?</span></span>                            | <span data-ttu-id="15969-220">true</span><span class="sxs-lookup"><span data-stu-id="15969-220">true</span></span>                                 |
| <span data-ttu-id="15969-221">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="15969-221">Position?</span></span>                            | <span data-ttu-id="15969-222">named</span><span class="sxs-lookup"><span data-stu-id="15969-222">named</span></span>                                |
| <span data-ttu-id="15969-223">默认值</span><span class="sxs-lookup"><span data-stu-id="15969-223">Default Value</span></span>                        | <span data-ttu-id="15969-224">无</span><span class="sxs-lookup"><span data-stu-id="15969-224">none</span></span>                                 |
| <span data-ttu-id="15969-225">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="15969-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15969-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15969-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15969-227">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="15969-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15969-228">false</span><span class="sxs-lookup"><span data-stu-id="15969-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="15969-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="15969-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="15969-230">指定此规则向其授予访问权限的一个或多个用户。</span><span class="sxs-lookup"><span data-stu-id="15969-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="15969-231">用户名可以是网关计算机上的本地用户帐户，也可以是 AD DS 中的用户。</span><span class="sxs-lookup"><span data-stu-id="15969-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="15969-232">格式为 `domain\user` 或 `computer\user`。</span><span class="sxs-lookup"><span data-stu-id="15969-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="15969-233">别名</span><span class="sxs-lookup"><span data-stu-id="15969-233">Aliases</span></span>                              | <span data-ttu-id="15969-234">无</span><span class="sxs-lookup"><span data-stu-id="15969-234">none</span></span>                                 |
| <span data-ttu-id="15969-235">是否必需？</span><span class="sxs-lookup"><span data-stu-id="15969-235">Required?</span></span>                            | <span data-ttu-id="15969-236">true</span><span class="sxs-lookup"><span data-stu-id="15969-236">true</span></span>                                 |
| <span data-ttu-id="15969-237">位置在哪里？</span><span class="sxs-lookup"><span data-stu-id="15969-237">Position?</span></span>                            | <span data-ttu-id="15969-238">1</span><span class="sxs-lookup"><span data-stu-id="15969-238">1</span></span>                                    |
| <span data-ttu-id="15969-239">默认值</span><span class="sxs-lookup"><span data-stu-id="15969-239">Default Value</span></span>                        | <span data-ttu-id="15969-240">无</span><span class="sxs-lookup"><span data-stu-id="15969-240">none</span></span>                                 |
| <span data-ttu-id="15969-241">是否接受管道输入？</span><span class="sxs-lookup"><span data-stu-id="15969-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15969-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15969-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="15969-243">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="15969-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15969-244">false</span><span class="sxs-lookup"><span data-stu-id="15969-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="15969-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="15969-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="15969-246">此 cmdlet 支持通用参数：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="15969-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="15969-247">有关详细信息，请参阅 [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters)。</span><span class="sxs-lookup"><span data-stu-id="15969-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="15969-248">输入</span><span class="sxs-lookup"><span data-stu-id="15969-248">INPUTS</span></span>

###  <a name="string"></a><span data-ttu-id="15969-249">字符串</span><span class="sxs-lookup"><span data-stu-id="15969-249">String</span></span>

<span data-ttu-id="15969-250">此 cmdlet 接受字符串或字符串数组作为输入。</span><span class="sxs-lookup"><span data-stu-id="15969-250">This cmdlet accepts a string or an array of strings as input.</span></span>

###  <a name="string"></a><span data-ttu-id="15969-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="15969-251">String\[\]</span></span>

<span data-ttu-id="15969-252">此 cmdlet 接受字符串或字符串数组作为输入。</span><span class="sxs-lookup"><span data-stu-id="15969-252">This cmdlet accepts a string or an array of strings as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="15969-253">输出</span><span class="sxs-lookup"><span data-stu-id="15969-253">Outputs</span></span>

###   <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="15969-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="15969-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="15969-255">此 cmdlet 将返回授权规则对象。</span><span class="sxs-lookup"><span data-stu-id="15969-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="15969-256">示例</span><span class="sxs-lookup"><span data-stu-id="15969-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="15969-257">示例 1</span><span class="sxs-lookup"><span data-stu-id="15969-257">EXAMPLE 1</span></span>

<span data-ttu-id="15969-258">此示例授予对 SMAdmins 组中的用户在 srv2 上的会话配置 PSWAEndpoint（一个受限运行空间）的访问权限。</span><span class="sxs-lookup"><span data-stu-id="15969-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="15969-259">注意：该计算机名必须是完全限定的域名 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="15969-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="15969-260">管理员定义受限制的会话配置或运行空间，这是一系列可供最终用户运行的有限 cmdlet 和任务。</span><span class="sxs-lookup"><span data-stu-id="15969-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="15969-261">定义受限制的运行空间可阻止用户访问不在允许的 Windows PowerShell® 运行空间中的其他计算机，提高连接安全性。</span><span class="sxs-lookup"><span data-stu-id="15969-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="15969-262">有关会话配置的详细信息，请参阅 [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) 或[安装和使用 Windows PowerShell Web 访问](../install-and-use-windows-powershell-web-access.md)。</span><span class="sxs-lookup"><span data-stu-id="15969-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="15969-263">示例 2</span><span class="sxs-lookup"><span data-stu-id="15969-263">EXAMPLE 2</span></span>

<span data-ttu-id="15969-264">此示例在 srv2 上为名为 contoso\\user1、contoso\\user2 和 contoso\\user3 用户中的用户，授予默认 Windows PowerShell 会话配置访问权限 `Microsoft.PowerShell`。</span><span class="sxs-lookup"><span data-stu-id="15969-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="15969-265">此 cmdlet 将创建三条规则（每人一条）。</span><span class="sxs-lookup"><span data-stu-id="15969-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="15969-266">示例 3</span><span class="sxs-lookup"><span data-stu-id="15969-266">EXAMPLE 3</span></span>

<span data-ttu-id="15969-267">此示例将说明如何通过管道输入用户名值。</span><span class="sxs-lookup"><span data-stu-id="15969-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="15969-268">示例 4</span><span class="sxs-lookup"><span data-stu-id="15969-268">EXAMPLE 4</span></span>

<span data-ttu-id="15969-269">此示例说明如何按属性名从管道为所有参数获取值。</span><span class="sxs-lookup"><span data-stu-id="15969-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

\
###   <a name="section-subheading"></a><span data-ttu-id="15969-270">{#section .subHeading}</span><span class="sxs-lookup"><span data-stu-id="15969-270">{#section .subHeading}</span></span>

<div class="subSection">

<div id="code-snippet-5" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="15969-271">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15969-271">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="15969-272">Copy</span><span class="sxs-lookup"><span data-stu-id="15969-272">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o = New-Object -TypeName PSObject | Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

</div>

</div>

</div>

</div>

</div>

###   <a name="section-1-subheading"></a><span data-ttu-id="15969-273">{#section-1 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="15969-273">{#section-1 .subHeading}</span></span>

<div class="subSection">

<div id="code-snippet-6" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="15969-274">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15969-274">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="15969-275">Copy</span><span class="sxs-lookup"><span data-stu-id="15969-275">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

</div>

### <a name="example-5-example-5-subheading"></a><span data-ttu-id="15969-276">示例 5 {#example-5 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="15969-276">EXAMPLE 5 {#example-5 .subHeading}</span></span>

<div class="subSection">

<span data-ttu-id="15969-277">此示例将添加一条规则，允许名为 PswaServer\\ChrisLocal 的本地用户访问名为 srv1.contoso.com 的服务器。</span><span class="sxs-lookup"><span data-stu-id="15969-277">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="15969-278">此示例对网关位于工作组，目标计算机位于域中的方案进行了说明。</span><span class="sxs-lookup"><span data-stu-id="15969-278">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="15969-279">授权规则适用于网关上的本地用户。</span><span class="sxs-lookup"><span data-stu-id="15969-279">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="15969-280">在 Windows PowerShell Web 访问登录页中，要成功进行身份验证，用户必须在“可选连接设置”中提供备用凭据组。</span><span class="sxs-lookup"><span data-stu-id="15969-280">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="15969-281">网关服务器使用一组额外的凭据，在服务器名为 srv1.contoso.com 的目标计算机上对用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="15969-281">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

\
<div id="code-snippet-7" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="15969-282">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15969-282">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="15969-283">Copy</span><span class="sxs-lookup"><span data-stu-id="15969-283">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

### <a name="example-6-example-6-subheading"></a><span data-ttu-id="15969-284">示例 6 {#example-6 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="15969-284">EXAMPLE 6 {#example-6 .subHeading}</span></span>

<div class="subSection">

<span data-ttu-id="15969-285">此示例允许全体用户访问所有计算机中的全部终结点。</span><span class="sxs-lookup"><span data-stu-id="15969-285">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="15969-286">这实际上关闭了授权规则。</span><span class="sxs-lookup"><span data-stu-id="15969-286">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="15969-287">注意：出于安全敏感部署的考虑，除测试环境或对安全要求不高的部署之外，不建议使用 `*` 通配符。</span><span class="sxs-lookup"><span data-stu-id="15969-287">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

\
<div id="code-snippet-8" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="15969-288">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15969-288">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="15969-289">Copy</span><span class="sxs-lookup"><span data-stu-id="15969-289">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *

</div>

</div>

</div>

</div>

</div>

</div>

<a name="related-topics"></a><span data-ttu-id="15969-290">相关主题</span><span class="sxs-lookup"><span data-stu-id="15969-290">Related topics</span></span> 
--------------


<span data-ttu-id="15969-291">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="15969-291">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="15969-292">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="15969-292">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="15969-293">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="15969-293">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="15969-294">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="15969-294">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="15969-295">[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\\</span><span class="sxs-lookup"><span data-stu-id="15969-295">[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\\</span></span>
\
<span data-ttu-id="15969-296">[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\\</span><span class="sxs-lookup"><span data-stu-id="15969-296">[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\\</span></span>
\
[<span data-ttu-id="15969-297">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="15969-297">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)