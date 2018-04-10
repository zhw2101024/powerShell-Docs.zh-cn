---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a><span data-ttu-id="c065f-102">存档 cmdlet</span><span class="sxs-lookup"><span data-stu-id="c065f-102">Archive cmdlets</span></span>

<span data-ttu-id="c065f-103">两个新的 cmdlet **Compress-Archive** 和 **Expand-Archive** 可用于压缩和展开 ZIP 文档。</span><span class="sxs-lookup"><span data-stu-id="c065f-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="c065f-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="c065f-104">Compress-Archive</span></span>
<span data-ttu-id="c065f-105">**Compress-Archive** cmdlet 从指定文件创建新存档文件。</span><span class="sxs-lookup"><span data-stu-id="c065f-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="c065f-106">存档文件允许将多个文件打包，还可选择性地将其压缩为单个文件以便处理和存储。</span><span class="sxs-lookup"><span data-stu-id="c065f-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="c065f-107">可以使用 **-CompressionLevel** 参数中指定的压缩算法来压缩存档文件。</span><span class="sxs-lookup"><span data-stu-id="c065f-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="c065f-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="c065f-108">Expand-Archive</span></span>
<span data-ttu-id="c065f-109">**Expand-Archive** cmdlet 从指定存档文件提取文件。</span><span class="sxs-lookup"><span data-stu-id="c065f-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="c065f-110">存档文件允许将多个文件打包，还可选择性地将其压缩为单个文件以便处理和存储。</span><span class="sxs-lookup"><span data-stu-id="c065f-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```