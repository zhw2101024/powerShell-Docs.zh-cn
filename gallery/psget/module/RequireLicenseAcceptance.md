---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: RequireLicenseAcceptance
ms.openlocfilehash: d78f8cb7f84869880e9a88a0f0407d18dc5c64cb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="85b4b-103">需要接受许可证的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="85b4b-104">简述</span><span class="sxs-lookup"><span data-stu-id="85b4b-104">SYNOPSIS</span></span>
<span data-ttu-id="85b4b-105">某些模块发布者的法律部门需要客户在从 PowerShell 库安装其模块之前，必须明确接受许可证。</span><span class="sxs-lookup"><span data-stu-id="85b4b-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="85b4b-106">如果用户使用 PowerShellGet 安装、更新或保存模块（无论是以直接方式还是作为另一个项的依赖项），并且该模块需要用户同意许可证，则用户必须表示其接受学科正，否则操作将失败。</span><span class="sxs-lookup"><span data-stu-id="85b4b-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="85b4b-107">发布模块的要求</span><span class="sxs-lookup"><span data-stu-id="85b4b-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="85b4b-108">需要用户接受许可证的模块应满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="85b4b-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="85b4b-109">模块清单的 PSData 部分应包含 RequireLicenseAcceptance = $True。</span><span class="sxs-lookup"><span data-stu-id="85b4b-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="85b4b-110">模块应在根目录中包含 license.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="85b4b-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="85b4b-111">模块清单应包含许可证 URI。</span><span class="sxs-lookup"><span data-stu-id="85b4b-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="85b4b-112">应使用 PowerShellGet 格式版本 2.0 和更高版本发布模块。</span><span class="sxs-lookup"><span data-stu-id="85b4b-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="85b4b-113">对 Install/Save/Update-Module 的影响</span><span class="sxs-lookup"><span data-stu-id="85b4b-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="85b4b-114">安装/保存/更新 cmdlet 将支持新参数 – AcceptLicense，此参数的行为就好像用户看到了许可证。</span><span class="sxs-lookup"><span data-stu-id="85b4b-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="85b4b-115">如果 RequiredLicenseAcceptance 为 True 且未指定 –AcceptLicense，系统将向用户显示 license.txt 并提示：&quot;是否接受这些许可条款（是/否/全部选是/全部选否）&quot;。</span><span class="sxs-lookup"><span data-stu-id="85b4b-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="85b4b-116">如果接受许可证</span><span class="sxs-lookup"><span data-stu-id="85b4b-116">If the license is accepted</span></span>
    - <span data-ttu-id="85b4b-117">**Save-Module：**将把模块复制到用户系统中</span><span class="sxs-lookup"><span data-stu-id="85b4b-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="85b4b-118">**Install-Module：**将把模块复制到用户系统的适当文件夹中（基于作用域）</span><span class="sxs-lookup"><span data-stu-id="85b4b-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="85b4b-119">**Update-Module：**将更新该模块。</span><span class="sxs-lookup"><span data-stu-id="85b4b-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="85b4b-120">如果拒绝许可证。</span><span class="sxs-lookup"><span data-stu-id="85b4b-120">If the license is declined.</span></span>
    - <span data-ttu-id="85b4b-121">操作将被取消。</span><span class="sxs-lookup"><span data-stu-id="85b4b-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="85b4b-122">所有 cmdlet 都会检查表明需要接受许可证的元数据（requireLicenseAcceptance 和格式版本）</span><span class="sxs-lookup"><span data-stu-id="85b4b-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="85b4b-123">如果客户端的格式版本早于 2.0，操作将失败，并要求用户更新客户端。</span><span class="sxs-lookup"><span data-stu-id="85b4b-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="85b4b-124">如果使用早于 2.0 的版本格式发布模块，将忽略 requireLicenseAcceptance 标记。</span><span class="sxs-lookup"><span data-stu-id="85b4b-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>


 ## <a name="module-dependencies"></a><span data-ttu-id="85b4b-125">模块依赖项</span><span class="sxs-lookup"><span data-stu-id="85b4b-125">Module Dependencies</span></span>
- <span data-ttu-id="85b4b-126">在安装/保存/更新操作期间，如果依赖模块（依赖于该模块的其他内容）需要接受许可证，则将需要接受许可证行为（上述）。</span><span class="sxs-lookup"><span data-stu-id="85b4b-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="85b4b-127">如果在系统中安装模块时已在本地目录中列出模块版本，我们将绕过许可证检查。</span><span class="sxs-lookup"><span data-stu-id="85b4b-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="85b4b-128">在安装/保存/更新操作期间，如果依赖模块需要许可证，且接受许可证并未发生，则操作将失败，并遵循项安装/保存/更新失败的正常流程。</span><span class="sxs-lookup"><span data-stu-id="85b4b-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="85b4b-129">对 -Force 的影响</span><span class="sxs-lookup"><span data-stu-id="85b4b-129">Impact on -Force</span></span>

