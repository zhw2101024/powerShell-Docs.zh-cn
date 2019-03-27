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
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>了解 VSCode 和 PowerShell 中的文件编码

使用 VS Code 创建和编辑 PowerShell 脚本时，务必使用正确的字符编码格式保存文件。

## <a name="what-is-file-encoding-and-why-is-it-important"></a>什么是文件编码以及它为什么很重要？

VSCode 管理人员向缓冲区中输入字符串与对文件系统读取/写入字节块之间的接口。 VSCode 保存文件时，会使用文本编码执行此操作。

同样，当 PowerShell 运行脚本时，必须将文件中的字节转换为字符以将文件重新构造为 PowerShell 程序。 由于 VSCode 写入文件，而 PowerShell 读取文件，因此它们需要使用相同的编码系统。 分析 PowerShell 脚本的这一过程是：字节 -> 字符 -> 标记 -> 抽象语法树 -> 执行。

VSCode 和 PowerShell 都使用合理的默认编码配置进行安装。 但是，PowerShell 使用的默认编码已随着 PowerShell Core (v6.x) 的发布而更改。 若要确保在 VSCode 中使用 PowerShell 或 PowerShell 扩展时不会出现问题，需要正确配置 VSCode 和 PowerShell 设置。

## <a name="common-causes-of-encoding-issues"></a>编码问题的常见原因

当 VSCode 或脚本文件的编码与 PowerShell 的期望编码不匹配时，会出现编码问题。 PowerShell 无法自动确定文件编码。

