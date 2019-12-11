---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 新的和更新的 cmdlet
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147587"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="3b4cc-103">新的和更新的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b4cc-103">New and updated cmdlets</span></span>

<span data-ttu-id="3b4cc-104">我们根据社区反馈，添加了新的 cmdlet，并更新了现有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="3b4cc-105">存档 cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b4cc-105">Archive cmdlets</span></span>

<span data-ttu-id="3b4cc-106">`Compress-Archive` 和 `Expand-Archive` 这两个新 cmdlet 可用于压缩和展开 ZIP 文件。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="3b4cc-107">有关详细信息，请参阅 [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) 模块文档。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="3b4cc-108">目录 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b4cc-108">Catalog Cmdlets</span></span>

<span data-ttu-id="3b4cc-109">在 Microsoft.PowerShell.Security 模块中新增了两个新 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="3b4cc-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="3b4cc-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="3b4cc-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="3b4cc-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="3b4cc-112">这两个 cmdlet 可用于生成和验证 Windows 目录文件。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="3b4cc-113">剪贴板 cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b4cc-113">Clipboard cmdlets</span></span>

<span data-ttu-id="3b4cc-114">通过 `Get-Clipboard` 和 `Set-Clipboard`，你可以更轻松地将内容传入和传出 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="3b4cc-115">剪贴板 cmdlet 支持图像、音频文件、文件列表和文本。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="3b4cc-116">有关更多信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-116">For more information, see:</span></span>

