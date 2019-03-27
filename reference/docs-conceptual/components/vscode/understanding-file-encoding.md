---
title: 了解 VSCode 和 PowerShell 中的文件编码
description: 在 VSCode 和 PowerShell 中配置文件编码
ms.date: 02/28/2019
ms.openlocfilehash: ec06d8f5d446a92e6cd9d2d70b11260d1d0afda8
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320398"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="7014c-103">了解 VSCode 和 PowerShell 中的文件编码</span><span class="sxs-lookup"><span data-stu-id="7014c-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="7014c-104">使用 VS Code 创建和编辑 PowerShell 脚本时，务必使用正确的字符编码格式保存文件。</span><span class="sxs-lookup"><span data-stu-id="7014c-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="7014c-105">什么是文件编码以及它为什么很重要？</span><span class="sxs-lookup"><span data-stu-id="7014c-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="7014c-106">VSCode 管理人员向缓冲区中输入字符串与对文件系统读取/写入字节块之间的接口。</span><span class="sxs-lookup"><span data-stu-id="7014c-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="7014c-107">VSCode 保存文件时，会使用文本编码执行此操作。</span><span class="sxs-lookup"><span data-stu-id="7014c-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="7014c-108">同样，当 PowerShell 运行脚本时，必须将文件中的字节转换为字符以将文件重新构造为 PowerShell 程序。</span><span class="sxs-lookup"><span data-stu-id="7014c-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="7014c-109">由于 VSCode 写入文件，而 PowerShell 读取文件，因此它们需要使用相同的编码系统。</span><span class="sxs-lookup"><span data-stu-id="7014c-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="7014c-110">分析 PowerShell 脚本的这一过程是：字节 -> 字符 -> 标记 -> 抽象语法树 -> 执行。</span><span class="sxs-lookup"><span data-stu-id="7014c-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="7014c-111">VSCode 和 PowerShell 都使用合理的默认编码配置进行安装。</span><span class="sxs-lookup"><span data-stu-id="7014c-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="7014c-112">但是，PowerShell 使用的默认编码已随着 PowerShell Core (v6.x) 的发布而更改。</span><span class="sxs-lookup"><span data-stu-id="7014c-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="7014c-113">若要确保在 VSCode 中使用 PowerShell 或 PowerShell 扩展时不会出现问题，需要正确配置 VSCode 和 PowerShell 设置。</span><span class="sxs-lookup"><span data-stu-id="7014c-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="7014c-114">编码问题的常见原因</span><span class="sxs-lookup"><span data-stu-id="7014c-114">Common causes of encoding issues</span></span>

<span data-ttu-id="7014c-115">当 VSCode 或脚本文件的编码与 PowerShell 的期望编码不匹配时，会出现编码问题。</span><span class="sxs-lookup"><span data-stu-id="7014c-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="7014c-116">PowerShell 无法自动确定文件编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="7014c-117">如果使用的字符不在 [7 位 ASCII 字符集](https://ascii.cl/)中，则更可能出现编码问题。</span><span class="sxs-lookup"><span data-stu-id="7014c-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="7014c-118">例如：</span><span class="sxs-lookup"><span data-stu-id="7014c-118">For example:</span></span>

