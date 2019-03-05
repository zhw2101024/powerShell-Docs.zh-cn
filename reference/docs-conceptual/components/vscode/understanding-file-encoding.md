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
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>了解 VSCode 和 PowerShell 中的文件编码

当使用 VS Code 创建和编辑 PowerShell 脚本，务必使用正确的字符编码格式保存文件。

## <a name="what-is-file-encoding-and-why-is-it-important"></a>什么是文件编码和为什么很重要？

VSCode 管理到缓冲区的字符组成的人工输入字符串和字节到文件系统读取/写入块之间的接口。 在将文件保存在 VSCode，它使用文本编码来执行此操作。

同样，当 PowerShell 运行脚本时它必须将文件中的字节转换为字符以将文件重构到 PowerShell 程序。 由于 VSCode 写入该文件和 PowerShell 读取文件时，他们需要使用相同的编码系统。 此过程的分析 PowerShell 脚本：*字节* -> *字符* -> *令牌* ->  *抽象语法树* -> *执行*。

VSCode 和 PowerShell 使用意义的默认编码配置安装。 但是，使用 PowerShell 的默认编码已更改的 PowerShell Core (v6.x) 版本。 若要确保具有在 VSCode 中使用 PowerShell 或 PowerShell 扩展没有出现问题，需要配置你的 VSCode 和 PowerShell 设置正确。

## <a name="common-causes-of-encoding-issues"></a>编码问题的常见原因

VSCode 或脚本文件的编码的 PowerShell 所需的编码不匹配时，会出现编码问题。 没有适用于 PowerShell 来自动确定的文件编码方法。

