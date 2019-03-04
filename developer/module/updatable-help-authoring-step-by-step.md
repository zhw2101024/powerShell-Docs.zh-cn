---
title: 可更新帮助创作：Step-by-Step | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860313"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="41df6-102">可更新帮助创作：分步指南</span><span class="sxs-lookup"><span data-stu-id="41df6-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="41df6-103">此文档列出了创作可更新帮助的过程中的步骤。</span><span class="sxs-lookup"><span data-stu-id="41df6-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="41df6-104">创作可更新的帮助：分步指南</span><span class="sxs-lookup"><span data-stu-id="41df6-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="41df6-105">可更新的帮助，专门用于最终用户，但它还提供对模块作者的好处很明显，帮助编写器，包括能够添加内容，修复错误，提供在多个 UI 区域性，并响应用户注释和请求，长时间后模块已发货。</span><span class="sxs-lookup"><span data-stu-id="41df6-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="41df6-106">本主题介绍如何打包并上传的帮助文件，以便用户可以下载并使用安装[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="41df6-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="41df6-107">以下步骤概述了支持可更新帮助的过程。</span><span class="sxs-lookup"><span data-stu-id="41df6-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="41df6-108">步骤 1：为帮助文件中查找 Internet 的站点</span><span class="sxs-lookup"><span data-stu-id="41df6-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="41df6-109">创建可更新帮助的第一步是查找您的模块的帮助文件的 Internet 位置。</span><span class="sxs-lookup"><span data-stu-id="41df6-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="41df6-110">实际上，您可以使用两个不同位置。</span><span class="sxs-lookup"><span data-stu-id="41df6-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="41df6-111">您可以将一个 Internet 位置和另一个 Internet 位置的帮助内容的 CAB 文件保留您的模块的帮助信息文件 (HelpInfo XML-如下所述)。</span><span class="sxs-lookup"><span data-stu-id="41df6-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="41df6-112">所有帮助内容 CAB 文件的模块必须都位于同一位置。</span><span class="sxs-lookup"><span data-stu-id="41df6-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="41df6-113">可以将不同的模块的帮助内容 CAB 文件放在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="41df6-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="41df6-114">步骤 2：将 HelpInfoURI 密钥添加到模块清单</span><span class="sxs-lookup"><span data-stu-id="41df6-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="41df6-115">添加**HelpInfoURI**向模块清单键。</span><span class="sxs-lookup"><span data-stu-id="41df6-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="41df6-116">键的值是位置的您的模块的 HelpInfo XML 信息文件的统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="41df6-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="41df6-117">为了安全，地址必须以"http"或"https"开头。</span><span class="sxs-lookup"><span data-stu-id="41df6-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="41df6-118">URI 应指定 Internet 位置，但不能包含 HelpInfo XML 文件名称。</span><span class="sxs-lookup"><span data-stu-id="41df6-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="41df6-119">例如：</span><span class="sxs-lookup"><span data-stu-id="41df6-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="41df6-120">步骤 3：创建 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="41df6-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="41df6-121">HelpInfo XML 信息文件包含您的帮助文件和每个受支持的 UI 区域性中模块的最新帮助文件的版本号的 Internet 位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="41df6-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="41df6-122">每个 Windows PowerShell 模块具有一个 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="41df6-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="41df6-123">当您更新您的帮助文件时，编辑或替换 HelpInfo XML 文件中;不添加另一个。</span><span class="sxs-lookup"><span data-stu-id="41df6-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="41df6-124">有关详细信息，请参阅[如何创建 HelpInfo XML 文件](./how-to-create-a-helpinfo-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="41df6-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="41df6-125">步骤 4：登录您的帮助文件</span><span class="sxs-lookup"><span data-stu-id="41df6-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="41df6-126">数字签名不是必需的但它们是建议的最佳做法，只要共享文件。</span><span class="sxs-lookup"><span data-stu-id="41df6-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="41df6-127">步骤 5：创建 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="41df6-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="41df6-128">使用创建 cabinet (.cab) 文件，如 MakeCab.exe，若要创建的工具。包含有关你的模块的帮助文件的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="41df6-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="41df6-129">每个受支持的 UI 区域性中创建单独的 CAB 文件适用于帮助文件。</span><span class="sxs-lookup"><span data-stu-id="41df6-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="41df6-130">有关详细信息，请参阅[如何准备可更新帮助的 CAB 文件](./how-to-prepare-updatable-help-cab-files.md)。</span><span class="sxs-lookup"><span data-stu-id="41df6-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="41df6-131">步骤 6：将文件上传</span><span class="sxs-lookup"><span data-stu-id="41df6-131">Step 6: Upload your files</span></span>

<span data-ttu-id="41df6-132">若要发布新的或更新的帮助文件，请将 CAB 文件上载到由指定的 Internet 位置**HelpContentUri** HelpInfo XML 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="41df6-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="41df6-133">然后，将 HelpInfo XML 文件上传到的值所指定的 Internet 位置**HelpInfoUri**密钥模块清单中。</span><span class="sxs-lookup"><span data-stu-id="41df6-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
