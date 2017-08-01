---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "端到端 - Active Directory"
ms.technology: powershell
ms.openlocfilehash: 3108f5dad96ef54feb3cf559fae38812ed46849c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="end-to-end---active-directory"></a><span data-ttu-id="8a713-103">端到端 - Active Directory</span><span class="sxs-lookup"><span data-stu-id="8a713-103">End to End - Active Directory</span></span>
<span data-ttu-id="8a713-104">假设你的程序作用域扩大了。</span><span class="sxs-lookup"><span data-stu-id="8a713-104">Imagine the scope of your program has increased.</span></span>
<span data-ttu-id="8a713-105">你现在有责任将 JEA 添加到域控制器以执行 Active Directory 操作。</span><span class="sxs-lookup"><span data-stu-id="8a713-105">You are now responsible for adding JEA to Domain Controllers to perform Active Directory actions.</span></span>
<span data-ttu-id="8a713-106">技术支持人员将使用 JEA 解锁帐户、重置密码以及执行其他类似操作。</span><span class="sxs-lookup"><span data-stu-id="8a713-106">The help desk people are going to use JEA to unlock accounts, reset passwords, and do other similar actions.</span></span>

<span data-ttu-id="8a713-107">你需要向另一组人员公开全新的一组命令。</span><span class="sxs-lookup"><span data-stu-id="8a713-107">You need to expose a completely new set of commands to a different group of people.</span></span>
<span data-ttu-id="8a713-108">在此基础上，你还需公开一组现有 Active Directory 脚本。</span><span class="sxs-lookup"><span data-stu-id="8a713-108">On top of that, you have a bunch of existing Active Directory scripts you need to expose.</span></span>
<span data-ttu-id="8a713-109">本部分将演练为此任务创作会话配置和角色功能。</span><span class="sxs-lookup"><span data-stu-id="8a713-109">This section will walk through authoring a Session Configuration and Role Capability for this task.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a713-110">必备条件</span><span class="sxs-lookup"><span data-stu-id="8a713-110">Prerequisites</span></span>
<span data-ttu-id="8a713-111">若要按照此部分进行逐步操作，需在域控制器上进行操作。</span><span class="sxs-lookup"><span data-stu-id="8a713-111">To follow this section step-by-step, you'll need to be operating on a domain controller.</span></span>
<span data-ttu-id="8a713-112">如果你无权访问你的域控制器，请不要担心。</span><span class="sxs-lookup"><span data-stu-id="8a713-112">If you don't have access to your domain controller, don't worry.</span></span>
<span data-ttu-id="8a713-113">请尝试对你熟悉的其他方案或角色进行操作以便跟进。</span><span class="sxs-lookup"><span data-stu-id="8a713-113">Try to follow along with by working against some other scenario or role with which you are familiar.</span></span>
<span data-ttu-id="8a713-114">如要快速设置新的域控制器，请参阅[“创建域控制器”附录](.\creating-a-domain-controller.md)。</span><span class="sxs-lookup"><span data-stu-id="8a713-114">If you want to quickly set up a new domain controller, check out the [Creating a Domain Controller appendix](.\creating-a-domain-controller.md).</span></span>

## <a name="steps-to-make-a-new-role-capability-and-session-configuration"></a><span data-ttu-id="8a713-115">创建新角色功能和会话配置的步骤</span><span class="sxs-lookup"><span data-stu-id="8a713-115">Steps to Make a new Role Capability and Session Configuration</span></span>

<span data-ttu-id="8a713-116">创建新角色功能乍看令人生畏，但可将其分为相当简单的几个步骤：</span><span class="sxs-lookup"><span data-stu-id="8a713-116">Making a new role capability can seem daunting at first, but it can be broken into fairly simple steps:</span></span>

1.  <span data-ttu-id="8a713-117">确定需要启用的任务</span><span class="sxs-lookup"><span data-stu-id="8a713-117">Identify the tasks you need to enable</span></span>
2.  <span data-ttu-id="8a713-118">根据需要限制这些任务</span><span class="sxs-lookup"><span data-stu-id="8a713-118">Restrict those tasks as necessary</span></span>
3.  <span data-ttu-id="8a713-119">确认它们适用于 JEA</span><span class="sxs-lookup"><span data-stu-id="8a713-119">Confirm they work with JEA</span></span>
4.  <span data-ttu-id="8a713-120">将其置于角色功能文件中</span><span class="sxs-lookup"><span data-stu-id="8a713-120">Put them in a Role Capability file</span></span>
5.  <span data-ttu-id="8a713-121">注册用于公开该角色功能的会话配置</span><span class="sxs-lookup"><span data-stu-id="8a713-121">Register a Session Configuration that exposes that Role Capability</span></span>