- <span data-ttu-id="7014c-119">重音拉丁字符（`É`、`ü`）</span><span class="sxs-lookup"><span data-stu-id="7014c-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="7014c-120">非拉丁字符，如西里尔文（`Д`、`Ц`）</span><span class="sxs-lookup"><span data-stu-id="7014c-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="7014c-121">汉字（`脚`、`本`）</span><span class="sxs-lookup"><span data-stu-id="7014c-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="7014c-122">编码问题的常见原因有：</span><span class="sxs-lookup"><span data-stu-id="7014c-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="7014c-123">VSCode 和 PowerShell 的编码尚未更改，仍使用默认设置。</span><span class="sxs-lookup"><span data-stu-id="7014c-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="7014c-124">对于 PowerShell 5.1 及更低版本，默认编码与 VSCode 不同。</span><span class="sxs-lookup"><span data-stu-id="7014c-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="7014c-125">另一个编辑器已打开，并采用新编码覆盖了文件。</span><span class="sxs-lookup"><span data-stu-id="7014c-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="7014c-126">ISE 通常会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="7014c-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="7014c-127">文件采用与 VSCode 或 PowerShell 期望编码不同的编码签入了源代码管理。</span><span class="sxs-lookup"><span data-stu-id="7014c-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="7014c-128">当协作者使用具有不同编码配置的编辑器时，可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="7014c-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="7014c-129">如何判断出现了编码问题</span><span class="sxs-lookup"><span data-stu-id="7014c-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="7014c-130">编码错误通常表现为脚本中的分析错误。</span><span class="sxs-lookup"><span data-stu-id="7014c-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="7014c-131">如果在脚本中发现奇怪的字符序列，则这可能是问题所在。</span><span class="sxs-lookup"><span data-stu-id="7014c-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="7014c-132">在以下示例中，短划线 (`–`) 显示为字符 `â€“`：</span><span class="sxs-lookup"><span data-stu-id="7014c-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="7014c-133">发生此问题的原因是 VSCode 将采用 UTF-8 的字符 `–` 编码为字节 `0xE2 0x80 0x93`。</span><span class="sxs-lookup"><span data-stu-id="7014c-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="7014c-134">当这些字节解码为 Windows-1252 时，它们会被解释为字符 `â€“`。</span><span class="sxs-lookup"><span data-stu-id="7014c-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="7014c-135">可能会看到的一些奇怪字符序列包括：</span><span class="sxs-lookup"><span data-stu-id="7014c-135">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="7014c-136">`â€“`（而不是 `–`）</span><span class="sxs-lookup"><span data-stu-id="7014c-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="7014c-137">`â€”`（而不是 `—`）</span><span class="sxs-lookup"><span data-stu-id="7014c-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="7014c-138">`Ã„2`（而不是 `Ä`）</span><span class="sxs-lookup"><span data-stu-id="7014c-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="7014c-139">`Â`（而不是 ` `（不间断空格））</span><span class="sxs-lookup"><span data-stu-id="7014c-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="7014c-140">`Ã©`（而不是 `é`）</span><span class="sxs-lookup"><span data-stu-id="7014c-140">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="7014c-141">此便捷[参考](https://www.i18nqa.com/debug/utf8-debug.html)列出了指示 UTF-8/Windows-1252 编码问题的常见模式。</span><span class="sxs-lookup"><span data-stu-id="7014c-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="7014c-142">VSCode 中的 PowerShell 扩展与编码的交互方式</span><span class="sxs-lookup"><span data-stu-id="7014c-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="7014c-143">PowerShell 扩展通过多种方式与脚本进行交互：</span><span class="sxs-lookup"><span data-stu-id="7014c-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="7014c-144">当脚本在 VSCode 中进行编辑时，内容由 VSCode 发送到扩展。</span><span class="sxs-lookup"><span data-stu-id="7014c-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="7014c-145">[语言服务器协议][]要求此内容采用 UTF-8 进行传输。</span><span class="sxs-lookup"><span data-stu-id="7014c-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="7014c-146">因此，扩展不可能获取错误的编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="7014c-147">当脚本直接在集成控制台中执行时，它们直接由 PowerShell 从文件读取。</span><span class="sxs-lookup"><span data-stu-id="7014c-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="7014c-148">如果 PowerShell 的编码与 VSCode 不同，则可能会出错。</span><span class="sxs-lookup"><span data-stu-id="7014c-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="7014c-149">当在 VSCode 中打开的一个脚本引用未在 VSCode 中打开的另一个脚本时，扩展会回退到从文件系统加载该脚本的内容。</span><span class="sxs-lookup"><span data-stu-id="7014c-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="7014c-150">PowerShell 扩展默认为 UTF-8 编码，但使用[字节顺序标记][]（或 BOM）检测来选择正确编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="7014c-151">当采用无 BOM 式格式的编码（如没有 BOM 的 [UTF-8][] 和 [Windows-1252][]）时，会出现问题。</span><span class="sxs-lookup"><span data-stu-id="7014c-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="7014c-152">PowerShell 扩展默认为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="7014c-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="7014c-153">扩展无法更改 VSCode 的编码设置。</span><span class="sxs-lookup"><span data-stu-id="7014c-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="7014c-154">有关详细信息，请参阅[问题 #824](https://github.com/Microsoft/vscode/issues/824)。</span><span class="sxs-lookup"><span data-stu-id="7014c-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="7014c-155">选择正确编码</span><span class="sxs-lookup"><span data-stu-id="7014c-155">Choosing the right encoding</span></span>

<span data-ttu-id="7014c-156">不同的系统和应用程序可以使用不同的编码：</span><span class="sxs-lookup"><span data-stu-id="7014c-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="7014c-157">在 .NET Standard 中、Web 上以及 Linux 领域中，UTF-8 现在是主流编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="7014c-158">许多 .NET Framework 应用程序使用 [UTF-16][]。</span><span class="sxs-lookup"><span data-stu-id="7014c-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="7014c-159">由于历史原因，这有时称为“Unicode”，该术语现在是指包括 UTF-8 和 UTF-16 在内的广泛[标准](https://en.wikipedia.org/wiki/Unicode)。</span><span class="sxs-lookup"><span data-stu-id="7014c-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="7014c-160">在 Windows 中上，早于 Unicode 出现的许多本机应用程序在默认情况下继续使用 Windows-1252。</span><span class="sxs-lookup"><span data-stu-id="7014c-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="7014c-161">Unicode 编码也具有字节顺序标记 (BOM) 的概念。</span><span class="sxs-lookup"><span data-stu-id="7014c-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="7014c-162">BOM 在文本开头出现，用于向解码器告知文本所使用的编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="7014c-163">对于多字节编码，BOM 还指示编码的[字节顺序](https://en.wikipedia.org/wiki/Endianness)。</span><span class="sxs-lookup"><span data-stu-id="7014c-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="7014c-164">BOM 设计为很少出现在非 Unicode 文本中的字节，从而当 BOM 存在时可以合理地猜测文本是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="7014c-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="7014c-165">BOM 是可选的，其采用在 Linux 领域中并不普遍，因为到处都在使用可靠的 UTF-8 约定。</span><span class="sxs-lookup"><span data-stu-id="7014c-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="7014c-166">大多数 Linux 应用程序假设文本输入采用 UTF-8 进行编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="7014c-167">虽然许多 Linux 应用程序可识别并正确处理 BOM，不过有一些应用程序无法这样做，从而导致使用这些应用程序操作的文本中出现异常。</span><span class="sxs-lookup"><span data-stu-id="7014c-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="7014c-168">**因此**：</span><span class="sxs-lookup"><span data-stu-id="7014c-168">**Therefore**:</span></span>

- <span data-ttu-id="7014c-169">如果主要使用 Windows 应用程序和 Windows PowerShell，则应优先使用诸如具有 BOM 的 UTF-8 或 UTF-16 这类编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="7014c-170">如果跨平台工作，则应优先使用具有 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="7014c-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="7014c-171">如果主要在与 Linux 关联的环境中工作，则应优先使用不具有 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="7014c-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="7014c-172">Windows-1252 和拉丁语-1 本质上是旧编码，应尽可能避免使用。</span><span class="sxs-lookup"><span data-stu-id="7014c-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="7014c-173">但是，某些较旧的 Windows 应用程序可能依赖于它们。</span><span class="sxs-lookup"><span data-stu-id="7014c-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="7014c-174">另外值得注意的是，脚本签名[依赖于编码](https://github.com/PowerShell/PowerShell/issues/3466)，这意味着签名脚本中的编码更改需要重新签名。</span><span class="sxs-lookup"><span data-stu-id="7014c-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="7014c-175">配置 VSCode</span><span class="sxs-lookup"><span data-stu-id="7014c-175">Configuring VSCode</span></span>

<span data-ttu-id="7014c-176">VSCode 的默认编码是不具有 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="7014c-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="7014c-177">若要设置 [VSCode 的编码][]，请转到 VSCode 设置（<kbd>Ctrl<kbd>+</kbd>，</kbd>）并设置 `"files.encoding"` 设置：</span><span class="sxs-lookup"><span data-stu-id="7014c-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="7014c-178">一些可能值有：</span><span class="sxs-lookup"><span data-stu-id="7014c-178">Some possible values are:</span></span>

- <span data-ttu-id="7014c-179">`utf8`：不具有 BOM 的 [UTF-8]</span><span class="sxs-lookup"><span data-stu-id="7014c-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="7014c-180">`utf8bom`：具有 BOM 的 [UTF-8]</span><span class="sxs-lookup"><span data-stu-id="7014c-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="7014c-181">`utf16le`：Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="7014c-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="7014c-182">`utf16be`：Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="7014c-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="7014c-183">`windows1252`：[Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="7014c-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="7014c-184">应在 GUI 视图中看到适用于此内容的下拉列表，或是在 JSON 视图中看到其完成。</span><span class="sxs-lookup"><span data-stu-id="7014c-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="7014c-185">还可以添加以下内容以尽可能自动检测编码：</span><span class="sxs-lookup"><span data-stu-id="7014c-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="7014c-186">如果不希望这些设置影响所有文件类型，则 VSCode 还允许按语言进行配置。</span><span class="sxs-lookup"><span data-stu-id="7014c-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="7014c-187">创建在 `[<language-name>]` 字段中放置设置，可以配置特定于语言的设置。</span><span class="sxs-lookup"><span data-stu-id="7014c-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="7014c-188">例如：</span><span class="sxs-lookup"><span data-stu-id="7014c-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="7014c-189">配置 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7014c-189">Configuring PowerShell</span></span>

<span data-ttu-id="7014c-190">PowerShell 的默认编码因版本而异：</span><span class="sxs-lookup"><span data-stu-id="7014c-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="7014c-191">在 PowerShell 6+ 中，默认编码在所有平台上都是不具有 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="7014c-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="7014c-192">在 Windows PowerShell 中，默认编码通常是 Windows-1252，这是[拉丁语-1][] 的扩展，也称为 ISO 8859-1。</span><span class="sxs-lookup"><span data-stu-id="7014c-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="7014c-193">在 PowerShell 5+ 中，可以使用以下方法查找默认编码：</span><span class="sxs-lookup"><span data-stu-id="7014c-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="7014c-194">以下[脚本](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)用于确定 PowerShell 会话对不具有 BOM 的脚本推断出何种编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="7014c-195">可以更普遍地使用配置文件设置将 PowerShell 配置为使用给定编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="7014c-196">请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="7014c-196">See the following articles:</span></span>

- <span data-ttu-id="7014c-197">[@mklement0] [有关 StackOverflow 上的 PowerShell 编码的解答](https://stackoverflow.com/a/40098904)。</span><span class="sxs-lookup"><span data-stu-id="7014c-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="7014c-198">[@rkeithhill] [有关在 PowerShell 中处理无 BOM 式 UTF-8 输入的博客文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。</span><span class="sxs-lookup"><span data-stu-id="7014c-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="7014c-199">无法强制 PowerShell 使用特定输入编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="7014c-200">在没有 BOM 时，PowerShell 5.1 及以下版本默认为 Windows-1252 编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="7014c-201">出于互操作性原因，最好使用具有 BOM 的 Unicode 格式保存脚本。</span><span class="sxs-lookup"><span data-stu-id="7014c-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7014c-202">涉及 PowerShell 脚本的任何其他工具都可能会受到编码选择的影响，或是将脚本重新编码为另一种编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="7014c-203">现有脚本</span><span class="sxs-lookup"><span data-stu-id="7014c-203">Existing scripts</span></span>

<span data-ttu-id="7014c-204">文件系统上已有的脚本可能需要重新编码为新的所选编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="7014c-205">在 VSCode 底部栏中，会看到 UTF-8 标签。</span><span class="sxs-lookup"><span data-stu-id="7014c-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="7014c-206">单击它可打开操作栏并选择“保存时使用编码”。</span><span class="sxs-lookup"><span data-stu-id="7014c-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="7014c-207">现在可以为该文件选取新编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="7014c-208">有关完整说明，请参阅 [VSCode 的编码][]。</span><span class="sxs-lookup"><span data-stu-id="7014c-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="7014c-209">如果需要重新编码多个文件，则可以使用以下脚本：</span><span class="sxs-lookup"><span data-stu-id="7014c-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="7014c-210">PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="7014c-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="7014c-211">如果还使用 PowerShell ISE 编辑脚本，则需要在其中同步编码设置。</span><span class="sxs-lookup"><span data-stu-id="7014c-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="7014c-212">ISE 应遵循 BOM，但也可以使用反射来[设置编码](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。</span><span class="sxs-lookup"><span data-stu-id="7014c-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="7014c-213">请注意，这不会在启动之间保持。</span><span class="sxs-lookup"><span data-stu-id="7014c-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="7014c-214">源代码管理软件</span><span class="sxs-lookup"><span data-stu-id="7014c-214">Source control software</span></span>

<span data-ttu-id="7014c-215">一些源代码管理工具（如 git）会忽略编码；git 只跟踪字节。</span><span class="sxs-lookup"><span data-stu-id="7014c-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="7014c-216">其他工具（如 Azure DevOps 或 Mercurial）可能不会忽略编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-216">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="7014c-217">甚至一些基于 git 的工具也依赖于文本解码。</span><span class="sxs-lookup"><span data-stu-id="7014c-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="7014c-218">在这种情况下，请确保：</span><span class="sxs-lookup"><span data-stu-id="7014c-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="7014c-219">在源代码管理中配置文本编码以匹配 VSCode 配置。</span><span class="sxs-lookup"><span data-stu-id="7014c-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="7014c-220">确保所有文件都采用相关编码签入到源代码管理中。</span><span class="sxs-lookup"><span data-stu-id="7014c-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="7014c-221">应注意通过源代码管理收到的编码更改。</span><span class="sxs-lookup"><span data-stu-id="7014c-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="7014c-222">这种情况的一个重要迹象是有差异指示更改，但似乎没有任何内容发生更改（因为字节更改，但字符未更改）。</span><span class="sxs-lookup"><span data-stu-id="7014c-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="7014c-223">协作者环境</span><span class="sxs-lookup"><span data-stu-id="7014c-223">Collaborators' environments</span></span>

<span data-ttu-id="7014c-224">在配置源代码管理的基础上，确保你所共享的任何文件上的协作者没有通过重新编码 PowerShell 文件来替代你的编码的设置。</span><span class="sxs-lookup"><span data-stu-id="7014c-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="7014c-225">其他程序</span><span class="sxs-lookup"><span data-stu-id="7014c-225">Other programs</span></span>

<span data-ttu-id="7014c-226">读取或写入 PowerShell 脚本的其他任何程序都可能会对它重新编码。</span><span class="sxs-lookup"><span data-stu-id="7014c-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="7014c-227">一些示例如下：</span><span class="sxs-lookup"><span data-stu-id="7014c-227">Some examples are:</span></span>

- <span data-ttu-id="7014c-228">使用剪贴板复制和粘贴脚本。</span><span class="sxs-lookup"><span data-stu-id="7014c-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="7014c-229">这是以下这类情形中十分常见：</span><span class="sxs-lookup"><span data-stu-id="7014c-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="7014c-230">将脚本复制到 VM 中</span><span class="sxs-lookup"><span data-stu-id="7014c-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="7014c-231">从电子邮件或网页中复制脚本</span><span class="sxs-lookup"><span data-stu-id="7014c-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="7014c-232">将脚本复制到 Microsoft Word 或 PowerPoint 文档中，或从这类文档中复制脚本</span><span class="sxs-lookup"><span data-stu-id="7014c-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="7014c-233">其他文本编辑器，如：</span><span class="sxs-lookup"><span data-stu-id="7014c-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="7014c-234">记事本</span><span class="sxs-lookup"><span data-stu-id="7014c-234">Notepad</span></span>
  - <span data-ttu-id="7014c-235">vim</span><span class="sxs-lookup"><span data-stu-id="7014c-235">vim</span></span>
  - <span data-ttu-id="7014c-236">任何其他 PowerShell 脚本编辑器</span><span class="sxs-lookup"><span data-stu-id="7014c-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="7014c-237">文本编辑实用工具，如：</span><span class="sxs-lookup"><span data-stu-id="7014c-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="7014c-238">PowerShell 重定向运算符，如 `>` 和 `>>`</span><span class="sxs-lookup"><span data-stu-id="7014c-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="7014c-239">文件传输程序，如：</span><span class="sxs-lookup"><span data-stu-id="7014c-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="7014c-240">Web 浏览器（下载脚本时）</span><span class="sxs-lookup"><span data-stu-id="7014c-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="7014c-241">文件共享</span><span class="sxs-lookup"><span data-stu-id="7014c-241">A file share</span></span>

<span data-ttu-id="7014c-242">其中一些工具以字节（而不是文本）进行处理，而其他工具提供编码配置。</span><span class="sxs-lookup"><span data-stu-id="7014c-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="7014c-243">在需要配置编码的情况下，需要使它与编辑器编码相同，以防止出现问题。</span><span class="sxs-lookup"><span data-stu-id="7014c-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="7014c-244">有关 PowerShell 中的编码的其他资源</span><span class="sxs-lookup"><span data-stu-id="7014c-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="7014c-245">有其他几篇有关在 PowerShell 中编码和配置编码的很好的文章值得一读：</span><span class="sxs-lookup"><span data-stu-id="7014c-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="7014c-246">[@mklement0] 的 [StackOverflow 上的 PowerShell 编码摘要](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="7014c-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="7014c-247">以前在 vscode-PowerShell 上建立的针对编码问题的问题：</span><span class="sxs-lookup"><span data-stu-id="7014c-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="7014c-248">#1308</span><span class="sxs-lookup"><span data-stu-id="7014c-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="7014c-249">#1628</span><span class="sxs-lookup"><span data-stu-id="7014c-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="7014c-250">#1680</span><span class="sxs-lookup"><span data-stu-id="7014c-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="7014c-251">#1744</span><span class="sxs-lookup"><span data-stu-id="7014c-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="7014c-252">#1751</span><span class="sxs-lookup"><span data-stu-id="7014c-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="7014c-253">经典的“Joel 说软件”探讨 Unicode</span><span class="sxs-lookup"><span data-stu-id="7014c-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="7014c-254">.NET Standard 中的编码</span><span class="sxs-lookup"><span data-stu-id="7014c-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[拉丁语-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[字节顺序标记]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[语言服务器协议]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode 的编码]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
