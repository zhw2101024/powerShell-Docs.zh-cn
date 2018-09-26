---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: 目录 cmdlet
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522882"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="8dae3-103">目录 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8dae3-103">Catalog Cmdlets</span></span>

<span data-ttu-id="8dae3-104">我们在 [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) 模块中新增了两个新 cmdlet 来生成和验证 windows 目录文件。</span><span class="sxs-lookup"><span data-stu-id="8dae3-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="8dae3-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="8dae3-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="8dae3-106">`New-FileCatalog` 用于为文件夹和文件集合创建 Windows 目录文件。</span><span class="sxs-lookup"><span data-stu-id="8dae3-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="8dae3-107">目录文件包含指定路径中的所有文件的哈希值。</span><span class="sxs-lookup"><span data-stu-id="8dae3-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="8dae3-108">用户可分发文件夹集合以及代表这些文件夹的对应目录文件。</span><span class="sxs-lookup"><span data-stu-id="8dae3-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="8dae3-109">内容接收方可使用目录文件，验证创建目录后是否对文件夹进行了任何更改。</span><span class="sxs-lookup"><span data-stu-id="8dae3-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="8dae3-110">我们支持创建目录版本 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="8dae3-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="8dae3-111">版本 1 使用 SHA1 哈希算法来创建文件哈希值，版本 2 则使用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="8dae3-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="8dae3-112">Windows Server 2008 R2 和 Windows 7 不支持目录版本 2。</span><span class="sxs-lookup"><span data-stu-id="8dae3-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="8dae3-113">如果使用的平台为 Windows 8、Windows Server 2012 及更高版本，则建议使用目录版本 2。</span><span class="sxs-lookup"><span data-stu-id="8dae3-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="8dae3-114">若要在现有模块上使用此命令，请指定 CatalogFilePath 和 Path 变量，以匹配模块清单的位置。</span><span class="sxs-lookup"><span data-stu-id="8dae3-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="8dae3-115">在下面的示例中，模块清单位于 C:\Program Files\Windows PowerShell\Modules\Pester。</span><span class="sxs-lookup"><span data-stu-id="8dae3-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="8dae3-116">这将创建目录文件。</span><span class="sxs-lookup"><span data-stu-id="8dae3-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="8dae3-117">若要验证目录文件（上面示例中的 Pester.cat 文件）的完整性，应使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet 对其进行签名。</span><span class="sxs-lookup"><span data-stu-id="8dae3-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="8dae3-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="8dae3-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="8dae3-119">`Test-FileCatalog` 用于验证代表一组文件夹的目录。</span><span class="sxs-lookup"><span data-stu-id="8dae3-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="8dae3-120">此 cmdlet 将在目录文件中找到的所有文件的哈希值及其相对路径与保存到磁盘的值相比较。</span><span class="sxs-lookup"><span data-stu-id="8dae3-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="8dae3-121">如果它检测到文件哈希值和路径之间存在任何不匹配，将返回状态 `ValidationFailed`。</span><span class="sxs-lookup"><span data-stu-id="8dae3-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="8dae3-122">用户可使用 `Detailed` 切换检索所有该信息。</span><span class="sxs-lookup"><span data-stu-id="8dae3-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="8dae3-123">目录的签名状态将在 `Signature` 字段中显示，该结果与针对目录文件调用 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet 的结果相同。</span><span class="sxs-lookup"><span data-stu-id="8dae3-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="8dae3-124">用户也可使用 `FilesToSkip` 参数在验证过程中跳过任何文件。</span><span class="sxs-lookup"><span data-stu-id="8dae3-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
