---
title: 如何更新帮助文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855523"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="96a98-102">如何更新帮助文件</span><span class="sxs-lookup"><span data-stu-id="96a98-102">How to Update Help Files</span></span>

<span data-ttu-id="96a98-103">本主题说明如何更新支持可更新帮助的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="96a98-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="96a98-104">更新帮助文件</span><span class="sxs-lookup"><span data-stu-id="96a98-104">Updating Help Files</span></span>

<span data-ttu-id="96a98-105">原因有很多更新帮助文件，例如更正错误、 阐明概念、 回答常见问题的问题、 添加新文件，或添加新的和更好的示例。</span><span class="sxs-lookup"><span data-stu-id="96a98-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="96a98-106">若要更新的帮助文件：</span><span class="sxs-lookup"><span data-stu-id="96a98-106">To update a help file:</span></span>

1. <span data-ttu-id="96a98-107">更改的文件。</span><span class="sxs-lookup"><span data-stu-id="96a98-107">Change the files.</span></span>

2. <span data-ttu-id="96a98-108">将文件转换为其他 UI 区域性。</span><span class="sxs-lookup"><span data-stu-id="96a98-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="96a98-109">收集有关每个 UI 区域性中模块的所有帮助文件 （new、 已更改，而不变）。</span><span class="sxs-lookup"><span data-stu-id="96a98-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="96a98-110">验证针对 XML 架构文件。</span><span class="sxs-lookup"><span data-stu-id="96a98-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="96a98-111">重新生成每个 UI 区域性的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="96a98-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="96a98-112">HelpInfo XML 文件中递增每个 UI 区域性的 CAB 文件的版本号。</span><span class="sxs-lookup"><span data-stu-id="96a98-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="96a98-113">将新的 CAB 文件上传到指定的值的位置**HelpContentUri** HelpInfo XML 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="96a98-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="96a98-114">较旧的 CAB 文件替换为新的 CAB 文件。</span><span class="sxs-lookup"><span data-stu-id="96a98-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="96a98-115">将更新的 HelpInfo XML 文件上传到由指定的位置**HelpInfoUri**密钥模块清单中。</span><span class="sxs-lookup"><span data-stu-id="96a98-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="96a98-116">将新文件替换为较早的 HelpInfo XML 文件。</span><span class="sxs-lookup"><span data-stu-id="96a98-116">Replace the older HelpInfo XML file with the new file.</span></span>