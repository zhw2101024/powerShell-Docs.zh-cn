---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: db9c630bcb8e9e0da423c779976739f1ae76f13e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057378"
---
# <a name="archive-cmdlets"></a>存档 cmdlet

两个新的 cmdlet **Compress-Archive** 和 **Expand-Archive** 可用于压缩和展开 ZIP 文档。

## <a name="compress-archive"></a>Compress-Archive
**Compress-Archive** cmdlet 从指定文件创建新存档文件。 存档文件允许将多个文件打包，还可选择性地将其压缩为单个文件以便处理和存储。 可以使用 **-CompressionLevel** 参数中指定的压缩算法来压缩存档文件。
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expand-Archive
**Expand-Archive** cmdlet 从指定存档文件提取文件。 存档文件允许将多个文件打包，还可选择性地将其压缩为单个文件以便处理和存储。
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
