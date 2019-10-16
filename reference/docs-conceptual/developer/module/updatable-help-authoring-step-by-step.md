---
title: 可更新的帮助创作：分步 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366986"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="7d58a-102">可更新帮助创作：分步</span><span class="sxs-lookup"><span data-stu-id="7d58a-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="7d58a-103">此文档列出了创作可更新帮助的过程中的步骤。</span><span class="sxs-lookup"><span data-stu-id="7d58a-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="7d58a-104">创作可更新帮助：分步</span><span class="sxs-lookup"><span data-stu-id="7d58a-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="7d58a-105">可更新帮助是为最终用户设计的，但它还为模块作者和帮助编写人员提供了显著的好处，包括添加内容、修复错误、在多个 UI 区域性中交付以及响应用户注释和请求的能力，长时间之后模块已寄送。</span><span class="sxs-lookup"><span data-stu-id="7d58a-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="7d58a-106">本主题介绍如何打包和上传帮助文件，以便用户可以使用[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[get-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 下载和安装帮助文件。</span><span class="sxs-lookup"><span data-stu-id="7d58a-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="7d58a-107">以下步骤概述了支持可更新帮助的过程。</span><span class="sxs-lookup"><span data-stu-id="7d58a-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="7d58a-108">步骤1：查找帮助文件的 Internet 站点</span><span class="sxs-lookup"><span data-stu-id="7d58a-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="7d58a-109">创建可更新帮助的第一步是在 Internet 位置查找模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="7d58a-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="7d58a-110">实际上，可以使用两个不同的位置。</span><span class="sxs-lookup"><span data-stu-id="7d58a-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="7d58a-111">可以在一个 Internet 位置将模块的帮助信息文件（HelpInfo XML）保存在一个 Internet 位置，并将帮助内容 CAB 文件保留在另一个 Internet 位置。</span><span class="sxs-lookup"><span data-stu-id="7d58a-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="7d58a-112">模块的所有帮助内容 CAB 文件都必须位于同一位置。</span><span class="sxs-lookup"><span data-stu-id="7d58a-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="7d58a-113">可以将不同模块的帮助内容 CAB 文件放置在同一位置。</span><span class="sxs-lookup"><span data-stu-id="7d58a-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="7d58a-114">步骤2：将 HelpInfoURI 键添加到模块清单</span><span class="sxs-lookup"><span data-stu-id="7d58a-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="7d58a-115">将**HelpInfoURI**键添加到模块清单中。</span><span class="sxs-lookup"><span data-stu-id="7d58a-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="7d58a-116">键的值是模块的 HelpInfo XML 信息文件位置的统一资源标识符（URI）。</span><span class="sxs-lookup"><span data-stu-id="7d58a-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="7d58a-117">为安全，该地址必须以 "http" 或 "https" 开头。</span><span class="sxs-lookup"><span data-stu-id="7d58a-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="7d58a-118">URI 应指定 Internet 位置，但不得包含 HelpInfo XML 文件名。</span><span class="sxs-lookup"><span data-stu-id="7d58a-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="7d58a-119">例如：</span><span class="sxs-lookup"><span data-stu-id="7d58a-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="7d58a-120">步骤3：创建 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="7d58a-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="7d58a-121">HelpInfo XML 信息文件包含帮助文件的 Internet 位置的 URI，以及每个受支持的 UI 区域性中的模块的最新帮助文件的版本号。</span><span class="sxs-lookup"><span data-stu-id="7d58a-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="7d58a-122">每个 Windows PowerShell 模块都有一个 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="7d58a-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="7d58a-123">更新帮助文件时，请编辑或替换 HelpInfo XML 文件;不添加另一个。</span><span class="sxs-lookup"><span data-stu-id="7d58a-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="7d58a-124">有关详细信息，请参阅[如何创建 HELPINFO XML 文件](./how-to-create-a-helpinfo-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="7d58a-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="7d58a-125">步骤4：签署帮助文件</span><span class="sxs-lookup"><span data-stu-id="7d58a-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="7d58a-126">数字签名并不是必需的，但在您共享文件时，这是最佳做法建议。</span><span class="sxs-lookup"><span data-stu-id="7d58a-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="7d58a-127">步骤5：创建 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="7d58a-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="7d58a-128">使用创建 cabinet 文件（.cab）的工具（如 MakeCab）来创建。CAB 文件，其中包含模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="7d58a-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="7d58a-129">为每个支持的 UI 区域性中的帮助文件创建单独的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="7d58a-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="7d58a-130">有关详细信息，请参阅[如何准备可更新的帮助 CAB 文件](./how-to-prepare-updatable-help-cab-files.md)。</span><span class="sxs-lookup"><span data-stu-id="7d58a-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="7d58a-131">步骤6：上传文件</span><span class="sxs-lookup"><span data-stu-id="7d58a-131">Step 6: Upload your files</span></span>

<span data-ttu-id="7d58a-132">若要发布新的或更新的帮助文件，请将 CAB 文件上传到 HelpInfo XML 文件中的**HelpContentUri**元素所指定的 Internet 位置。</span><span class="sxs-lookup"><span data-stu-id="7d58a-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="7d58a-133">然后，将 HelpInfo XML 文件上传到由模块清单中的**HelpInfoUri**键的值指定的 Internet 位置。</span><span class="sxs-lookup"><span data-stu-id="7d58a-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
