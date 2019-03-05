---
title: 了解 VSCode 和 PowerShell 中的文件编码
description: 配置文件在 VSCode 和 PowerShell 中编码
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251467"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="3eb3f-103">了解 VSCode 和 PowerShell 中的文件编码</span><span class="sxs-lookup"><span data-stu-id="3eb3f-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="3eb3f-104">当使用 VS Code 创建和编辑 PowerShell 脚本，务必使用正确的字符编码格式保存文件。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="3eb3f-105">什么是文件编码和为什么很重要？</span><span class="sxs-lookup"><span data-stu-id="3eb3f-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="3eb3f-106">VSCode 管理到缓冲区的字符组成的人工输入字符串和字节到文件系统读取/写入块之间的接口。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="3eb3f-107">在将文件保存在 VSCode，它使用文本编码来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="3eb3f-108">同样，当 PowerShell 运行脚本时它必须将文件中的字节转换为字符以将文件重构到 PowerShell 程序。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="3eb3f-109">由于 VSCode 写入该文件和 PowerShell 读取文件时，他们需要使用相同的编码系统。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="3eb3f-110">此过程的分析 PowerShell 脚本：*字节* -> *字符* -> *令牌* ->  *抽象语法树* -> *执行*。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="3eb3f-111">VSCode 和 PowerShell 使用意义的默认编码配置安装。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="3eb3f-112">但是，使用 PowerShell 的默认编码已更改的 PowerShell Core (v6.x) 版本。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="3eb3f-113">若要确保具有在 VSCode 中使用 PowerShell 或 PowerShell 扩展没有出现问题，需要配置你的 VSCode 和 PowerShell 设置正确。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="3eb3f-114">编码问题的常见原因</span><span class="sxs-lookup"><span data-stu-id="3eb3f-114">Common causes of encoding issues</span></span>