您更有可能具有编码问题，如果你使用的字符不在[7 位 ASCII 字符集](https://ascii.cl/)。 例如：

- 带重音符号拉丁字符 (`É`， `ü`)
- 非拉丁字符如西里尔文 (`Д`， `Ц`)
- Han 中文 (`脚`， `本`)

编码问题的常见原因如下：

- 尚未从其默认设置更改的 VSCode 和 PowerShell 的编码。 对于 PowerShell 5.1 及更低，默认编码是不同于 VSCode 的。
- 另一个编辑器已打开，并覆盖中的新编码的文件。 这通常是使用 ISE。
- 该文件已签入源代码管理中的编码不同哪些 VSCode 或 PowerShell 从需要。 这可以协作者使用具有不同编码的配置编辑器。

### <a name="how-to-tell-when-you-have-encoding-issues"></a>如何知道使用了编码问题

通常编码错误显示按分析脚本中的错误。 如果您在脚本中发现了奇怪字符序列，这可能是问题。 在以下示例中，为短划线 (`–`) 显示为字符`â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

发生此问题的原因 VSCode 对字符进行编码`–`utf-8 字节`0xE2 0x80 0x93`。
当这两个字节作为 Windows 1252 解码后时，它们被解释为字符`â€“`。

你可能会看到一些奇怪的字符序列包括：

- `â€“`（而不是 `–`）
- `â€”`（而不是 `—`）
- `Ã„2`（而不是 `Ä`）
- `Â` 而不是` `（非换行空格）
- `Ã©`（而不是 `é`）

上述便捷[引用](https://www.i18nqa.com/debug/utf8-debug.html)列出了指示 UTF-8/Windows-1252年编码问题的常见模式。

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>PowerShell 扩展在 VSCode 中的使用编码的交互方式

PowerShell 扩展中通过多种方式使用脚本进行交互：

1. 当脚本将在 VSCode 中编辑时，内容 vscode 发送到该扩展。 [语言服务器协议][]要求此内容在 utf-8 中传输。 因此，不可能的扩展，以获取编码错误。
2. 脚本执行时直接在集成控制台中，它们是从文件中读取 powershell 直接。 从 VSCode 的 Tf PowerShell 编码不同，某些内容可能会出现以下错误。
3. 将在 VSCode 中打开的脚本引用了未在 VSCode 中打开的另一个脚本，该扩展将回退到从文件系统加载该脚本的内容。 PowerShell 扩展默认为 utf-8 编码，但使用[字节顺序标记][]，或 BOM，检测，以选择正确的编码。

假设采用无 BOM 式格式的编码时出现问题 (如[utf-8][]与没有 BOM 和[Windows-1252][])。
PowerShell 扩展默认为 utf-8。 该扩展不能更改 VSCode 的编码设置。
有关详细信息，请参阅[发出 #824](https://github.com/Microsoft/vscode/issues/824)。

## <a name="choosing-the-right-encoding"></a>选择正确的编码

不同的系统和应用程序可以使用不同的编码：

- 在.NET Standard 中，在 web 上，并在 Linux 领域，utf-8 是现在的主流的编码。
- 许多.NET Framework 应用程序使用[utf-16][]。 由于历史原因，这有时称为"Unicode"、 一个术语，现在是指广泛[标准](https://en.wikipedia.org/wiki/Unicode)包含 utf-8 和 utf-16。
- 在 Windows 中上, 许多由 Unicode 的本机应用程序继续以默认情况下使用 Windows 1252。

Unicode 编码还都具有字节顺序标记 (BOM) 的概念。 物料清单出现在要告诉解码器使用文本的编码文本的开头。 对于多字节编码还指示 BOM[字节顺序](https://en.wikipedia.org/wiki/Endianness)的编码。 Bom 被设计为很少发生在非 Unicode 文本，从而允许文本是 Unicode，如果存在 BOM 合理估计值的字节数。

Bom 是可选的其采用并不常见 Linux 世界中，因为 utf-8 的可靠约定用于各个位置。 大多数 Linux 应用程序假设采用 utf-8 进行编码文本输入。 虽然许多 Linux 应用程序将识别并正确处理一个 BOM，许多不这样做，从而导致项目中使用这些应用程序操作的文本。

**因此**：

- 如果您工作主要与 Windows 应用程序和 Windows PowerShell，您应优先使用如 utf-8 BOM 或 utf-16 编码。
- 如果跨平台工作，应优先使用具有 BOM 的 utf-8。
- 如果您主要在 Linux 关联的上下文中工作，应优先使用 utf-8 无 BOM。
- Windows-1252年和拉丁语-1 应尽可能避免实质上是旧的编码。
  但是，某些较旧的 Windows 应用程序可能依赖于它们。
- 它也是值得注意的是脚本签名[依赖于编码的](https://github.com/PowerShell/PowerShell/issues/3466)，这意味着的编码签名的脚本上的更改需要重新签名。

## <a name="configuring-vscode"></a>配置 VSCode

VSCode 的默认编码为 utf-8 而无需 BOM。

若要设置[VSCode 的编码][]，请转到 VSCode 设置 (<kbd>Ctrl<kbd>+</kbd>，</kbd>) 并设置`"files.encoding"`设置：

```json
"files.encoding": "utf8bom"
```

一些可能的值为：

- `utf8`: [Utf-8]不 BOM
- `utf8bom`: [Utf-8]与物料清单
- `utf16le`: Little endian [utf-16]
- `utf16be`: Big endian [utf-16]
- `windows1252`: [Windows-1252]

应为此获取下拉列表中，在 GUI 视图中，或查看 JSON 中的其完成。

此外可以为自动检测编码在可能的情况添加以下：

```json
"files.autoGuessEncoding": true
```

如果不希望这些设置会影响所有文件类型，VSCode 还允许每种语言的配置。 创建特定于语言的设置将设置放在`[<language-name>]`字段。 例如：

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>配置 PowerShell

PowerShell 的默认编码版本而异：

- 在 PowerShell 6 + 中，默认编码在所有平台上是无 BOM utf-8。
- 在 Windows PowerShell 中，默认编码为通常 Windows-1252 的扩展[latin 1][]，也称为 ISO 8859-1。

在 PowerShell 5 + 你可以找到与此默认编码：

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

以下[脚本](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)可用于确定哪些编码到 PowerShell 会话来推断为不带 BOM 的脚本。

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

就可以配置 PowerShell 以使用给定编码更普遍的情况使用配置文件设置。 请参阅以下文章：

- [@mklement0][有关 PowerShell 编码在 StackOverflow 上的答案](https://stackoverflow.com/a/40098904)。
- [@rkeithhill][有关在 PowerShell 中的无 BOM 的 utf-8 输入处理的博客文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。

不能强制 PowerShell 以使用特定的输入编码。 PowerShell 5.1 及以下默认值为 Windows-1252 编码时没有 bom。 互操作性方面的考虑，最好将脚本保存具有 BOM 以 Unicode 格式。

> [!IMPORTANT]
> 任何其他工具可以触摸 PowerShell 脚本可能会受到您编码的选择，或重新对您的脚本到另一种编码进行编码。

### <a name="existing-scripts"></a>现有脚本

已在文件系统上的脚本可能需要进行重新编码为在新的所选编码。 在 VSCode 底部栏，您将看到标签 utf-8。 单击它以打开操作栏并选择**使用编码来保存**。 现在，可以选取该文件的新编码。 请参阅[VSCode 的编码][]有关的完整说明。

如果你需要重新对多个文件进行编码，可以使用以下脚本：

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell 集成脚本环境 (ISE)

如果您还可以编辑使用 PowerShell ISE 的脚本，需要同步那里编码设置。

在 ISE 应遵循 BOM，但也可以使用反射来[设置的编码](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。
请注意这不会保存新创公司之间。

### <a name="source-control-software"></a>源代码管理软件

某些源代码管理工具，例如 git、 忽略编码;git 只会跟踪字节。
其他人，例如 TFS 或 Mercurial，可能不允许。 甚至一些基于 git 的工具依赖于解码的文本。

在这种情况下，请确保：

- 配置您的源代码管理以匹配 VSCode 配置中的编码的文本。
- 请确保所有文件已签都入到源代码管理中的相关的编码。
- 应谨慎地对接收通过源控件的编码更改。 此密钥登录是差异，该值指示的更改，但执行任何操作似乎已更改 （因为字节但字符不具有）。

### <a name="collaborators-environments"></a>协作者环境

基于配置源代码管理，请确保您协作者共享的任何文件上没有替代你通过 PowerShell 文件进行重新编码的编码的设置。

### <a name="other-programs"></a>其他程序

其他任何程序，读取或写入的 PowerShell 脚本可能会重新对其进行编码。

一些示例如下：

- 使用剪贴板复制和粘贴脚本。 这是常见的方案，例如：
  - 将脚本复制到 VM
  - 复制电子邮件或网页的脚本
  - 将脚本复制入或移出 Microsoft Word 或 PowerPoint 文档
- 其他文本编辑器，如：
  - 记事本
  - vim
  - 任何其他 PowerShell 脚本编辑器
- 文本编辑实用程序，如：
  - `Get-Content`/`Set-Content`/`Out-File`
  - PowerShell 重定向运算符，例如`>`和 `>>`
  - `sed`/`awk`
- 文件传输的程序，如：
  - Web 浏览器下载脚本时
  - 文件共享

其中某些工具处理在字节而不是文本，但其他人提供编码配置。 在这些情况下，您需要配置的编码，您需要使其与编码以防止出现问题你编辑器相同。

## <a name="other-resources-on-encoding-in-powershell"></a>在 PowerShell 中的编码的其他资源

有几个其他很好帖子编码和配置 PowerShell 中的编码值得读取：

- [@mklement0][PowerShell 编码在 StackOverflow 上的摘要](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- 在 vscode PowerShell 编码问题上打开上一个问题：
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [经典*Joel 讲述软件*编写关于 Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [.NET Standard 中的编码](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[字节顺序标记]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[语言服务器协议]: https://microsoft.github.io/language-server-protocol/
[VSCode 的编码]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support