# <a name="contributing-to-powershell-documentation"></a>贡献 PowerShell 文档

感谢对 PowerShell 文档的关注！ 参阅下方内容，了解如何贡献技术文档。

>有关 Git 和 GitHub 入门的常规信息，请参阅 [GitHub Help](https://help.github.com/)（GitHub 帮助）。 

## <a name="sign-a-cla"></a>签订 CLA

向 PowerShell 存储库中贡献文档前，必须[签订 Microsoft 文档贡献许可协议 (CLA)](https://cla.microsoft.com/)。 如果之前已在 PowerShell 存储库中贡献有文档，那么祝贺你！ 你已经完成此步骤。

## <a name="providing-feedback-on-powershell-documentation"></a>提供有关 PowerShell 文档的反馈

可指出错误、提出更改建议，或通过在 [PowerShell-Docs 存储库问题页](https://help.github.com/articles/creating-an-issue/)上[创建问题](https://github.com/PowerShell/PowerShell-Docs/issues)来请求新的主题。

PowerShell 文档团队成员会定期审查问题，并相应对问题进行鉴别、分配和处理。

## <a name="writing-powershell-documentation"></a>撰写 PowerShell 文档

向 PowerShell 贡献文档最简单的一种方式是协助撰写和编辑文档。 GitHub 上托管的所有文档都是使用 [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/) 进行撰写的。

## <a name="making-minor-edits-to-existing-topics"></a>对现有主题进行少量编辑

要[编辑现有文件](https://help.github.com/articles/editing-files-in-another-user-s-repository/)，只需导航到相应文件，然后单击“编辑”按钮。 GitHub 会自动创建用户的存储库分叉，用户可在其中进行更改。 完成后，保存编辑后的内容，然后向 [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 存储库的临时分支提交[拉取请求](https://help.github.com/articles/creating-a-pull-request/)。 创建拉取请求后，PowerShell 文档团队成员会审核更改，然后将其并入临时分支。

## <a name="making-major-edits-to-existing-topics"></a>对现有主题进行大量编辑

如果要对现有文章作出较大修改、添加或更改图像，或贡献新文章，则需要手动创建 GitHub 分叉，然后将分叉克隆到本地计算机。 分叉是 GitHub 帐户下基于 GitHub 的主存储库副本，提供可单独使用的工作副本。 需从分叉创建拉取请求。 同样，克隆是基于本地的存储库副本（此情况下即为分叉的克隆）。 通过克隆，可脱机使用 Git 存储库，并可使用更强大的本机软件/工具。

以下是对现有文档作出大量编辑的工作流程：

1. 为 [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 存储库[创建分叉](https://help.github.com/articles/fork-a-repo/)。
2. 在本地计算机上[创建分叉的克隆](https://help.github.com/articles/cloning-a-repository/)。
3. 在克隆的存储库中创建新的本地分支。
4. 在 Markdown 编辑器中对要更新的文件进行更改。 
   相关的常用 Markdown 编辑器详见下文。
5. 向分叉[推送本地分支](https://help.github.com/articles/pushing-to-a-remote/)。
6. 对 [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 存储库的临时分支[创建拉取请求](https://help.github.com/articles/creating-a-pull-request/)。

## <a name="creating-new-topics"></a>创建新主题

若要贡献新的文档，首先请查看[标记为“正在进行”的问题](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress)，以确保避免重复性工作。
如果没人在处理你计划的内容：

* 打开一个新问题，将其标记为“正在进行”（如果你是 PowerShell 组织的成员）或添加“正在进行”注释以告诉其他人你目前准备处理的内容
* 若要对现有主题作出大量编辑，请执行上述相同的工作流程。
* 编辑 `TOC.md` 主题（位于每个文档集的顶级文件夹）以将新主题添加到目录。 
  确定新主题在目录中的位置，然后添加相应级别的标题，并附上主题的链接 (`[My topic title](relative path to my topic)`)。

## <a name="markdown-editors"></a>Markdown 编辑器

以下是一些可使用的 Markdown 编辑器：

* [Visual Studio Code](https://code.visualstudio.com)
* [Markdown Pad](http://markdownpad.com/)
* [Atom](https://atom.io/)
* [Sublime Text](http://www.sublimetext.com/)


## <a name="github-flavored-markdown-gfm"></a>GitHub Flavored Markdown (GFM)

此存储库中的所有文章均使用 [GitHub Flavored Markdown (GFM)](https://help.github.com/articles/github-flavored-markdown/)。

部分基本 GFM 语法包括：

* **换行符与段落：**Markdown 中不存在 HTML `<br />` 或 `<p />` 元素。 而是由两个文本块之间的空行指定新段落。

> **注意**：请在每个句子后添加单个新行来简化差异和历史记录的命令行输出。
当前并非所有的 PowerShell-Docs 都采用此方法，但以后会逐渐统一使用此方式。 欢迎随时提供贡献和帮助。 

* **斜体：**HTML`<em>some text</em>` 元素编写为 `*some text*`
* **粗体：**HTML`<strong>some text</strong>` 元素编写为 `**some text**`
* **标题：**在行的开头使用 `#` 字符指定 HTML 标题。 
  `#` 字符数量对应于标题的层次结构级别（例如，`#` = `<h1>` 和 `###` = ```<h3>```）。
* **编号列表：**若要制作编号（排序）列表，行应以 `1. ` 开始。  
  若要在单个列表元素中包含多个元素，请按如下所示设置列表格式：
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
获取此输出：

1.  对于第一个元素（如本例所示），在 1 后插入一个制表位。 

    若要包括第二个元素（如本例所示），请在第一个元素后插入一个换行符，并对齐缩进。

* **项目符号列表：**除 `1. ` 替换为 `* `、`- ` 或 `+ ` 外，项目符号（未排序）列表与排序列表基本相同。 多元素列表与排序列表工作方式相同。
* **链接：**超链接的语法是 `[visible link text](link URL)`。
* **同一 docset 中另一主题的链接：**docset 是此存储库中的顶级文件夹（例如，“dsc”和“scripting”）。
    同一 docset 中主题超链接的语法是 `[topic title](relative path to topic)`。 
    有关详细信息，请参阅 [README 中的相对链接](https://help.github.com/articles/relative-links-in-readmes/)。 
    若要链接到不同的顶级文件夹中的主题，请使用发布页上的 URL，如上文所述。
