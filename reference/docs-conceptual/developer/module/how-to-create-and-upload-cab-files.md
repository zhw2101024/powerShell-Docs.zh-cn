---
title: 如何创建和上传 CAB 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367326"
---
# <a name="how-to-create-and-upload-cab-files"></a><span data-ttu-id="7da3a-102">如何创建和上传 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="7da3a-102">How to Create and Upload CAB Files</span></span>

<span data-ttu-id="7da3a-103">本主题说明如何创建可更新的帮助 CAB 文件，并将其上载到可更新的帮助 cmdlet 可以找到它们的位置。</span><span class="sxs-lookup"><span data-stu-id="7da3a-103">This topic explains how to create Updatable Help CAB files and upload them to the location where the Updatable Help cmdlets can find them.</span></span>

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a><span data-ttu-id="7da3a-104">如何创建和上传可更新的帮助 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="7da3a-104">How to Create and Upload Updatable Help CAB Files</span></span>

<span data-ttu-id="7da3a-105">您可以使用 "可更新的帮助" 功能，为多语言和区域性中的模块提供新的或更新的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-105">You can use the Updatable Help feature to deliver new or updated help files for a module in multiple languages and cultures.</span></span> <span data-ttu-id="7da3a-106">模块的可更新帮助包由一个 HelpInfo XML 文件和一个或多个 cabinet （。CAB）文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-106">An Updatable Help package for a module consists of one HelpInfo XML file and one or more cabinet (.CAB) files.</span></span> <span data-ttu-id="7da3a-107">每个 CAB 文件都包含一个 UI 区域性中的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-107">Each CAB file contains help files for the module in one UI culture.</span></span> <span data-ttu-id="7da3a-108">使用以下过程来创建可更新帮助的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-108">Use the following procedure to create CAB files for Updatable Help.</span></span>

1. <span data-ttu-id="7da3a-109">按 UI 区域性组织模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-109">Organize the help files for the module by UI culture.</span></span> <span data-ttu-id="7da3a-110">每个可更新帮助 CAB 文件都包含一个 UI 区域性中某个模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-110">Each Updatable Help CAB file contains the help files for one module in one UI culture.</span></span> <span data-ttu-id="7da3a-111">可以为模块提供多个帮助 CAB 文件，每个文件都适用于不同的 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="7da3a-111">You can deliver multiple help CAB files for the module, each for a different UI culture.</span></span>

2. <span data-ttu-id="7da3a-112">验证 "帮助" 文件只包含可更新帮助所允许的文件类型，并根据帮助文件架构对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="7da3a-112">Verify that help files include only the file types permitted for Updatable Help and validate them against a help file schema.</span></span> <span data-ttu-id="7da3a-113">如果 `Update-Help` cmdlet 遇到无效的文件或该文件不是允许的类型，则它不会安装无效文件，也不会停止从 CAB 安装文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-113">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB.</span></span> <span data-ttu-id="7da3a-114">有关允许的文件类型的列表，请参阅[可更新的帮助 CAB 文件中允许的文件类型](./file-types-permitted-in-an-updatable-help-cab-file.md)。</span><span class="sxs-lookup"><span data-stu-id="7da3a-114">For a list of permitted file types, see [File Types Permitted in an Updatable Help CAB File](./file-types-permitted-in-an-updatable-help-cab-file.md).</span></span>

3. <span data-ttu-id="7da3a-115">对帮助文件进行数字签名。</span><span class="sxs-lookup"><span data-stu-id="7da3a-115">Digitally sign the help files.</span></span> <span data-ttu-id="7da3a-116">不需要数字签名，但这是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="7da3a-116">Digital signatures are not required, but they are a best practice.</span></span>

4. <span data-ttu-id="7da3a-117">包括 UI 区域性中的模块的所有帮助文件，而不仅是新的或已更改的文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-117">Include all of help files for the module in the UI culture, not only files that are new or have changed.</span></span> <span data-ttu-id="7da3a-118">如果 CAB 文件不完整，则首次下载帮助文件或不下载每个更新的用户将不会获得所有的模块帮助文件。</span><span class="sxs-lookup"><span data-stu-id="7da3a-118">If the CAB file is incomplete, users who download help files for the first time or do not download every update, will not have all of the module help files.</span></span>

5. <span data-ttu-id="7da3a-119">使用创建 cabinet 文件的实用程序，如 MakeCab。</span><span class="sxs-lookup"><span data-stu-id="7da3a-119">Use a utility that creates cabinet files, such as MakeCab.exe.</span></span> <span data-ttu-id="7da3a-120">Windows PowerShell 不包含用于创建 CAB 文件的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7da3a-120">Windows PowerShell does not include cmdlets that create CAB files.</span></span>

6. <span data-ttu-id="7da3a-121">将 CAB 文件命名为。</span><span class="sxs-lookup"><span data-stu-id="7da3a-121">Name the CAB files.</span></span> <span data-ttu-id="7da3a-122">有关详细信息，请参阅[如何命名可更新的帮助 CAB 文件](./how-to-name-an-updatable-help-cab-file.md)。</span><span class="sxs-lookup"><span data-stu-id="7da3a-122">For more information, see [How to Name an Updatable Help CAB File](./how-to-name-an-updatable-help-cab-file.md).</span></span>

7. <span data-ttu-id="7da3a-123">将模块的 CAB 文件上传到模块的 HelpInfo XML 文件中的**HelpContentUri**元素指定的位置。</span><span class="sxs-lookup"><span data-stu-id="7da3a-123">Upload the CAB files for the module to the location that is specified by the **HelpContentUri** element in the HelpInfo XML file for the module.</span></span> <span data-ttu-id="7da3a-124">然后，将 HelpInfo XML 文件上传到模块清单的**HelpInfoUri**键指定的位置。</span><span class="sxs-lookup"><span data-stu-id="7da3a-124">Then upload the HelpInfo XML file to the location that is specified by the **HelpInfoUri** key of the module manifest.</span></span> <span data-ttu-id="7da3a-125">**HelpContentUri**和**HelpInfoUri**可以指向相同的位置。</span><span class="sxs-lookup"><span data-stu-id="7da3a-125">The **HelpContentUri** and **HelpInfoUri** can point to the same location.</span></span>

> [!CAUTION]
> <span data-ttu-id="7da3a-126">**HelpInfoUri**键和**HelpContentUri**元素的值必须以 "http" 或 "https" 开头。</span><span class="sxs-lookup"><span data-stu-id="7da3a-126">The value of the **HelpInfoUri** key and the **HelpContentUri** element must begin with "http" or "https".</span></span> <span data-ttu-id="7da3a-127">该值必须指示 Internet 位置，并且不能包含文件名。</span><span class="sxs-lookup"><span data-stu-id="7da3a-127">The value must indicate an Internet location and it must not include a file name.</span></span>