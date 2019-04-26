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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082407"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="e53f6-102">如何创建 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="e53f6-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="e53f6-103">本部分中的本主题说明如何创建和填充的帮助信息文件，通常称为"HelpInfo XML 文件，"Windows PowerShell 可更新帮助功能。</span><span class="sxs-lookup"><span data-stu-id="e53f6-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="e53f6-104">HelpInfo XML 文件概述</span><span class="sxs-lookup"><span data-stu-id="e53f6-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="e53f6-105">HelpInfo XML 文件是模块的有关可更新帮助信息的主要来源。</span><span class="sxs-lookup"><span data-stu-id="e53f6-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="e53f6-106">它包括模块、 支持的 UI 区域性和可更新帮助使用来确定用户是否具有最新帮助文件的版本号的帮助文件的位置。</span><span class="sxs-lookup"><span data-stu-id="e53f6-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="e53f6-107">每个模块具有一个 HelpInfo XML 文件，即使该模块包含多个 UI 区域性的多个帮助文件。</span><span class="sxs-lookup"><span data-stu-id="e53f6-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="e53f6-108">模块作者创建 HelpInfo XML 文件，并将其放置在由指定的 Internet 位置**HelpInfoUri**密钥模块清单中。</span><span class="sxs-lookup"><span data-stu-id="e53f6-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="e53f6-109">当模块帮助文件进行更新，并上传时，模块作者更新 HelpInfo XML 文件，并使用新版本替换原始的 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e53f6-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="e53f6-110">请仔细维护 HelpInfo XML 文件至关重要。</span><span class="sxs-lookup"><span data-stu-id="e53f6-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="e53f6-111">如果上传新文件，但忘记递增版本号，可更新帮助将下载到用户的计算机的新文件。</span><span class="sxs-lookup"><span data-stu-id="e53f6-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="e53f6-112">如果你添加为新的 UI 区域性，帮助文件，但不更新 HelpInfo XML 文件或将其放在正确的位置，可更新的帮助不会下载新文件。</span><span class="sxs-lookup"><span data-stu-id="e53f6-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e53f6-113">本部分内容</span><span class="sxs-lookup"><span data-stu-id="e53f6-113">In this section</span></span>

<span data-ttu-id="e53f6-114">本部分包括以下主题。</span><span class="sxs-lookup"><span data-stu-id="e53f6-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="e53f6-115">HelpInfo XML 架构</span><span class="sxs-lookup"><span data-stu-id="e53f6-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="e53f6-116">HelpInfo XML 示例文件</span><span class="sxs-lookup"><span data-stu-id="e53f6-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="e53f6-117">如何命名 HelpInfo XML 文件</span><span class="sxs-lookup"><span data-stu-id="e53f6-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="e53f6-118">如何设置 HelpInfo XML 版本号</span><span class="sxs-lookup"><span data-stu-id="e53f6-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="e53f6-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e53f6-119">See Also</span></span>

[<span data-ttu-id="e53f6-120">支持可更新帮助</span><span class="sxs-lookup"><span data-stu-id="e53f6-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)