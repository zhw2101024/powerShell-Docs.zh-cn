---
title: 如何创建并上载 CAB 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082373"
---
# <a name="how-to-create-and-upload-cab-files"></a><span data-ttu-id="69017-102">如何创建和上传 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="69017-102">How to Create and Upload CAB Files</span></span>

<span data-ttu-id="69017-103">本主题说明如何创建可更新帮助的 CAB 文件并将其上载到其中的可更新帮助的 cmdlet 可以找到它们的位置。</span><span class="sxs-lookup"><span data-stu-id="69017-103">This topic explains how to create Updatable Help CAB files and upload them to the location where the Updatable Help cmdlets can find them.</span></span>

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a><span data-ttu-id="69017-104">如何创建和上传可更新帮助的 CAB 文件</span><span class="sxs-lookup"><span data-stu-id="69017-104">How to Create and Upload Updatable Help CAB Files</span></span>

<span data-ttu-id="69017-105">可更新帮助功能可用于提供新的或更新的帮助文件中多个语言和文化的模块。</span><span class="sxs-lookup"><span data-stu-id="69017-105">You can use the Updatable Help feature to deliver new or updated help files for a module in multiple languages and cultures.</span></span> <span data-ttu-id="69017-106">模块的可更新帮助包包含一个 HelpInfo XML 文件和一个或多个 cab 文件 (。CAB) 文件。</span><span class="sxs-lookup"><span data-stu-id="69017-106">An Updatable Help package for a module consists of one HelpInfo XML file and one or more cabinet (.CAB) files.</span></span> <span data-ttu-id="69017-107">每个 CAB 文件包含一个 UI 区域性中的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="69017-107">Each CAB file contains help files for the module in one UI culture.</span></span> <span data-ttu-id="69017-108">使用以下过程来创建可更新帮助的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="69017-108">Use the following procedure to create CAB files for Updatable Help.</span></span>

1. <span data-ttu-id="69017-109">通过 UI 区域性组织模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="69017-109">Organize the help files for the module by UI culture.</span></span> <span data-ttu-id="69017-110">每个可更新帮助的 CAB 文件包含一个 UI 区域性中的一个模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="69017-110">Each Updatable Help CAB file contains the help files for one module in one UI culture.</span></span> <span data-ttu-id="69017-111">你可提供多个帮助的模块，每个不同的 UI 区域性的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="69017-111">You can deliver multiple help CAB files for the module, each for a different UI culture.</span></span>

2. <span data-ttu-id="69017-112">验证的帮助文件包括允许可更新帮助的文件类型并针对帮助文件架构进行验证。</span><span class="sxs-lookup"><span data-stu-id="69017-112">Verify that help files include only the file types permitted for Updatable Help and validate them against a help file schema.</span></span> <span data-ttu-id="69017-113">如果`Update-Help`cmdlet 遇到无效或不允许的类型的文件，它不会安装无效的文件，并停止从 CAB 安装文件。</span><span class="sxs-lookup"><span data-stu-id="69017-113">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB.</span></span> <span data-ttu-id="69017-114">允许的文件类型的列表，请参阅[可更新帮助 CAB 文件中的文件类型允许](./file-types-permitted-in-an-updatable-help-cab-file.md)。</span><span class="sxs-lookup"><span data-stu-id="69017-114">For a list of permitted file types, see [File Types Permitted in an Updatable Help CAB File](./file-types-permitted-in-an-updatable-help-cab-file.md).</span></span>

3. <span data-ttu-id="69017-115">进行数字签名帮助文件。</span><span class="sxs-lookup"><span data-stu-id="69017-115">Digitally sign the help files.</span></span> <span data-ttu-id="69017-116">数字签名不是必需的但它们是一种最佳做法。</span><span class="sxs-lookup"><span data-stu-id="69017-116">Digital signatures are not required, but they are a best practice.</span></span>

4. <span data-ttu-id="69017-117">包括所有在 UI 中的模块的文件的区域性，而不仅仅是新的文件或已改变的帮助。</span><span class="sxs-lookup"><span data-stu-id="69017-117">Include all of help files for the module in the UI culture, not only files that are new or have changed.</span></span> <span data-ttu-id="69017-118">如果不完整的 CAB 文件，第一次下载帮助文件或不下载每个更新，用户不会的所有模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="69017-118">If the CAB file is incomplete, users who download help files for the first time or do not download every update, will not have all of the module help files.</span></span>

5. <span data-ttu-id="69017-119">使用创建 cabinet 文件，如 MakeCab.exe 实用程序。</span><span class="sxs-lookup"><span data-stu-id="69017-119">Use a utility that creates cabinet files, such as MakeCab.exe.</span></span> <span data-ttu-id="69017-120">Windows PowerShell 不包括创建 CAB 文件的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="69017-120">Windows PowerShell does not include cmdlets that create CAB files.</span></span>

6. <span data-ttu-id="69017-121">命名的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="69017-121">Name the CAB files.</span></span> <span data-ttu-id="69017-122">有关详细信息，请参阅[如何命名可更新帮助 CAB 文件](./how-to-name-an-updatable-help-cab-file.md)。</span><span class="sxs-lookup"><span data-stu-id="69017-122">For more information, see [How to Name an Updatable Help CAB File](./how-to-name-an-updatable-help-cab-file.md).</span></span>

7. <span data-ttu-id="69017-123">将该模块的 CAB 文件上载到指定的位置**HelpContentUri**模块的 HelpInfo XML 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="69017-123">Upload the CAB files for the module to the location that is specified by the **HelpContentUri** element in the HelpInfo XML file for the module.</span></span> <span data-ttu-id="69017-124">然后将 HelpInfo XML 文件上载到由指定的位置**HelpInfoUri**模块清单的密钥。</span><span class="sxs-lookup"><span data-stu-id="69017-124">Then upload the HelpInfo XML file to the location that is specified by the **HelpInfoUri** key of the module manifest.</span></span> <span data-ttu-id="69017-125">**HelpContentUri**并**HelpInfoUri**可以指向同一位置。</span><span class="sxs-lookup"><span data-stu-id="69017-125">The **HelpContentUri** and **HelpInfoUri** can point to the same location.</span></span>

> [!CAUTION]
> <span data-ttu-id="69017-126">值**HelpInfoUri**密钥和**HelpContentUri**元素必须以"http"或"https"开头。</span><span class="sxs-lookup"><span data-stu-id="69017-126">The value of the **HelpInfoUri** key and the **HelpContentUri** element must begin with "http" or "https".</span></span> <span data-ttu-id="69017-127">值必须指示 Internet 位置，并且不包含文件名称。</span><span class="sxs-lookup"><span data-stu-id="69017-127">The value must indicate an Internet location and it must not include a file name.</span></span>