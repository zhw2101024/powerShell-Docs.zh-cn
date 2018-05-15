---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: 需要接受许可证的模块
ms.openlocfilehash: fe197ea271e18580a221ad4d5245b685bd81775b
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="modules-requiring-license-acceptance"></a>需要接受许可证的模块

## <a name="synopsis"></a>简述

某些模块发布者的法律部门需要客户在从 PowerShell 库安装其模块之前，必须明确接受许可证。 如果用户使用 PowerShellGet 安装、更新或保存模块（无论是以直接方式还是作为另一个项的依赖项），并且该模块需要用户同意许可证，则用户必须表示其接受学科正，否则操作将失败。

## <a name="publish-requirements-for-modules"></a>发布模块的要求

需要用户接受许可证的模块应满足以下要求：

- 模块清单的 PSData 部分应包含 RequireLicenseAcceptance = $True。
- 模块应在根目录中包含 license.txt 文件。
- 模块清单应包含许可证 URI。
- 应使用 PowerShellGet 格式版本 2.0 和更高版本发布模块。

## <a name="impact-on-installsaveupdate-module"></a>对 Install/Save/Update-Module 的影响

- 安装/保存/更新 cmdlet 将支持新参数 – AcceptLicense，此参数的行为就好像用户看到了许可证。
- 如果 RequiredLicenseAcceptance 为 True 且未指定 –AcceptLicense，系统将向用户显示 license.txt 并提示：&quot;是否接受这些许可条款（是/否/全部选是/全部选否）&quot;。
  - 如果接受许可证
    - **Save-Module：** 将把模块复制到用户系统中
    - **Install-Module：** 将把模块复制到用户系统的适当文件夹中（基于作用域）
    - **Update-Module：** 将更新该模块。
  - 如果拒绝许可证。
    - 操作将被取消。
- 所有 cmdlet 都会检查表明需要接受许可证的元数据（requireLicenseAcceptance 和格式版本）
  - 如果客户端的格式版本早于 2.0，操作将失败，并要求用户更新客户端。
  - 如果使用早于 2.0 的版本格式发布模块，将忽略 requireLicenseAcceptance 标记。


 ## <a name="module-dependencies"></a>模块依赖项
- 在安装/保存/更新操作期间，如果依赖模块（依赖于该模块的其他内容）需要接受许可证，则将需要接受许可证行为（上述）。
- 如果在系统中安装模块时已在本地目录中列出模块版本，我们将绕过许可证检查。
- 在安装/保存/更新操作期间，如果依赖模块需要许可证，且接受许可证并未发生，则操作将失败，并遵循项安装/保存/更新失败的正常流程。

 ## <a name="impact-on--force"></a>对 -Force 的影响

指定 – Force 不足以接受许可证。 – AcceptLicense 是获取安装权限的必要条件。 如果指定 – Force，RequiredLicenseAcceptance 为 True ，且未指定 – AcceptLicense 时，操作将失败。

## <a name="examples"></a>示例

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>示例 1：更新模块清单以需要接受许可证

```PowerShell
PS> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

此命令会更新清单文件，并将 RequireLicenseAcceptance 标记设置为 true。

### <a name="example-2-install-module-requiring-license-acceptance"></a>示例 2：安装需要接受许可证的模块

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance

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

此命令显示了 license.txt 文件中的许可证，并提示用户接受许可证。

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>示例 3：安装需要接受许可证及 -AcceptLicense 的模块

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

在未提示接受许可证的情况下安装模块。

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>示例 4：安装需要接受许可证及 -Force 的模块

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>示例 5：安装模块及需要接受许可证的依赖项

模块“ModuleWithDependency”依赖于模块“ModuleRequireLicenseAcceptance”。 系统提示用户接受许可证。

```PowerShell
PS> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>示例 6：安装模块以及需要接受许可证和 -AcceptLicense 的依赖项

模块“ModuleWithDependency”依赖于模块“ModuleRequireLicenseAcceptance”。 系统不提示用户接受许可证，因为已指定 -AcceptLicense。

```PowerShell
PS>  Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>示例 7：安装需要在早于 PSGetFormatVersion 2.0 的客户端上接受许可证的模块

```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```

### <a name="example-8-save-module-requiring-license-acceptance"></a>示例 8：保存需要接受许可证的模块

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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

此命令显示了 license.txt 文件中的许可证，并提示用户接受许可证。

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>示例 9：保存需要接受许可证及 -AcceptLicense 的模块

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

在未提示接受许可证的情况下保存模块。

### <a name="example-10-update-module-requiring-license-acceptance"></a>示例 10：更新需要接受许可证的模块

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance

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

此命令显示了 license.txt 文件中的许可证，并提示用户接受许可证。

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>示例 11：更新需要接受许可证及 -AcceptLicense 的模块

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

在未提示接受许可证的情况下更新模块。

## <a name="more-details"></a>详细信息

### <a name="require-license-acceptance-for-scriptsscript-license-acceptancemd"></a>[需要为脚本接受许可证](./script-license-acceptance.md)

### <a name="require-license-acceptance-support-on-powershellgalleryhow-toworking-with-itemsitems-that-require-license-acceptancemd"></a>[PowerShellGallery 上的需要接受许可证支持](../how-to/working-with-items/items-that-require-license-acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationhow-toworking-with-itemsdeploy-to-azure-automationmd"></a>[在部署到 Azure 自动化时需要接受许可证](../how-to/working-with-items/deploy-to-azure-automation.md)