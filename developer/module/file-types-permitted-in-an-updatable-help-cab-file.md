---
title: 文件类型允许在可更新帮助的 CAB 文件 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082441"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="9d17c-102">可更新帮助 CAB 文件中允许的文件类型</span><span class="sxs-lookup"><span data-stu-id="9d17c-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="9d17c-103">本主题列出并描述了可更新帮助的 CAB 文件的内容要求。</span><span class="sxs-lookup"><span data-stu-id="9d17c-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="9d17c-104">可更新帮助的 CAB 文件要求</span><span class="sxs-lookup"><span data-stu-id="9d17c-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="9d17c-105">默认情况下限制为 1 GB 是未压缩的 CAB 文件内容。</span><span class="sxs-lookup"><span data-stu-id="9d17c-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="9d17c-106">若要绕过此限制，用户必须使用**Force**的参数[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d17c-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="9d17c-107">若要确保从 Internet 下载帮助文件的安全，可更新帮助的 CAB 文件可以包括下面列出的文件类型。</span><span class="sxs-lookup"><span data-stu-id="9d17c-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="9d17c-108">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 可验证所有针对帮助主题架构文件。</span><span class="sxs-lookup"><span data-stu-id="9d17c-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="9d17c-109">如果`Update-Help`cmdlet 遇到无效或不允许的类型的文件，它不会安装无效的文件，并停止从用户的计算机上的 CAB 安装文件。</span><span class="sxs-lookup"><span data-stu-id="9d17c-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="9d17c-110">Cmdlet 的基于 XML 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="9d17c-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="9d17c-111">脚本和函数的基于 XML 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="9d17c-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="9d17c-112">Windows PowerShell 提供程序的基于 XML 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="9d17c-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="9d17c-113">基于文本的帮助主题，例如有关主题的信息。</span><span class="sxs-lookup"><span data-stu-id="9d17c-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="9d17c-114">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)解压缩 CAB 时，会验证 CAB 内容。</span><span class="sxs-lookup"><span data-stu-id="9d17c-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="9d17c-115">如果`Update-Help`查找不符合标准的文件类型的可更新帮助的 CAB 文件中，它将生成一个终止错误并停止操作。</span><span class="sxs-lookup"><span data-stu-id="9d17c-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="9d17c-116">它不从 CAB，甚至那些符合文件类型安装任何帮助文件。</span><span class="sxs-lookup"><span data-stu-id="9d17c-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>