## <a name="step-1-identify-what-needs-to-be-exposed"></a><span data-ttu-id="8a713-122">步骤 1：确定需要公开的内容</span><span class="sxs-lookup"><span data-stu-id="8a713-122">Step 1: Identify What Needs to Be Exposed</span></span>
<span data-ttu-id="8a713-123">在创建新角色功能或会话配置之前，需要确定用户需通过 JEA 终结点执行的所有操作，以及如何通过 PowerShell 来执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="8a713-123">Before you make a new Role Capability or Session Configuration, you need to identify all of the things users will need to do through the JEA endpoint, as well as how to do them through PowerShell.</span></span>
<span data-ttu-id="8a713-124">这将涉及大量的需求收集和研究。</span><span class="sxs-lookup"><span data-stu-id="8a713-124">This will involve a fair amount of requirement gathering and research.</span></span>
<span data-ttu-id="8a713-125">你进行此过程的方式将取决于你的组织和目标。</span><span class="sxs-lookup"><span data-stu-id="8a713-125">How you go about this process will depend on your organization and goals.</span></span>
<span data-ttu-id="8a713-126">请务必将需求收集和研究作为实际过程的一个关键部分。</span><span class="sxs-lookup"><span data-stu-id="8a713-126">It is important to call out requirement gathering and research as a critical part of the real world process.</span></span>
<span data-ttu-id="8a713-127">这可能是采用 JEA 的过程中最艰难的步骤。</span><span class="sxs-lookup"><span data-stu-id="8a713-127">This may be the most difficult step in the process of adopting JEA.</span></span>

