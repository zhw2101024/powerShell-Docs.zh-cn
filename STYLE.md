<a id="style-guide-for-powershell-docs" class="xliff"></a>
# PowerShell 文档的风格指南


<a id="titlesheadings" class="xliff"></a>
## 标题

* 标题（由 \# 预先设定的任何内容））后应换行
* 仅大写标题的第一个字母和该标题中的全部专有名词
* 每个文档只有 1 个 H1
* 编辑参考内容时，H2 由 PlatyPUS 规定，不能进行添加或删除，否则将导致构建中断
* 只使用 \# 样式标题（而不是 = 或 \- 样式标题）

<a id="correct" class="xliff"></a>
### 正确

```
# Header 1

## Header 2

### Header 3

```

<a id="incorrect" class="xliff"></a>
### 不正确

```
Header 1
========

Header 2
--------

### Header 3
```

<a id="syntax" class="xliff"></a>
## 语法

* 当谈到段落中的一个 cmdlet 时，使用 \` 突出显示 cmdlet 名称
  * 正确示例：此 `Write-Host` Cmdlet 可以...
  * 错误示例：此 Write-host Cmdlet 可以...并通过管道传递到 out-file Cmdlet 以...
* 在撰写文章（而不是参考内容）时，cmdlet 名称的第一个实例应该是指向 cmdlet 文档的链接
* 所有 PowerShell 语法块都应使用 ```powershell
* 不要让 PowerShell 命令以“`PS C:\>`”为开头
  * 正确示例：
  ```powershell
  Get-Process
  ```
  * 错误示例：
  ```powershell
  PS C:\> Get-Process
  ```
* 应对 PowerShell 命令发出的输出进行注释，以防止它接收突出显示的语法
* 属性名称和参数名称应为**粗体**样式
* PowerShell cmdlet 采用[帕斯卡命名法](https://en.wikipedia.org/wiki/PascalCase)。 谓词与名词通过连字符分隔开来。

<a id="lists" class="xliff"></a>
## 列表

* 不要使用句点结束列表项（除非它们包含多个句子）
* 如果你的列表包含多个句子，请考虑在主要设想下使用标题 3/4/5（如果适用）

<a id="links" class="xliff"></a>
## 链接

* 始终使用 MarkDown 语法 `[friendlyname](url)` 标记链接
* 链接应具有友好名称（如适用），最有可能是链接页面的标题
  * **例外情况**：指向非 Microsoft 网站的链接只能具有 URL
* 底部“相关链接”部分中的所有项都应具有超链接。 

<a id="line-breaks" class="xliff"></a>
## 换行符

* 必须包括语义换行符
* 应将行限制为 100 个字符（打开项目：可帮助我们验证此限制的工具）
* 你可以删除 PS4+、非 ps3（需要验证）的其他换行符