<span data-ttu-id="85b4b-130">指定 – Force 不足以接受许可证。</span><span class="sxs-lookup"><span data-stu-id="85b4b-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="85b4b-131">– AcceptLicense 是获取安装权限的必要条件。</span><span class="sxs-lookup"><span data-stu-id="85b4b-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="85b4b-132">如果指定 – Force，RequiredLicenseAcceptance 为 True ，且未指定 – AcceptLicense 时，操作将失败。</span><span class="sxs-lookup"><span data-stu-id="85b4b-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="85b4b-133">示例</span><span class="sxs-lookup"><span data-stu-id="85b4b-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="85b4b-134">示例 1：更新模块清单以需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="85b4b-134">Example 1: Update Module Manifest to require license acceptance</span></span>
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```
<span data-ttu-id="85b4b-135">此命令会更新清单文件，并将 RequireLicenseAcceptance 标记设置为 true。</span><span class="sxs-lookup"><span data-stu-id="85b4b-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>
### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="85b4b-136">示例 2：安装需要接受许可证的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-136">Example 2: Install Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):

```
<span data-ttu-id="85b4b-137">此命令显示了 license.txt 文件中的许可证，并提示用户接受许可证。</span><span class="sxs-lookup"><span data-stu-id="85b4b-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="85b4b-138">示例 3：安装需要接受许可证及 -AcceptLicense 的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="85b4b-139">在未提示接受许可证的情况下安装模块。</span><span class="sxs-lookup"><span data-stu-id="85b4b-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="85b4b-140">示例 4：安装需要接受许可证及 -Force 的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-140">Example 4: Install Module requiring license acceptance with -Force</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="85b4b-141">示例 5：安装模块及需要接受许可证的依赖项</span><span class="sxs-lookup"><span data-stu-id="85b4b-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>
<span data-ttu-id="85b4b-142">模块“ModuleWithDependency”依赖于模块“ModuleRequireLicenseAcceptance”。</span><span class="sxs-lookup"><span data-stu-id="85b4b-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="85b4b-143">系统提示用户接受许可证。</span><span class="sxs-lookup"><span data-stu-id="85b4b-143">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleWithDependency

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="85b4b-144">示例 6：安装模块以及需要接受许可证和 -AcceptLicense 的依赖项</span><span class="sxs-lookup"><span data-stu-id="85b4b-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="85b4b-145">模块“ModuleWithDependency”依赖于模块“ModuleRequireLicenseAcceptance”。</span><span class="sxs-lookup"><span data-stu-id="85b4b-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="85b4b-146">系统不提示用户接受许可证，因为已指定 -AcceptLicense。</span><span class="sxs-lookup"><span data-stu-id="85b4b-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="85b4b-147">示例 7：安装需要在早于 PSGetFormatVersion 2.0 的客户端上接受许可证的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="85b4b-148">示例 8：保存需要接受许可证的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-148">Example 8: Save Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```
<span data-ttu-id="85b4b-149">此命令显示了 license.txt 文件中的许可证，并提示用户接受许可证。</span><span class="sxs-lookup"><span data-stu-id="85b4b-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="85b4b-150">示例 9：保存需要接受许可证及 -AcceptLicense 的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
<span data-ttu-id="85b4b-151">在未提示接受许可证的情况下保存模块。</span><span class="sxs-lookup"><span data-stu-id="85b4b-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="85b4b-152">示例 10：更新需要接受许可证的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-152">Example 10: Update Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```
<span data-ttu-id="85b4b-153">此命令显示了 license.txt 文件中的许可证，并提示用户接受许可证。</span><span class="sxs-lookup"><span data-stu-id="85b4b-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="85b4b-154">示例 11：更新需要接受许可证及 -AcceptLicense 的模块</span><span class="sxs-lookup"><span data-stu-id="85b4b-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="85b4b-155">在未提示接受许可证的情况下更新模块。</span><span class="sxs-lookup"><span data-stu-id="85b4b-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="85b4b-156">详细信息</span><span class="sxs-lookup"><span data-stu-id="85b4b-156">More details</span></span>
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[<span data-ttu-id="85b4b-157">需要为脚本接受许可证</span><span class="sxs-lookup"><span data-stu-id="85b4b-157">Require License Acceptance for Scripts</span></span>](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="85b4b-158">PowerShellGallery 上的需要接受许可证支持</span><span class="sxs-lookup"><span data-stu-id="85b4b-158">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="85b4b-159">在部署到 Azure 自动化时需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="85b4b-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)