### <a name="find-resources"></a><span data-ttu-id="8a713-128">查找资源</span><span class="sxs-lookup"><span data-stu-id="8a713-128">Find Resources</span></span>
<span data-ttu-id="8a713-129">针对创建 Active Directory 管理终结点进行研究时，你可能找到了以下一组在线资源：</span><span class="sxs-lookup"><span data-stu-id="8a713-129">Here is a set of online resources that might have come up in your research on creating an Active Directory management endpoint:</span></span>
-   [<span data-ttu-id="8a713-130">Active Directory PowerShell 概述</span><span class="sxs-lookup"><span data-stu-id="8a713-130">Active Directory PowerShell Overview</span></span>](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [<span data-ttu-id="8a713-131">适用于 Active Directory 的 CMD 到 PowerShell 指南</span><span class="sxs-lookup"><span data-stu-id="8a713-131">CMD to PowerShell Guide for Active Directory</span></span>](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### <a name="make-a-list"></a><span data-ttu-id="8a713-132">制作列表</span><span class="sxs-lookup"><span data-stu-id="8a713-132">Make a List</span></span>
<span data-ttu-id="8a713-133">在本节剩余部分中，你将进行以下十个操作。</span><span class="sxs-lookup"><span data-stu-id="8a713-133">Here is a set of ten actions that you will be working from in the remainder of this section.</span></span>
<span data-ttu-id="8a713-134">请注意这只是一个示例，你组织的需求可能会有所不同：</span><span class="sxs-lookup"><span data-stu-id="8a713-134">Keep in mind this is simply an example, your organizations requirements may be different:</span></span>

|<span data-ttu-id="8a713-135">操作</span><span class="sxs-lookup"><span data-stu-id="8a713-135">Action</span></span>                                                         |<span data-ttu-id="8a713-136">PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="8a713-136">PowerShell Command</span></span>                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|<span data-ttu-id="8a713-137">帐户解锁</span><span class="sxs-lookup"><span data-stu-id="8a713-137">Account Unlock</span></span>                                                 |`Unlock-ADAccount`                                             |
|<span data-ttu-id="8a713-138">密码重置</span><span class="sxs-lookup"><span data-stu-id="8a713-138">Password Reset</span></span>                                                 |<span data-ttu-id="8a713-139">`Set-ADAccountPassword` 和 `Set-ADUser -ChangePasswordAtLogon`</span><span class="sxs-lookup"><span data-stu-id="8a713-139">`Set-ADAccountPassword` and `Set-ADUser -ChangePasswordAtLogon`</span></span>|
|<span data-ttu-id="8a713-140">更改用户的职务</span><span class="sxs-lookup"><span data-stu-id="8a713-140">Change a User's Title</span></span>                                          |`Set-ADUser -Title`                                            |  
|<span data-ttu-id="8a713-141">查找处于已锁定、已禁用、已停用等状态的 AD 帐户</span><span class="sxs-lookup"><span data-stu-id="8a713-141">Find AD Accounts that are locked out, disabled, inactive, etc.</span></span> |`Search-ADAccount`                                             |
|<span data-ttu-id="8a713-142">将用户添加到组</span><span class="sxs-lookup"><span data-stu-id="8a713-142">Add User to Group</span></span>                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|<span data-ttu-id="8a713-143">从组中删除用户</span><span class="sxs-lookup"><span data-stu-id="8a713-143">Remove User from Group</span></span>                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|<span data-ttu-id="8a713-144">启用用户帐户</span><span class="sxs-lookup"><span data-stu-id="8a713-144">Enable a user account</span></span>                                          |`Enable-ADAccount`                                             |
|<span data-ttu-id="8a713-145">禁用用户帐户</span><span class="sxs-lookup"><span data-stu-id="8a713-145">Disable a user account</span></span>                                         |`Disable-ADAccount`                                            |

## <a name="step-2-restrict-tasks-as-necessary"></a><span data-ttu-id="8a713-146">步骤 2：根据需要限制任务</span><span class="sxs-lookup"><span data-stu-id="8a713-146">Step 2: Restrict Tasks as Necessary</span></span>

<span data-ttu-id="8a713-147">现在你拥有了操作的列表，需仔细思考每个命令的功能。</span><span class="sxs-lookup"><span data-stu-id="8a713-147">Now that you have your list of actions, you need to think through the capabilities of each command.</span></span>
<span data-ttu-id="8a713-148">这样做有两个重要的原因：</span><span class="sxs-lookup"><span data-stu-id="8a713-148">There are two important reasons to do this:</span></span>

1.  <span data-ttu-id="8a713-149">首先，容易为用户提供比你预期更多的功能。</span><span class="sxs-lookup"><span data-stu-id="8a713-149">It is easy to give users more capabilities than you intend.</span></span>
<span data-ttu-id="8a713-150">例如，`Set-ADUser` 是一个极其强大和灵活的命令。</span><span class="sxs-lookup"><span data-stu-id="8a713-150">For example, `Set-ADUser` is an incredibly powerful and flexible command.</span></span>
<span data-ttu-id="8a713-151">你可能不希望向技术支持用户公开其全部功能。</span><span class="sxs-lookup"><span data-stu-id="8a713-151">You may not want to expose everything it can do to help desk users.</span></span>  

2.  <span data-ttu-id="8a713-152">更糟糕的是，它可能会公开允许用户脱离 JEA 限制的命令。</span><span class="sxs-lookup"><span data-stu-id="8a713-152">Even worse, it's possible to expose commands that allow users to escape JEA's restrictions.</span></span>
<span data-ttu-id="8a713-153">如果发生这种情况，JEA 将不再起到安全边界的作用。</span><span class="sxs-lookup"><span data-stu-id="8a713-153">If this happens, JEA ceases to function as a security boundary.</span></span>
<span data-ttu-id="8a713-154">请谨慎选择命令。</span><span class="sxs-lookup"><span data-stu-id="8a713-154">Please be careful when selecting commands.</span></span>
<span data-ttu-id="8a713-155">例如，Invoke-Expression 将允许用户运行不受限制的代码。</span><span class="sxs-lookup"><span data-stu-id="8a713-155">For example, Invoke-Expression will allow users to run unrestricted code.</span></span>
<span data-ttu-id="8a713-156">有关这一主题的详细讨论，请参阅“限制命令时的注意事项”部分。</span><span class="sxs-lookup"><span data-stu-id="8a713-156">For more discussion on this topic, check out the Considerations When Restricting Commands section.</span></span>

<span data-ttu-id="8a713-157">检查每个命令后，请决定限制以下内容：</span><span class="sxs-lookup"><span data-stu-id="8a713-157">After reviewing each command, you decide to restrict the following:</span></span>

1.  <span data-ttu-id="8a713-158">`Set-ADUser` 应仅允许在使用 -Title 参数时运行</span><span class="sxs-lookup"><span data-stu-id="8a713-158">`Set-ADUser` should only be allowed to run with the -Title parameter</span></span>

2.  <span data-ttu-id="8a713-159">`Add-ADGroupMember` 和 `Remove-ADGroupMember` 应仅适用于特定组</span><span class="sxs-lookup"><span data-stu-id="8a713-159">`Add-ADGroupMember` and `Remove-ADGroupMember` should only work with certain groups</span></span>

### <a name="step-3-confirm-the-tasks-work-with-jea"></a><span data-ttu-id="8a713-160">步骤 3：确认任务适用 JEA</span><span class="sxs-lookup"><span data-stu-id="8a713-160">Step 3: Confirm the Tasks Work with JEA</span></span>
<span data-ttu-id="8a713-161">在受限的 JEA 环境中，实际使用这些 cmdlet 可能并不直接。</span><span class="sxs-lookup"><span data-stu-id="8a713-161">Actually using those cmdlets may not be straightforward in the restricted JEA environment.</span></span>
<span data-ttu-id="8a713-162">JEA 在*无语言*模式下运行，该模式（以及其他一些模式）将阻止用户使用变量。</span><span class="sxs-lookup"><span data-stu-id="8a713-162">JEA runs in *NoLanguage* mode which, among other things, prevents users from using variables.</span></span>
<span data-ttu-id="8a713-163">为确保最终用户具有流畅的体验，请务必检查某些内容。</span><span class="sxs-lookup"><span data-stu-id="8a713-163">In order to ensure that end users have a smooth experience, it's important to check for a few things.</span></span>

<span data-ttu-id="8a713-164">例如，请考虑 `Set-ADAccountPassword`。</span><span class="sxs-lookup"><span data-stu-id="8a713-164">As an example, consider `Set-ADAccountPassword`.</span></span>
<span data-ttu-id="8a713-165">-NewPassword 参数需要安全字符串。</span><span class="sxs-lookup"><span data-stu-id="8a713-165">The -NewPassword parameter requires a secure string.</span></span>
<span data-ttu-id="8a713-166">用户常创建安全字符串并将其作为变量进行传递（如下所示）：</span><span class="sxs-lookup"><span data-stu-id="8a713-166">Often, users create a secure string and pass it in as a variable (as below):</span></span>

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

<span data-ttu-id="8a713-167">但是，*无语言*模式阻止使用变量。</span><span class="sxs-lookup"><span data-stu-id="8a713-167">However, *NoLanguage* mode prevents the usage of variables.</span></span>
<span data-ttu-id="8a713-168">你可以通过两种方式避开此限制：</span><span class="sxs-lookup"><span data-stu-id="8a713-168">You can get around this restriction in two ways:</span></span>

1.  <span data-ttu-id="8a713-169">你可以要求用户运行命令而不分配变量。</span><span class="sxs-lookup"><span data-stu-id="8a713-169">You can require users run the command without assigning variables.</span></span>
<span data-ttu-id="8a713-170">这很容易配置，但可能令操作员苦于使用终结点。</span><span class="sxs-lookup"><span data-stu-id="8a713-170">This is easy to configure, but can be painful for the operators using the endpoint.</span></span>
<span data-ttu-id="8a713-171">谁愿意每次重置密码时都键入安全字符串？</span><span class="sxs-lookup"><span data-stu-id="8a713-171">Who wants to type this out every time you reset a password?</span></span>
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  <span data-ttu-id="8a713-172">你可以在向最终用户公开的脚本或函数中包装复杂性。</span><span class="sxs-lookup"><span data-stu-id="8a713-172">You can wrap the complexity in a script or a function that you expose to end users.</span></span>
<span data-ttu-id="8a713-173">你公开的脚本和函数在不受限制的上下文中运行；你可以编写使用变量的函数并调用其他命令而不会引发任何问题。</span><span class="sxs-lookup"><span data-stu-id="8a713-173">Scripts and functions that you expose run in an unrestricted context; you can write functions that use variables and call other commands without any issue.</span></span>
<span data-ttu-id="8a713-174">这种方法可简化最终用户体验、避免错误、减少所需 PowerShell 知识，并减少过多功能的无意公开。</span><span class="sxs-lookup"><span data-stu-id="8a713-174">This approach simplifies the end user experience, prevents errors, reduces required PowerShell knowledge, and reduces unintentionally exposing excess functionality.</span></span>
<span data-ttu-id="8a713-175">唯一的缺点是创作和维护函数的成本。</span><span class="sxs-lookup"><span data-stu-id="8a713-175">The only downside is the cost of authoring and maintaining the function.</span></span>

### <a name="aside-adding-a-function-to-your-module"></a><span data-ttu-id="8a713-176">保留：将函数添加到模块</span><span class="sxs-lookup"><span data-stu-id="8a713-176">Aside: Adding a Function to your Module</span></span>
<span data-ttu-id="8a713-177">采用方法 2，你将编写名为 `Reset-ContosoUserPassword` 的 PowerShell 函数。</span><span class="sxs-lookup"><span data-stu-id="8a713-177">Taking approach #2, you are going to write a PowerShell function called `Reset-ContosoUserPassword`.</span></span>
<span data-ttu-id="8a713-178">当你重置用户密码时，此函数将执行所需的一切操作。</span><span class="sxs-lookup"><span data-stu-id="8a713-178">This function is going to do everything that needs to happen when you reset a user's password.</span></span>
<span data-ttu-id="8a713-179">在你的组织中，这可能涉及到特别而复杂的操作。</span><span class="sxs-lookup"><span data-stu-id="8a713-179">In your organization, this may involve doing fancy and complicated things.</span></span>
<span data-ttu-id="8a713-180">因为这只是一个示例，因此你的命令将仅重置密码并要求用户在登录时更改密码。</span><span class="sxs-lookup"><span data-stu-id="8a713-180">Because this is just an example, your command will just reset the password and require the user change the password at logon.</span></span>
<span data-ttu-id="8a713-181">我们会将它放在你在最后一部分中创建的 Contoso_AD_Module 模块中。</span><span class="sxs-lookup"><span data-stu-id="8a713-181">We will put it in the Contoso_AD_Module module you made in the last section.</span></span>

1. <span data-ttu-id="8a713-182">在 PowerShell ISE 中，打开“Contoso_AD_Module.psm1”</span><span class="sxs-lookup"><span data-stu-id="8a713-182">In PowerShell ISE, open "Contoso_AD_Module.psm1"</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. <span data-ttu-id="8a713-183">按 Crtl+J 以打开代码片段菜单。</span><span class="sxs-lookup"><span data-stu-id="8a713-183">Press Crtl+J to open the snippets menu.</span></span>

3. <span data-ttu-id="8a713-184">按着下箭头键直到你找到“function”，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="8a713-184">Key down until you find "function" and press enter.</span></span>
<span data-ttu-id="8a713-185">这将显示函数最基本的主干。</span><span class="sxs-lookup"><span data-stu-id="8a713-185">This puts up a super basic skeleton of a function.</span></span>

4. <span data-ttu-id="8a713-186">将函数重命名为“Reset-ContosoUserPassword”。</span><span class="sxs-lookup"><span data-stu-id="8a713-186">Rename the function "Reset-ContosoUserPassword".</span></span>  

5. <span data-ttu-id="8a713-187">将参数之一重命名为“Identity”，并删除另一参数。</span><span class="sxs-lookup"><span data-stu-id="8a713-187">Rename one of the parameters "Identity" and delete the second.</span></span>

6. <span data-ttu-id="8a713-188">将以下内容复制到该函数的正文。</span><span class="sxs-lookup"><span data-stu-id="8a713-188">Copy the following into the body of the function.</span></span>
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. <span data-ttu-id="8a713-189">保存该文件。</span><span class="sxs-lookup"><span data-stu-id="8a713-189">Save the file.</span></span>
<span data-ttu-id="8a713-190">最后，你应该得到如下所示的内容：</span><span class="sxs-lookup"><span data-stu-id="8a713-190">You should end up with something that looks like this:</span></span>
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
<span data-ttu-id="8a713-191">现在，你的用户可以轻松调用 `Reset-ContosoUserPassword` 而无需记忆创建安全字符串内联的语法。</span><span class="sxs-lookup"><span data-stu-id="8a713-191">Now, your users can simply call `Reset-ContosoUserPassword` and not have to remember the syntax to create a secure string inline.</span></span>

## <a name="step-4-edit-the-role-capability-file"></a><span data-ttu-id="8a713-192">步骤 4：编辑角色功能文件</span><span class="sxs-lookup"><span data-stu-id="8a713-192">Step 4: Edit the Role Capability File</span></span>
<span data-ttu-id="8a713-193">在[角色功能创建](./role-capabilities.md#role-capability-creation)部分，已创建一个空白的角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="8a713-193">In the [Role Capability Creation](./role-capabilities.md#role-capability-creation) section, you created a blank Role Capability file.</span></span>
<span data-ttu-id="8a713-194">在本部分中，你将在该文件中填充值。</span><span class="sxs-lookup"><span data-stu-id="8a713-194">In this section, you will fill in the values in that file.</span></span>

<span data-ttu-id="8a713-195">首先在 PowerShell ISE 中打开该角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="8a713-195">Start by opening the role capability file in PowerShell ISE.</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
<span data-ttu-id="8a713-196">使用以下更改更新文件：</span><span class="sxs-lookup"><span data-stu-id="8a713-196">Update the file with the following changes:</span></span>
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

<span data-ttu-id="8a713-197">有关上述部分，需要注意以下几点：</span><span class="sxs-lookup"><span data-stu-id="8a713-197">There are a few things to note about the above:</span></span>
1.  <span data-ttu-id="8a713-198">PowerShell 将尝试自动加载你的角色功能所需的模块。</span><span class="sxs-lookup"><span data-stu-id="8a713-198">PowerShell will attempt to auto-load the modules needed for your Role Capability.</span></span>
<span data-ttu-id="8a713-199">如果你注意到未自动加载模块的问题，可能需要在“ModulesToImport”字段中显式列出模块名称。</span><span class="sxs-lookup"><span data-stu-id="8a713-199">You may need to explicitly list module names in the "ModulesToImport" field if you notice problems with a module not being autoloaded.</span></span>

2.  <span data-ttu-id="8a713-200">如果你不确定某命令是 cmdlet 还是函数，请运行 `Get-Command` 并查看“CommandType”属性</span><span class="sxs-lookup"><span data-stu-id="8a713-200">If you aren't sure if a command is a cmdlet or a function, run `Get-Command` and look at the "CommandType" property</span></span>

3.  <span data-ttu-id="8a713-201">如果不易定义一组允许的值，可通过 ValidatePattern 使用正则表达式来限制形参实参。</span><span class="sxs-lookup"><span data-stu-id="8a713-201">The ValidatePattern allows you to use a regular expression to restrict parameter arguments if it is not easy to define a set of allowable values.</span></span>
<span data-ttu-id="8a713-202">不能为单个参数同时定义 ValidatePattern 和 ValidateSet。</span><span class="sxs-lookup"><span data-stu-id="8a713-202">You cannot define both a ValidatePattern and ValidateSet for a single parameter.</span></span>

## <a name="step-5-register-a-new-session-configuration"></a><span data-ttu-id="8a713-203">步骤 5：注册新会话配置</span><span class="sxs-lookup"><span data-stu-id="8a713-203">Step 5: Register a new Session Configuration</span></span>
<span data-ttu-id="8a713-204">接下来，你将创建新的会话配置文件，该文件将向“JEA_NonAdmin_HelpDesk”AD 组的成员公开你的角色功能。</span><span class="sxs-lookup"><span data-stu-id="8a713-204">Next, you will create a new session configuration file that will expose your Role Capability to members of the "JEA_NonAdmin_HelpDesk" AD group.</span></span>

<span data-ttu-id="8a713-205">首先在 PowerShell ISE 中创建并打开新的空白会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="8a713-205">Start by creating and opening a new blank Session Configuration file in PowerShell ISE.</span></span>
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
<span data-ttu-id="8a713-206">修改 PSSC 文件中的以下字段。</span><span class="sxs-lookup"><span data-stu-id="8a713-206">Modify the following fields in the PSSC file.</span></span>
<span data-ttu-id="8a713-207">如果你正在自己的环境中工作，应将“CONTOSO\JEA_NonAdmins_Helpdesk”替换为你自己的非管理员用户或组。</span><span class="sxs-lookup"><span data-stu-id="8a713-207">If you are working in your own environment, you should replace "CONTOSO\JEA_NonAdmins_Helpdesk" with your own non-administrator user or group.</span></span>
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
<span data-ttu-id="8a713-208">保存并注册会话配置</span><span class="sxs-lookup"><span data-stu-id="8a713-208">Save and register the Session Configuration</span></span>
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## <a name="test-it-out"></a><span data-ttu-id="8a713-209">动手检验吧！</span><span class="sxs-lookup"><span data-stu-id="8a713-209">Test It Out!</span></span>
<span data-ttu-id="8a713-210">获取你的非管理员用户凭据：</span><span class="sxs-lookup"><span data-stu-id="8a713-210">Get your non-administrator user credentials:</span></span>
```PowerShell
$HelpDeskCred = Get-Credential
```
<span data-ttu-id="8a713-211">如果按照 [设置用户和组](creating-a-domain-controller.md#set-up-users-and-groups) 部分进行操作，则凭据如下：</span><span class="sxs-lookup"><span data-stu-id="8a713-211">If you followed the [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) section, the credentials will be:</span></span>
-   <span data-ttu-id="8a713-212">用户名 =“HelpDeskUser”</span><span class="sxs-lookup"><span data-stu-id="8a713-212">Username = "HelpDeskUser"</span></span>
-   <span data-ttu-id="8a713-213">密码 =“pa$ $w0rd”</span><span class="sxs-lookup"><span data-stu-id="8a713-213">Password = "pa$$w0rd"</span></span>

<span data-ttu-id="8a713-214">使用非管理员凭据远程登录到 AD 支持人员终结点：</span><span class="sxs-lookup"><span data-stu-id="8a713-214">Remote into the ADHelpdesk endpoint using the non-admin credential:</span></span>
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
<span data-ttu-id="8a713-215">使用 Set-ADUser 重置用户的职务。</span><span class="sxs-lookup"><span data-stu-id="8a713-215">Use Set-ADUser to reset a user's title.</span></span>
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
<span data-ttu-id="8a713-216">验证职务是否已更改。</span><span class="sxs-lookup"><span data-stu-id="8a713-216">Verify that the title has changed.</span></span>
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
<span data-ttu-id="8a713-217">现在，使用 Add-ADGroupMember 将用户添加到 TestGroup。</span><span class="sxs-lookup"><span data-stu-id="8a713-217">Now, use Add-ADGroupMember to add a user to the TestGroup.</span></span>
<span data-ttu-id="8a713-218">注意：请确保事先创建了 TestGroup。</span><span class="sxs-lookup"><span data-stu-id="8a713-218">Note: make sure you've created the TestGroup beforehand.</span></span>
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
<span data-ttu-id="8a713-219">退出会话：</span><span class="sxs-lookup"><span data-stu-id="8a713-219">Exit the session:</span></span>
```PowerShell
Exit-PSSession
```
## <a name="key-concepts"></a><span data-ttu-id="8a713-220">关键概念</span><span class="sxs-lookup"><span data-stu-id="8a713-220">Key Concepts</span></span>
<span data-ttu-id="8a713-221">**NoLanguage 模式**：当 PowerShell 处于“NoLanguage”模式时，用户仅能运行命令，而不能使用任何语言元素。</span><span class="sxs-lookup"><span data-stu-id="8a713-221">**NoLanguage Mode**: When PowerShell is in "NoLanguage" mode, users may only run commands; they cannot use any language elements.</span></span>
<span data-ttu-id="8a713-222">有关详细信息，请运行 `Get-Help about_Language_Modes`。</span><span class="sxs-lookup"><span data-stu-id="8a713-222">For more information, run `Get-Help about_Language_Modes`.</span></span>

<span data-ttu-id="8a713-223">**PowerShell 函数**：PowerShell 函数是可以按名称调用的小型 PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="8a713-223">**PowerShell Functions**: PowerShell functions are bits of PowerShell code that you can call by name.</span></span>
<span data-ttu-id="8a713-224">有关详细信息，请运行 `Get-Help about_Functions`。</span><span class="sxs-lookup"><span data-stu-id="8a713-224">For more information, run `Get-Help about_Functions`.</span></span>

<span data-ttu-id="8a713-225">**ValidateSet/ValidatePattern**：公开命令时，你可以限制特定形参的有效实参。</span><span class="sxs-lookup"><span data-stu-id="8a713-225">**ValidateSet/ValidatePattern**: When exposing a command, you can restrict valid arguments for specific parameters.</span></span>
<span data-ttu-id="8a713-226">ValidateSet 是有效实参的特定列表。</span><span class="sxs-lookup"><span data-stu-id="8a713-226">A ValidateSet is a specific list of valid arguments.</span></span>
<span data-ttu-id="8a713-227">ValidatePattern 是该形参的实参必须匹配的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="8a713-227">A ValidatePattern is a regular expression that the arguments for that parameter must match.</span></span>

