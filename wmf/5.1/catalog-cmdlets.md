---
title: "目录 cmdlet"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: carolz
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: ecf70f38bbf48f410eb59b75f86eea767637757a
ms.openlocfilehash: 72df0311a1d187dc6c7c1d29b0a3d2fd243848f0

---
# <a name="catalog-cmdlets"></a>目录 Cmdlet  

我们在 [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) 模块中新增了两个新 cmdlet 来生成和验证 windows 目录文件。  

## <a name="new-filecatalog"></a>New-FileCatalog 
--------------------------------

`New-FileCatalog` 用于为文件夹和文件集合创建 Windows 目录文件。 目录文件包含指定路径中的所有文件的哈希值。 用户可分发文件夹集合以及代表这些文件夹的对应目录文件。 内容接收方可使用目录文件，验证创建目录后是否对文件夹进行了任何更改。    

```PowerShell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
我们支持创建目录版本 1 和 2。 版本 1 使用 SHA1 哈希算法来创建文件哈希值，版本 2 则使用 SHA256。 Windows Server 2008 R2 和 Windows 7 不支持目录版本 2。 如果使用的平台为 Windows 8、Windows Server 2012 及更高版本，则建议使用目录版本 2。  

若要在现有模块上使用此命令，请指定 CatalogFilePath 和 Path 变量，以匹配模块清单的位置。 在下面的示例中，模块清单位于 C:\Program Files\Windows PowerShell\Modules\Pester。 

![](../images/NewFileCatalog.jpg)

这将创建目录文件。 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

若要验证目录文件（上面示例中的 Pester.cat 文件）的完整性，应使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet 对其进行签名。   


## <a name="test-filecatalog"></a>Test-FileCatalog 
--------------------------------

`Test-FileCatalog` 用于验证代表一组文件夹的目录。 

```PowerShell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

此 cmdlet 将在目录文件中找到的所有文件的哈希值及其相对路径与保存到磁盘的值相比较。 如果它检测到文件哈希值和路径之间存在任何不匹配，将返回状态 `ValidationFailed`。 用户可使用 `Detailed` 切换检索所有该信息。 目录的签名状态将在 `Signature` 字段中显示，该结果与针对目录文件调用 [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet 的结果相同。 用户也可使用 `FilesToSkip` 参数在验证过程中跳过任何文件。 



<!--HONumber=Nov16_HO4-->