如果使用的字符不在 [7 位 ASCII 字符集](https://ascii.cl/)中，则更可能出现编码问题。 例如：

- 重音拉丁字符（`É`、`ü`）
- 非拉丁字符，如西里尔文（`Д`、`Ц`）
- 汉字（`脚`、`本`）

编码问题的常见原因有：

- VSCode 和 PowerShell 的编码尚未更改，仍使用默认设置。 对于 PowerShell 5.1 及更低版本，默认编码与 VSCode 不同。
- 另一个编辑器已打开，并采用新编码覆盖了文件。 ISE 通常会发生这种情况。
- 文件采用与 VSCode 或 PowerShell 期望编码不同的编码签入了源代码管理。 当协作者使用具有不同编码配置的编辑器时，可能会发生这种情况。

### <a name="how-to-tell-when-you-have-encoding-issues"></a>如何判断出现了编码问题

编码错误通常表现为脚本中的分析错误。 如果在脚本中发现奇怪的字符序列，则这可能是问题所在。 在以下示例中，短划线 (`–`) 显示为字符 `â€“`：

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

发生此问题的原因是 VSCode 将采用 UTF-8 的字符 `–` 编码为字节 `0xE2 0x80 0x93`。
当这些字节解码为 Windows-1252 时，它们会被解释为字符 `â€“`。

可能会看到的一些奇怪字符序列包括：

<!-- markdownlint-disable MD038 -->
- `â€“`（而不是 `–`）
- `â€”`（而不是 `—`）
- `Ã„2`（而不是 `Ä`）
- `Â`（而不是 ` `（不间断空格））
- `Ã©`（而不是 `é`）
<!-- markdownlint-enable MD038 -->

此便捷[参考](https://www.i18nqa.com/debug/utf8-debug.html)列出了指示 UTF-8/Windows-1252 编码问题的常见模式。

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>VSCode 中的 PowerShell 扩展与编码的交互方式

PowerShell 扩展通过多种方式与脚本进行交互：

1. 当脚本在 VSCode 中进行编辑时，内容由 VSCode 发送到扩展。 [语言服务器协议][]要求此内容采用 UTF-8 进行传输。 因此，扩展不可能获取错误的编码。
2. 当脚本直接在集成控制台中执行时，它们直接由 PowerShell 从文件读取。 如果 PowerShell 的编码与 VSCode 不同，则可能会出错。
3. 当在 VSCode 中打开的一个脚本引用未在 VSCode 中打开的另一个脚本时，扩展会回退到从文件系统加载该脚本的内容。 PowerShell 扩展默认为 UTF-8 编码，但使用[字节顺序标记][]（或 BOM）检测来选择正确编码。

当采用无 BOM 式格式的编码（如没有 BOM 的 [UTF-8][] 和 [Windows-1252][]）时，会出现问题。
PowerShell 扩展默认为 UTF-8。 扩展无法更改 VSCode 的编码设置。
有关详细信息，请参阅[问题 #824](https://github.com/Microsoft/vscode/issues/824)。

## <a name="choosing-the-right-encoding"></a>选择正确编码

不同的系统和应用程序可以使用不同的编码：

- 在 .NET Standard 中、Web 上以及 Linux 领域中，UTF-8 现在是主流编码。
- 许多 .NET Framework 应用程序使用 [UTF-16][]。 由于历史原因，这有时称为“Unicode”，该术语现在是指包括 UTF-8 和 UTF-16 在内的广泛[标准](https://en.wikipedia.org/wiki/Unicode)。
- 在 Windows 中上，早于 Unicode 出现的许多本机应用程序在默认情况下继续使用 Windows-1252。

Unicode 编码也具有字节顺序标记 (BOM) 的概念。 BOM 在文本开头出现，用于向解码器告知文本所使用的编码。 对于多字节编码，BOM 还指示编码的[字节顺序](https://en.wikipedia.org/wiki/Endianness)。 BOM 设计为很少出现在非 Unicode 文本中的字节，从而当 BOM 存在时可以合理地猜测文本是 Unicode。

BOM 是可选的，其采用在 Linux 领域中并不普遍，因为到处都在使用可靠的 UTF-8 约定。 大多数 Linux 应用程序假设文本输入采用 UTF-8 进行编码。 虽然许多 Linux 应用程序可识别并正确处理 BOM，不过有一些应用程序无法这样做，从而导致使用这些应用程序操作的文本中出现异常。

**因此**：

- 如果主要使用 Windows 应用程序和 Windows PowerShell，则应优先使用诸如具有 BOM 的 UTF-8 或 UTF-16 这类编码。
- 如果跨平台工作，则应优先使用具有 BOM 的 UTF-8。
- 如果主要在与 Linux 关联的环境中工作，则应优先使用不具有 BOM 的 UTF-8。
- Windows-1252 和拉丁语-1 本质上是旧编码，应尽可能避免使用。
  但是，某些较旧的 Windows 应用程序可能依赖于它们。
- 另外值得注意的是，脚本签名[依赖于编码](https://github.com/PowerShell/PowerShell/issues/3466)，这意味着签名脚本中的编码更改需要重新签名。

## <a name="configuring-vscode"></a>配置 VSCode

VSCode 的默认编码是不具有 BOM 的 UTF-8。

若要设置 [VSCode 的编码][]，请转到 VSCode 设置（<kbd>Ctrl<kbd>+</kbd>，</kbd>）并设置 `"files.encoding"` 设置：

```json
"files.encoding": "utf8bom"
```

一些可能值有：

- `utf8`：不具有 BOM 的 [UTF-8]
- `utf8bom`：具有 BOM 的 [UTF-8]
- `utf16le`：Little endian [UTF-16]
- `utf16be`：Big endian [UTF-16]
- `windows1252`：[Windows-1252]

应在 GUI 视图中看到适用于此内容的下拉列表，或是在 JSON 视图中看到其完成。

还可以添加以下内容以尽可能自动检测编码：

```json
"files.autoGuessEncoding": true
```

如果不希望这些设置影响所有文件类型，则 VSCode 还允许按语言进行配置。 创建在 `[<language-name>]` 字段中放置设置，可以配置特定于语言的设置。 例如：

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>配置 PowerShell

PowerShell 的默认编码因版本而异：

- 在 PowerShell 6+ 中，默认编码在所有平台上都是不具有 BOM 的 UTF-8。
- 在 Windows PowerShell 中，默认编码通常是 Windows-1252，这是[拉丁语-1][] 的扩展，也称为 ISO 8859-1。

在 PowerShell 5+ 中，可以使用以下方法查找默认编码：

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

以下[脚本](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)用于确定 PowerShell 会话对不具有 BOM 的脚本推断出何种编码。

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

可以更普遍地使用配置文件设置将 PowerShell 配置为使用给定编码。 请参阅以下文章：

- [@mklement0] [有关 StackOverflow 上的 PowerShell 编码的解答](https://stackoverflow.com/a/40098904)。
- [@rkeithhill] [有关在 PowerShell 中处理无 BOM 式 UTF-8 输入的博客文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。

无法强制 PowerShell 使用特定输入编码。 在没有 BOM 时，PowerShell 5.1 及以下版本默认为 Windows-1252 编码。 出于互操作性原因，最好使用具有 BOM 的 Unicode 格式保存脚本。

> [!IMPORTANT]
> 涉及 PowerShell 脚本的任何其他工具都可能会受到编码选择的影响，或是将脚本重新编码为另一种编码。

### <a name="existing-scripts"></a>现有脚本

文件系统上已有的脚本可能需要重新编码为新的所选编码。 在 VSCode 底部栏中，会看到 UTF-8 标签。 单击它可打开操作栏并选择“保存时使用编码”。 现在可以为该文件选取新编码。 有关完整说明，请参阅 [VSCode 的编码][]。

如果需要重新编码多个文件，则可以使用以下脚本：

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell 集成脚本环境 (ISE)

如果还使用 PowerShell ISE 编辑脚本，则需要在其中同步编码设置。

ISE 应遵循 BOM，但也可以使用反射来[设置编码](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。
请注意，这不会在启动之间保持。

### <a name="source-control-software"></a>源代码管理软件

一些源代码管理工具（如 git）会忽略编码；git 只跟踪字节。
其他工具（如 Azure DevOps 或 Mercurial）可能不会忽略编码。 甚至一些基于 git 的工具也依赖于文本解码。

在这种情况下，请确保：

- 在源代码管理中配置文本编码以匹配 VSCode 配置。
- 确保所有文件都采用相关编码签入到源代码管理中。
- 应注意通过源代码管理收到的编码更改。 这种情况的一个重要迹象是有差异指示更改，但似乎没有任何内容发生更改（因为字节更改，但字符未更改）。

### <a name="collaborators-environments"></a>协作者环境

在配置源代码管理的基础上，确保你所共享的任何文件上的协作者没有通过重新编码 PowerShell 文件来替代你的编码的设置。

### <a name="other-programs"></a>其他程序

读取或写入 PowerShell 脚本的其他任何程序都可能会对它重新编码。

一些示例如下：

- 使用剪贴板复制和粘贴脚本。 这是以下这类情形中十分常见：
  - 将脚本复制到 VM 中
  - 从电子邮件或网页中复制脚本
  - 将脚本复制到 Microsoft Word 或 PowerPoint 文档中，或从这类文档中复制脚本
- 其他文本编辑器，如：
  - 记事本
  - vim
  - 任何其他 PowerShell 脚本编辑器
- 文本编辑实用工具，如：
  - `Get-Content`/`Set-Content`/`Out-File`
  - PowerShell 重定向运算符，如 `>` 和 `>>`
  - `sed`/`awk`
- 文件传输程序，如：
  - Web 浏览器（下载脚本时）
  - 文件共享

其中一些工具以字节（而不是文本）进行处理，而其他工具提供编码配置。 在需要配置编码的情况下，需要使它与编辑器编码相同，以防止出现问题。

## <a name="other-resources-on-encoding-in-powershell"></a>有关 PowerShell 中的编码的其他资源

有其他几篇有关在 PowerShell 中编码和配置编码的很好的文章值得一读：

- [@mklement0] 的 [StackOverflow 上的 PowerShell 编码摘要](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- 以前在 vscode-PowerShell 上建立的针对编码问题的问题：
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [经典的“Joel 说软件”探讨 Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [.NET Standard 中的编码](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[拉丁语-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[字节顺序标记]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[语言服务器协议]: https://microsoft.github.io/language-server-protocol/
[VSCode 的编码]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
