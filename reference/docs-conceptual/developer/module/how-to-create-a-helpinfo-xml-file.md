---
title: 如何创建 HelpInfo XML 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367316"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="cf75c-102">如何创建 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="cf75c-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="cf75c-103">本节中的主题介绍如何创建和填充 Windows PowerShell 可更新帮助功能的帮助信息文件（通常称为 "HelpInfo XML 文件"）。</span><span class="sxs-lookup"><span data-stu-id="cf75c-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="cf75c-104">HelpInfo XML 文件概述</span><span class="sxs-lookup"><span data-stu-id="cf75c-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="cf75c-105">HelpInfo XML 文件是有关模块的可更新帮助的主要信息来源。</span><span class="sxs-lookup"><span data-stu-id="cf75c-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="cf75c-106">它包括模块的帮助文件的位置、支持的 UI 区域性以及可更新帮助用于确定用户是否具有最新帮助文件的版本号。</span><span class="sxs-lookup"><span data-stu-id="cf75c-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="cf75c-107">每个模块都只有一个 HelpInfo XML 文件，即使该模块包含多个 UI 区域性的多个帮助文件也是如此。</span><span class="sxs-lookup"><span data-stu-id="cf75c-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="cf75c-108">模块作者创建 HelpInfo XML 文件，并将其放置在由模块清单中的**HelpInfoUri**键指定的 Internet 位置。</span><span class="sxs-lookup"><span data-stu-id="cf75c-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="cf75c-109">当模块帮助文件更新并上传时，模块作者将更新 HelpInfo XML 文件，并将原始 HelpInfo XML 文件替换为新版本。</span><span class="sxs-lookup"><span data-stu-id="cf75c-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="cf75c-110">仔细维护 HelpInfo XML 文件非常重要。</span><span class="sxs-lookup"><span data-stu-id="cf75c-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="cf75c-111">如果上传新文件，但忘记增加版本号，则可更新帮助不会将新文件下载到用户的计算机。</span><span class="sxs-lookup"><span data-stu-id="cf75c-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="cf75c-112">如果为新的 UI 区域性添加帮助文件，但不更新 HelpInfo XML 文件或将其放在正确的位置，则可更新的帮助将不会下载新文件。</span><span class="sxs-lookup"><span data-stu-id="cf75c-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cf75c-113">本部分内容</span><span class="sxs-lookup"><span data-stu-id="cf75c-113">In this section</span></span>

<span data-ttu-id="cf75c-114">本部分包括以下主题。</span><span class="sxs-lookup"><span data-stu-id="cf75c-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="cf75c-115">HelpInfo XML 架构</span><span class="sxs-lookup"><span data-stu-id="cf75c-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="cf75c-116">HelpInfo XML 示例文件</span><span class="sxs-lookup"><span data-stu-id="cf75c-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="cf75c-117">如何命名 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="cf75c-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="cf75c-118">如何设置 HelpInfo XML 版本号</span><span class="sxs-lookup"><span data-stu-id="cf75c-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="cf75c-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf75c-119">See Also</span></span>

[<span data-ttu-id="cf75c-120">支持可更新帮助</span><span class="sxs-lookup"><span data-stu-id="cf75c-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)