- [<span data-ttu-id="3b4cc-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="3b4cc-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="3b4cc-118">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="3b4cc-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="3b4cc-119">加密消息语法 (CMS) cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b4cc-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="3b4cc-120">加密消息语法 cmdlet 对使用 IETF 标准格式加密保护消息的内容提供加密和解密支持，如 [RFC5652](https://tools.ietf.org/html/rfc5652.html).中所述。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="3b4cc-121">CMS 加密标准采用公钥加密系统，其中用来加密内容的密钥（公钥  ）和用来解密内容的密钥（私钥  ）是不同的。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="3b4cc-122">公钥可以广泛共享，并非敏感数据。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="3b4cc-123">只能使用私钥解密使用公钥加密的任何内容。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="3b4cc-124">有关详细信息，请参阅 [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)（公钥加密）。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="3b4cc-125">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-125">For more information see:</span></span>

- [<span data-ttu-id="3b4cc-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="3b4cc-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="3b4cc-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="3b4cc-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="3b4cc-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="3b4cc-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="3b4cc-129">证书需要唯一的密钥用法标识符 (EKU)（如“代码签名”或“加密邮件”）在 PowerShell 中将它们识别为数据加密证书。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="3b4cc-130">若要在证书提供程序中查看文档加密证书，可以使用 `Get-ChildItem` 的 DocumentEncryptionCert  动态参数：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="3b4cc-131">从字符串内容中提取并分析结构化对象</span><span class="sxs-lookup"><span data-stu-id="3b4cc-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="3b4cc-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="3b4cc-132">ConvertFrom-String</span></span>

<span data-ttu-id="3b4cc-133">新 `ConvertFrom-String` cmdlet 支持两种模式：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="3b4cc-134">基本分隔分析</span><span class="sxs-lookup"><span data-stu-id="3b4cc-134">Basic delimited parsing</span></span>
- <span data-ttu-id="3b4cc-135">自动生成的示例驱动的分析</span><span class="sxs-lookup"><span data-stu-id="3b4cc-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="3b4cc-136">默认情况下，分隔分析会在空格处将输入拆分，并为得到的组分配属性名称。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="3b4cc-137">UpdateTemplate  参数将算法学习的结果保存到模板文件中的注释内。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="3b4cc-138">这使得学习过程（速度最慢的阶段）成为一次性完成的过程。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="3b4cc-139">使用包含已编码学习算法的模板来运行 `ConvertFrom-String` 现为近即时行为。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="3b4cc-140">有关详细信息，请参阅 [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String)。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="3b4cc-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="3b4cc-141">Convert-String</span></span>

<span data-ttu-id="3b4cc-142">`Convert-String` 可用于通过提供前后对照示例来指定所需文本外观。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="3b4cc-143">该 cmdlet 将自动设置文本格式。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="3b4cc-144">有关详细信息，请参阅 [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String)。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="3b4cc-145">对 FileInfo 对象的更新</span><span class="sxs-lookup"><span data-stu-id="3b4cc-145">Updates to FileInfo object</span></span>

<span data-ttu-id="3b4cc-146">文件版本信息可能会产生误导，尤其是在对文件进行了修补的情况下。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="3b4cc-147">WMF 5.0 向 FileInfo 对象添加了新的 FileVersionRaw 和 ProductVersionRaw 脚本属性    。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="3b4cc-148">以下是为 powershell.exe 显示的属性（假设 $pid 为 PowerShell 进程的 ID）：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="3b4cc-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="3b4cc-149">Format-Hex</span></span>

<span data-ttu-id="3b4cc-150">`Format-Hex` 使你能够以十六进制格式查看文本或二进制数据。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="3b4cc-151">有关详细信息，请参阅 [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex)。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="3b4cc-152">Get-ChildItem 具有 -Depth 参数</span><span class="sxs-lookup"><span data-stu-id="3b4cc-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="3b4cc-153">`Get-ChildItem` 现在具有 Depth  参数，可以将其与 Recurse  一起使用来限制递归：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="3b4cc-154">对声明版本范围的模块支持（1.\* 等）</span><span class="sxs-lookup"><span data-stu-id="3b4cc-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="3b4cc-155">现在，可以组合 MinimumVersion 和 MaximumVersion，导入特定范围内的模块   。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="3b4cc-156">这些参数还支持通配符。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="3b4cc-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="3b4cc-157">New-Guid</span></span>

<span data-ttu-id="3b4cc-158">还有许多需要唯一标识符的情况。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="3b4cc-159">`New-GUID` cmdlet 提供了一种简单的方法来创建新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="3b4cc-160">NoNewLine 参数</span><span class="sxs-lookup"><span data-stu-id="3b4cc-160">NoNewLine parameter</span></span>

<span data-ttu-id="3b4cc-161">`Out-File`、`Add-Content` 和 `Set-Content` 现在具有新的 NoNewline  开关，它将在输出后省略新的行。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="3b4cc-162">例如：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="3b4cc-163">如果不指定 NoNewline  ，每个片段将出现在单独的行上：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="3b4cc-164">使用改进的 Item cmdlet 与符号链接交互</span><span class="sxs-lookup"><span data-stu-id="3b4cc-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="3b4cc-165">为支持符号链接，扩展了 Item cmdlet 和几个相关 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="3b4cc-166">符号链接文件</span><span class="sxs-lookup"><span data-stu-id="3b4cc-166">Symbolic link files</span></span>

<span data-ttu-id="3b4cc-167">在此示例中，我们在 C:\Temp 中创建一个名为 MySymLinkFile.txt 的新符号链接文件，该文件将链接到 $pshome\profile.ps1。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="3b4cc-168">所有三个示例生成相同的结果。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="3b4cc-169">符号链接目录</span><span class="sxs-lookup"><span data-stu-id="3b4cc-169">Symbolic link directories</span></span>

<span data-ttu-id="3b4cc-170">在此示例中，我们在 C:\Temp 中创建一个名为 MySymLinkDir 的新符号链接目录，该目录将链接到 $pshome 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="3b4cc-171">所有三个示例生成相同的结果。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="3b4cc-172">硬链接</span><span class="sxs-lookup"><span data-stu-id="3b4cc-172">Hard links</span></span>

<span data-ttu-id="3b4cc-173">允许的路径  和名称  的相同组合如上所述。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="3b4cc-174">目录联接</span><span class="sxs-lookup"><span data-stu-id="3b4cc-174">Directory junctions</span></span>

<span data-ttu-id="3b4cc-175">可以继续使用上述路径  和名称  组合。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="3b4cc-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="3b4cc-176">Get-ChildItem</span></span>

<span data-ttu-id="3b4cc-177">现在，`Get-ChildItem` 在 Mode  属性中显示“l”以指示符号链接文件或目录。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="3b4cc-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="3b4cc-178">Remove-Item</span></span>

<span data-ttu-id="3b4cc-179">删除符号链接类似于删除任何其他项目类型。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="3b4cc-180">使用 Force  参数可删除目标目录和符号链接中的文件。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="3b4cc-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="3b4cc-181">New-TemporaryFile</span></span>

<span data-ttu-id="3b4cc-182">有时必须在脚本中创建临时文件。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="3b4cc-183">现在可以通过 `New-TemporaryFile` cmdlet 完成此操作：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="3b4cc-184">PowerShell 网络交换机管理</span><span class="sxs-lookup"><span data-stu-id="3b4cc-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="3b4cc-185">在 WMF 5.0 中引入的网络交换机 cmdlet 让你能够将交换机、虚拟 LAN (VLAN) 和基本第 2 层网络交换机端口配置应用到 Windows Server 2012 R2 徽标认证的网络交换机。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="3b4cc-186">通过使用这些 cmdlet，你可以执行：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="3b4cc-187">全局交换机配置，如：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="3b4cc-188">设置主机名</span><span class="sxs-lookup"><span data-stu-id="3b4cc-188">Set host name</span></span>
  - <span data-ttu-id="3b4cc-189">设置交换机横幅</span><span class="sxs-lookup"><span data-stu-id="3b4cc-189">Set switch banner</span></span>
  - <span data-ttu-id="3b4cc-190">保留配置</span><span class="sxs-lookup"><span data-stu-id="3b4cc-190">Persist configuration</span></span>
  - <span data-ttu-id="3b4cc-191">启用或禁用功能</span><span class="sxs-lookup"><span data-stu-id="3b4cc-191">Enable or disable feature</span></span>

- <span data-ttu-id="3b4cc-192">VLAN 配置：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-192">VLAN configuration:</span></span>
  - <span data-ttu-id="3b4cc-193">创建或删除 VLAN</span><span class="sxs-lookup"><span data-stu-id="3b4cc-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="3b4cc-194">启用或禁用 VLAN</span><span class="sxs-lookup"><span data-stu-id="3b4cc-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="3b4cc-195">枚举 VLAN</span><span class="sxs-lookup"><span data-stu-id="3b4cc-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="3b4cc-196">为 VLAN 设置友好名称</span><span class="sxs-lookup"><span data-stu-id="3b4cc-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="3b4cc-197">第 2 层端口配置：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="3b4cc-198">枚举端口</span><span class="sxs-lookup"><span data-stu-id="3b4cc-198">Enumerate ports</span></span>
  - <span data-ttu-id="3b4cc-199">启用或禁用端口</span><span class="sxs-lookup"><span data-stu-id="3b4cc-199">Enable or disable ports</span></span>
  - <span data-ttu-id="3b4cc-200">设置端口模式和属性</span><span class="sxs-lookup"><span data-stu-id="3b4cc-200">Set port modes and properties</span></span>
  - <span data-ttu-id="3b4cc-201">添加或将 VLAN 关联到端口上的 Trunk 或 Access</span><span class="sxs-lookup"><span data-stu-id="3b4cc-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="3b4cc-202">有关详细信息，请参阅 [NetworkSwitchManager](/powershell/module/networkswitchmanager/) 文档。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="3b4cc-203">基于 OData 终结点和 ODataUtils 生成 PowerShell cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b4cc-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="3b4cc-204">ODataUtils 模块允许从支持 OData 的 REST 终结点生成 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="3b4cc-205">Microsoft.PowerShell.ODataUtils 模块包括以下功能：</span><span class="sxs-lookup"><span data-stu-id="3b4cc-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="3b4cc-206">将附加信息从服务器端终结点引导到客户端。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="3b4cc-207">客户端分页支持</span><span class="sxs-lookup"><span data-stu-id="3b4cc-207">Client-side paging support</span></span>
- <span data-ttu-id="3b4cc-208">通过使用 -Select 参数进行的服务器端筛选</span><span class="sxs-lookup"><span data-stu-id="3b4cc-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="3b4cc-209">对 Web 请求标头的支持</span><span class="sxs-lookup"><span data-stu-id="3b4cc-209">Support for web request headers</span></span>

<span data-ttu-id="3b4cc-210">由 `Export-ODataEndPointProxy` cmdlet 生成的代理 cmdlet 提供来自信息流上服务器端 OData 终结点的其他信息  。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="3b4cc-211">在以下示例中，我们将检索热门产品并捕获 `$infoStream` 变量中的输出。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="3b4cc-212">通过指定 IncludeTotalResponseCount  参数，我们将获得服务器上可用的所有产品  记录的总计数。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="3b4cc-213">你可以使用客户端分页支持从服务器中分批获取记录。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="3b4cc-214">当你必须通过网络从服务器获取大量数据时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="3b4cc-215">生成的代理 cmdlet 支持 Select  参数，你可以使用该参数作为筛选器以只接收客户端需要的记录属性。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="3b4cc-216">在服务器端进行筛选，从而减少通过网络传输的数据量。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="3b4cc-217">`Export-ODataEndpointProxy` cmdlet 以及由其生成的代理 cmdlet 现在支持 Headers  参数。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="3b4cc-218">标头可用于通过通道传递 OData 终结点所需的其他信息。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="3b4cc-219">在以下示例中，为 Headers  参数提供了包含订阅密钥的哈希表。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="3b4cc-220">这是需要订阅密钥进行身份验证的服务的一个典型示例。</span><span class="sxs-lookup"><span data-stu-id="3b4cc-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