<span data-ttu-id="3eb3f-115">VSCode 或脚本文件的编码的 PowerShell 所需的编码不匹配时，会出现编码问题。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="3eb3f-116">没有适用于 PowerShell 来自动确定的文件编码方法。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="3eb3f-117">您更有可能具有编码问题，如果你使用的字符不在[7 位 ASCII 字符集](https://ascii.cl/)。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="3eb3f-118">例如：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-118">For example:</span></span>

- <span data-ttu-id="3eb3f-119">带重音符号拉丁字符 (`É`， `ü`)</span><span class="sxs-lookup"><span data-stu-id="3eb3f-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="3eb3f-120">非拉丁字符如西里尔文 (`Д`， `Ц`)</span><span class="sxs-lookup"><span data-stu-id="3eb3f-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="3eb3f-121">Han 中文 (`脚`， `本`)</span><span class="sxs-lookup"><span data-stu-id="3eb3f-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="3eb3f-122">编码问题的常见原因如下：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="3eb3f-123">尚未从其默认设置更改的 VSCode 和 PowerShell 的编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="3eb3f-124">对于 PowerShell 5.1 及更低，默认编码是不同于 VSCode 的。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="3eb3f-125">另一个编辑器已打开，并覆盖中的新编码的文件。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="3eb3f-126">这通常是使用 ISE。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="3eb3f-127">该文件已签入源代码管理中的编码不同哪些 VSCode 或 PowerShell 从需要。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="3eb3f-128">这可以协作者使用具有不同编码的配置编辑器。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="3eb3f-129">如何知道使用了编码问题</span><span class="sxs-lookup"><span data-stu-id="3eb3f-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="3eb3f-130">通常编码错误显示按分析脚本中的错误。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="3eb3f-131">如果您在脚本中发现了奇怪字符序列，这可能是问题。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="3eb3f-132">在以下示例中，为短划线 (`–`) 显示为字符`â€“`:</span><span class="sxs-lookup"><span data-stu-id="3eb3f-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="3eb3f-133">发生此问题的原因 VSCode 对字符进行编码`–`utf-8 字节`0xE2 0x80 0x93`。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="3eb3f-134">当这两个字节作为 Windows 1252 解码后时，它们被解释为字符`â€“`。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="3eb3f-135">你可能会看到一些奇怪的字符序列包括：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="3eb3f-136">`â€“`（而不是 `–`）</span><span class="sxs-lookup"><span data-stu-id="3eb3f-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="3eb3f-137">`â€”`（而不是 `—`）</span><span class="sxs-lookup"><span data-stu-id="3eb3f-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="3eb3f-138">`Ã„2`（而不是 `Ä`）</span><span class="sxs-lookup"><span data-stu-id="3eb3f-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="3eb3f-139">`Â` 而不是` `（非换行空格）</span><span class="sxs-lookup"><span data-stu-id="3eb3f-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="3eb3f-140">`Ã©`（而不是 `é`）</span><span class="sxs-lookup"><span data-stu-id="3eb3f-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="3eb3f-141">上述便捷[引用](https://www.i18nqa.com/debug/utf8-debug.html)列出了指示 UTF-8/Windows-1252年编码问题的常见模式。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="3eb3f-142">PowerShell 扩展在 VSCode 中的使用编码的交互方式</span><span class="sxs-lookup"><span data-stu-id="3eb3f-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="3eb3f-143">PowerShell 扩展中通过多种方式使用脚本进行交互：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="3eb3f-144">当脚本将在 VSCode 中编辑时，内容 vscode 发送到该扩展。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="3eb3f-145">[语言服务器协议][]要求此内容在 utf-8 中传输。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="3eb3f-146">因此，不可能的扩展，以获取编码错误。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="3eb3f-147">脚本执行时直接在集成控制台中，它们是从文件中读取 powershell 直接。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="3eb3f-148">从 VSCode 的 Tf PowerShell 编码不同，某些内容可能会出现以下错误。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-148">Tf PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="3eb3f-149">将在 VSCode 中打开的脚本引用了未在 VSCode 中打开的另一个脚本，该扩展将回退到从文件系统加载该脚本的内容。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="3eb3f-150">PowerShell 扩展默认为 utf-8 编码，但使用[字节顺序标记][]，或 BOM，检测，以选择正确的编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="3eb3f-151">假设采用无 BOM 式格式的编码时出现问题 (如[utf-8][]与没有 BOM 和[Windows-1252][])。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="3eb3f-152">PowerShell 扩展默认为 utf-8。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="3eb3f-153">该扩展不能更改 VSCode 的编码设置。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="3eb3f-154">有关详细信息，请参阅[发出 #824](https://github.com/Microsoft/vscode/issues/824)。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="3eb3f-155">选择正确的编码</span><span class="sxs-lookup"><span data-stu-id="3eb3f-155">Choosing the right encoding</span></span>

<span data-ttu-id="3eb3f-156">不同的系统和应用程序可以使用不同的编码：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="3eb3f-157">在.NET Standard 中，在 web 上，并在 Linux 领域，utf-8 是现在的主流的编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="3eb3f-158">许多.NET Framework 应用程序使用[utf-16][]。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="3eb3f-159">由于历史原因，这有时称为"Unicode"、 一个术语，现在是指广泛[标准](https://en.wikipedia.org/wiki/Unicode)包含 utf-8 和 utf-16。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="3eb3f-160">在 Windows 中上, 许多由 Unicode 的本机应用程序继续以默认情况下使用 Windows 1252。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="3eb3f-161">Unicode 编码还都具有字节顺序标记 (BOM) 的概念。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="3eb3f-162">物料清单出现在要告诉解码器使用文本的编码文本的开头。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="3eb3f-163">对于多字节编码还指示 BOM[字节顺序](https://en.wikipedia.org/wiki/Endianness)的编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="3eb3f-164">Bom 被设计为很少发生在非 Unicode 文本，从而允许文本是 Unicode，如果存在 BOM 合理估计值的字节数。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="3eb3f-165">Bom 是可选的其采用并不常见 Linux 世界中，因为 utf-8 的可靠约定用于各个位置。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="3eb3f-166">大多数 Linux 应用程序假设采用 utf-8 进行编码文本输入。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="3eb3f-167">虽然许多 Linux 应用程序将识别并正确处理一个 BOM，许多不这样做，从而导致项目中使用这些应用程序操作的文本。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="3eb3f-168">**因此**：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-168">**Therefore**:</span></span>

- <span data-ttu-id="3eb3f-169">如果您工作主要与 Windows 应用程序和 Windows PowerShell，您应优先使用如 utf-8 BOM 或 utf-16 编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="3eb3f-170">如果跨平台工作，应优先使用具有 BOM 的 utf-8。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="3eb3f-171">如果您主要在 Linux 关联的上下文中工作，应优先使用 utf-8 无 BOM。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="3eb3f-172">Windows-1252年和拉丁语-1 应尽可能避免实质上是旧的编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="3eb3f-173">但是，某些较旧的 Windows 应用程序可能依赖于它们。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="3eb3f-174">它也是值得注意的是脚本签名[依赖于编码的](https://github.com/PowerShell/PowerShell/issues/3466)，这意味着的编码签名的脚本上的更改需要重新签名。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="3eb3f-175">配置 VSCode</span><span class="sxs-lookup"><span data-stu-id="3eb3f-175">Configuring VSCode</span></span>

<span data-ttu-id="3eb3f-176">VSCode 的默认编码为 utf-8 而无需 BOM。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="3eb3f-177">若要设置[VSCode 的编码][]，请转到 VSCode 设置 (<kbd>Ctrl<kbd>+</kbd>，</kbd>) 并设置`"files.encoding"`设置：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="3eb3f-178">一些可能的值为：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-178">Some possible values are:</span></span>

- <span data-ttu-id="3eb3f-179">`utf8`: [Utf-8]不 BOM</span><span class="sxs-lookup"><span data-stu-id="3eb3f-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="3eb3f-180">`utf8bom`: [Utf-8]与物料清单</span><span class="sxs-lookup"><span data-stu-id="3eb3f-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="3eb3f-181">`utf16le`: Little endian [utf-16]</span><span class="sxs-lookup"><span data-stu-id="3eb3f-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="3eb3f-182">`utf16be`: Big endian [utf-16]</span><span class="sxs-lookup"><span data-stu-id="3eb3f-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="3eb3f-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="3eb3f-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="3eb3f-184">应为此获取下拉列表中，在 GUI 视图中，或查看 JSON 中的其完成。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="3eb3f-185">此外可以为自动检测编码在可能的情况添加以下：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="3eb3f-186">如果不希望这些设置会影响所有文件类型，VSCode 还允许每种语言的配置。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="3eb3f-187">创建特定于语言的设置将设置放在`[<language-name>]`字段。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="3eb3f-188">例如：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="3eb3f-189">配置 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3eb3f-189">Configuring PowerShell</span></span>

<span data-ttu-id="3eb3f-190">PowerShell 的默认编码版本而异：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="3eb3f-191">在 PowerShell 6 + 中，默认编码在所有平台上是无 BOM utf-8。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="3eb3f-192">在 Windows PowerShell 中，默认编码为通常 Windows-1252 的扩展[latin 1][]，也称为 ISO 8859-1。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="3eb3f-193">在 PowerShell 5 + 你可以找到与此默认编码：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="3eb3f-194">以下[脚本](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)可用于确定哪些编码到 PowerShell 会话来推断为不带 BOM 的脚本。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="3eb3f-195">就可以配置 PowerShell 以使用给定编码更普遍的情况使用配置文件设置。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="3eb3f-196">请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-196">See the following articles:</span></span>

- <span data-ttu-id="3eb3f-197">[@mklement0][有关 PowerShell 编码在 StackOverflow 上的答案](https://stackoverflow.com/a/40098904)。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="3eb3f-198">[@rkeithhill][有关在 PowerShell 中的无 BOM 的 utf-8 输入处理的博客文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="3eb3f-199">不能强制 PowerShell 以使用特定的输入编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="3eb3f-200">PowerShell 5.1 及以下默认值为 Windows-1252 编码时没有 bom。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="3eb3f-201">互操作性方面的考虑，最好将脚本保存具有 BOM 以 Unicode 格式。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3eb3f-202">任何其他工具可以触摸 PowerShell 脚本可能会受到您编码的选择，或重新对您的脚本到另一种编码进行编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="3eb3f-203">现有脚本</span><span class="sxs-lookup"><span data-stu-id="3eb3f-203">Existing scripts</span></span>

<span data-ttu-id="3eb3f-204">已在文件系统上的脚本可能需要进行重新编码为在新的所选编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="3eb3f-205">在 VSCode 底部栏，您将看到标签 utf-8。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="3eb3f-206">单击它以打开操作栏并选择**使用编码来保存**。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="3eb3f-207">现在，可以选取该文件的新编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="3eb3f-208">请参阅[VSCode 的编码][]有关的完整说明。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="3eb3f-209">如果你需要重新对多个文件进行编码，可以使用以下脚本：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="3eb3f-210">PowerShell 集成脚本环境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="3eb3f-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="3eb3f-211">如果您还可以编辑使用 PowerShell ISE 的脚本，需要同步那里编码设置。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="3eb3f-212">在 ISE 应遵循 BOM，但也可以使用反射来[设置的编码](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="3eb3f-213">请注意这不会保存新创公司之间。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="3eb3f-214">源代码管理软件</span><span class="sxs-lookup"><span data-stu-id="3eb3f-214">Source control software</span></span>

<span data-ttu-id="3eb3f-215">某些源代码管理工具，例如 git、 忽略编码;git 只会跟踪字节。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="3eb3f-216">其他人，例如 TFS 或 Mercurial，可能不允许。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="3eb3f-217">甚至一些基于 git 的工具依赖于解码的文本。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="3eb3f-218">在这种情况下，请确保：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="3eb3f-219">配置您的源代码管理以匹配 VSCode 配置中的编码的文本。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="3eb3f-220">请确保所有文件已签都入到源代码管理中的相关的编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="3eb3f-221">应谨慎地对接收通过源控件的编码更改。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="3eb3f-222">此密钥登录是差异，该值指示的更改，但执行任何操作似乎已更改 （因为字节但字符不具有）。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="3eb3f-223">协作者环境</span><span class="sxs-lookup"><span data-stu-id="3eb3f-223">Collaborators' environments</span></span>

<span data-ttu-id="3eb3f-224">基于配置源代码管理，请确保您协作者共享的任何文件上没有替代你通过 PowerShell 文件进行重新编码的编码的设置。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="3eb3f-225">其他程序</span><span class="sxs-lookup"><span data-stu-id="3eb3f-225">Other programs</span></span>

<span data-ttu-id="3eb3f-226">其他任何程序，读取或写入的 PowerShell 脚本可能会重新对其进行编码。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="3eb3f-227">一些示例如下：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-227">Some examples are:</span></span>

- <span data-ttu-id="3eb3f-228">使用剪贴板复制和粘贴脚本。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="3eb3f-229">这是常见的方案，例如：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="3eb3f-230">将脚本复制到 VM</span><span class="sxs-lookup"><span data-stu-id="3eb3f-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="3eb3f-231">复制电子邮件或网页的脚本</span><span class="sxs-lookup"><span data-stu-id="3eb3f-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="3eb3f-232">将脚本复制入或移出 Microsoft Word 或 PowerPoint 文档</span><span class="sxs-lookup"><span data-stu-id="3eb3f-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="3eb3f-233">其他文本编辑器，如：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="3eb3f-234">记事本</span><span class="sxs-lookup"><span data-stu-id="3eb3f-234">Notepad</span></span>
  - <span data-ttu-id="3eb3f-235">vim</span><span class="sxs-lookup"><span data-stu-id="3eb3f-235">vim</span></span>
  - <span data-ttu-id="3eb3f-236">任何其他 PowerShell 脚本编辑器</span><span class="sxs-lookup"><span data-stu-id="3eb3f-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="3eb3f-237">文本编辑实用程序，如：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="3eb3f-238">PowerShell 重定向运算符，例如`>`和 `>>`</span><span class="sxs-lookup"><span data-stu-id="3eb3f-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="3eb3f-239">文件传输的程序，如：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="3eb3f-240">Web 浏览器下载脚本时</span><span class="sxs-lookup"><span data-stu-id="3eb3f-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="3eb3f-241">文件共享</span><span class="sxs-lookup"><span data-stu-id="3eb3f-241">A file share</span></span>

<span data-ttu-id="3eb3f-242">其中某些工具处理在字节而不是文本，但其他人提供编码配置。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="3eb3f-243">在这些情况下，您需要配置的编码，您需要使其与编码以防止出现问题你编辑器相同。</span><span class="sxs-lookup"><span data-stu-id="3eb3f-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="3eb3f-244">在 PowerShell 中的编码的其他资源</span><span class="sxs-lookup"><span data-stu-id="3eb3f-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="3eb3f-245">有几个其他很好帖子编码和配置 PowerShell 中的编码值得读取：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="3eb3f-246">[@mklement0][PowerShell 编码在 StackOverflow 上的摘要](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="3eb3f-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="3eb3f-247">在 vscode PowerShell 编码问题上打开上一个问题：</span><span class="sxs-lookup"><span data-stu-id="3eb3f-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="3eb3f-248">#1308</span><span class="sxs-lookup"><span data-stu-id="3eb3f-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="3eb3f-249">#1628</span><span class="sxs-lookup"><span data-stu-id="3eb3f-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="3eb3f-250">#1680</span><span class="sxs-lookup"><span data-stu-id="3eb3f-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="3eb3f-251">#1744</span><span class="sxs-lookup"><span data-stu-id="3eb3f-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="3eb3f-252">#1751</span><span class="sxs-lookup"><span data-stu-id="3eb3f-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="3eb3f-253">经典*Joel 讲述软件*编写关于 Unicode</span><span class="sxs-lookup"><span data-stu-id="3eb3f-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="3eb3f-254">.NET Standard 中的编码</span><span class="sxs-lookup"><span data-stu-id="3eb3f-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[字节顺序标记]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[语言服务器协议]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode 的编码]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support