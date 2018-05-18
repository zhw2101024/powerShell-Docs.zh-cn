---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: 需要为脚本接受许可证
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="ebc5c-103">需要为脚本接受许可证</span><span class="sxs-lookup"><span data-stu-id="ebc5c-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="ebc5c-104">脚本不支持接受许可证。</span><span class="sxs-lookup"><span data-stu-id="ebc5c-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="ebc5c-105">但是，支持其中的脚本依赖于需要接受许可证的模块的方案。</span><span class="sxs-lookup"><span data-stu-id="ebc5c-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="ebc5c-106">脚本命令 (Install-Script/Save-Script/Update-Script) 支持新参数 -AcceptLicense，此参数的行为就好像用户看到了许可证。</span><span class="sxs-lookup"><span data-stu-id="ebc5c-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="ebc5c-107">如果未指定 -AcceptLicense，系统将向用户显示依赖模块的 license.txt，并提示用户接受许可证。</span><span class="sxs-lookup"><span data-stu-id="ebc5c-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="ebc5c-108">示例</span><span class="sxs-lookup"><span data-stu-id="ebc5c-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="ebc5c-109">示例 1：安装脚本及需要接受许可证的依赖项</span><span class="sxs-lookup"><span data-stu-id="ebc5c-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="ebc5c-110">脚本“ScriptRequireLicenseAcceptance”依赖于“ModuleRequireLicenseAcceptance”模块。</span><span class="sxs-lookup"><span data-stu-id="ebc5c-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="ebc5c-111">系统提示用户接受许可证。</span><span class="sxs-lookup"><span data-stu-id="ebc5c-111">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="ebc5c-112">示例 2：安装脚本及需要接受许可证和 -AcceptLicense 的依赖项</span><span class="sxs-lookup"><span data-stu-id="ebc5c-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="ebc5c-113">脚本“ScriptRequireLicenseAcceptance”依赖于“ModuleRequireLicenseAcceptance”模块。</span><span class="sxs-lookup"><span data-stu-id="ebc5c-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="ebc5c-114">系统不提示用户接受许可证，因为已指定 -AcceptLicense。</span><span class="sxs-lookup"><span data-stu-id="ebc5c-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="ebc5c-115">详细信息</span><span class="sxs-lookup"><span data-stu-id="ebc5c-115">More details</span></span>

- [<span data-ttu-id="ebc5c-116">模块的需要接受许可证支持</span><span class="sxs-lookup"><span data-stu-id="ebc5c-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="ebc5c-117">PowerShellGallery 上的需要接受许可证支持</span><span class="sxs-lookup"><span data-stu-id="ebc5c-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [<span data-ttu-id="ebc5c-118">在部署到 Azure 自动化时需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="ebc5c-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)