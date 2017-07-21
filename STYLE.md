# <a name="style-guide-for-powershell-docs"></a><span data-ttu-id="df5cd-101">PowerShell 文档的风格指南</span><span class="sxs-lookup"><span data-stu-id="df5cd-101">Style guide for PowerShell-Docs</span></span>


## <a name="titlesheadings"></a><span data-ttu-id="df5cd-102">标题</span><span class="sxs-lookup"><span data-stu-id="df5cd-102">Titles/Headings</span></span>

* <span data-ttu-id="df5cd-103">标题（由 \# 预先设定的任何内容））后应换行</span><span class="sxs-lookup"><span data-stu-id="df5cd-103">Titles/headings (anything preprended by \#) should be followed with a newline</span></span>
* <span data-ttu-id="df5cd-104">仅大写标题的第一个字母和该标题中的全部专有名词</span><span class="sxs-lookup"><span data-stu-id="df5cd-104">Only the first letter of a title and any proper nouns in that title should be capitalized</span></span>
* <span data-ttu-id="df5cd-105">每个文档只有 1 个 H1</span><span class="sxs-lookup"><span data-stu-id="df5cd-105">Only 1 H1 per document</span></span>
* <span data-ttu-id="df5cd-106">编辑参考内容时，H2 由 PlatyPUS 规定，不能进行添加或删除，否则将导致构建中断</span><span class="sxs-lookup"><span data-stu-id="df5cd-106">When editing reference content, the H2s are prescribed by platyPS and should not be added or removed as it will cause a build break</span></span>
* <span data-ttu-id="df5cd-107">只使用 \# 样式标题（而不是 = 或 \- 样式标题）</span><span class="sxs-lookup"><span data-stu-id="df5cd-107">Only use \# style headers (as opposed to = or \- style headers)</span></span>

### <a name="correct"></a><span data-ttu-id="df5cd-108">正确</span><span class="sxs-lookup"><span data-stu-id="df5cd-108">Correct</span></span>

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a><span data-ttu-id="df5cd-109">不正确</span><span class="sxs-lookup"><span data-stu-id="df5cd-109">Incorrect</span></span>

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a><span data-ttu-id="df5cd-110">语法</span><span class="sxs-lookup"><span data-stu-id="df5cd-110">Syntax</span></span>

* <span data-ttu-id="df5cd-111">当谈到段落中的一个 cmdlet 时，使用 \\` 突出显示 cmdlet 名称</span><span class="sxs-lookup"><span data-stu-id="df5cd-111">When talking about a cmdlet in paragraph, use \\` to highlight cmdlet names</span></span>
  * <span data-ttu-id="df5cd-112">正确示例：此 `Write-Host` Cmdlet 可以...</span><span class="sxs-lookup"><span data-stu-id="df5cd-112">Correct Example: This `Write-Host` Cmdlet can ...</span></span>
  * <span data-ttu-id="df5cd-113">错误示例：此 Write-host Cmdlet 可以...并通过管道传递到 out-file Cmdlet 以...</span><span class="sxs-lookup"><span data-stu-id="df5cd-113">Incorrect Example: This **Write-Host** Cmdlet can ... and pipeline to out-file Cmdlet to ...</span></span>
* <span data-ttu-id="df5cd-114">在撰写文章（而不是参考内容）时，cmdlet 名称的第一个实例应该是指向 cmdlet 文档的链接</span><span class="sxs-lookup"><span data-stu-id="df5cd-114">When writing an article (as opposed to reference content), the first instance of a cmdlet name should be a link to the cmdlet documentation</span></span>
* <span data-ttu-id="df5cd-115">所有 PowerShell 语法块都应使用 ``\`powershell</span><span class="sxs-lookup"><span data-stu-id="df5cd-115">All PowerShell syntax blocks should use &#96;&#96;&#96;powershell</span></span>
* <span data-ttu-id="df5cd-116">不要让 PowerShell 命令以“`PS C:\>`”为开头</span><span class="sxs-lookup"><span data-stu-id="df5cd-116">Do not start PowerShell commands with "`PS C:\>`"</span></span>
  * <span data-ttu-id="df5cd-117">正确示例：</span><span class="sxs-lookup"><span data-stu-id="df5cd-117">Correct Example:</span></span>
  ```powershell
  Get-Process
  ```
  * <span data-ttu-id="df5cd-118">错误示例：</span><span class="sxs-lookup"><span data-stu-id="df5cd-118">Incorrect Example:</span></span>
  ```powershell
  PS C:\> Get-Process
  ```
* <span data-ttu-id="df5cd-119">应对 PowerShell 命令发出的输出进行注释，以防止它接收突出显示的语法</span><span class="sxs-lookup"><span data-stu-id="df5cd-119">Output emitted by PowerShell commands should be commented to prevent it from recieving syntax highlighting</span></span>
* <span data-ttu-id="df5cd-120">属性名称和参数名称应为**粗体**样式</span><span class="sxs-lookup"><span data-stu-id="df5cd-120">Property names and parameter names should be in **bold**</span></span>
* <span data-ttu-id="df5cd-121">PowerShell cmdlet 采用[帕斯卡命名法](https://en.wikipedia.org/wiki/PascalCase)。</span><span class="sxs-lookup"><span data-stu-id="df5cd-121">PowerShell cmdlets are "[Pascal Cased](https://en.wikipedia.org/wiki/PascalCase)".</span></span> <span data-ttu-id="df5cd-122">谓词与名词通过连字符分隔开来。</span><span class="sxs-lookup"><span data-stu-id="df5cd-122">Verbs are seperated from nouns by a hyphen.</span></span>

## <a name="lists"></a><span data-ttu-id="df5cd-123">列表</span><span class="sxs-lookup"><span data-stu-id="df5cd-123">Lists</span></span>

* <span data-ttu-id="df5cd-124">不要使用句点结束列表项（除非它们包含多个句子）</span><span class="sxs-lookup"><span data-stu-id="df5cd-124">Do not end list items with a period (unless they contain multiple sentences)</span></span>
* <span data-ttu-id="df5cd-125">如果你的列表包含多个句子，请考虑在主要设想下使用标题 3/4/5（如果适用）</span><span class="sxs-lookup"><span data-stu-id="df5cd-125">If your list contains multiple sentences, consider using a header 3/4/5 (as applicable) underneath your primary idea</span></span>

## <a name="links"></a><span data-ttu-id="df5cd-126">链接</span><span class="sxs-lookup"><span data-stu-id="df5cd-126">Links</span></span>

* <span data-ttu-id="df5cd-127">始终使用 MarkDown 语法 `[friendlyname](url)` 标记链接</span><span class="sxs-lookup"><span data-stu-id="df5cd-127">Links are always marked up using MarkDown syntax `[friendlyname](url)`</span></span>
* <span data-ttu-id="df5cd-128">链接应具有友好名称（如适用），最有可能是链接页面的标题</span><span class="sxs-lookup"><span data-stu-id="df5cd-128">Links should have a a friendly name when applicable, most likely the title of the linked page</span></span>
  * <span data-ttu-id="df5cd-129">**例外情况**：指向非 Microsoft 网站的链接只能具有 URL</span><span class="sxs-lookup"><span data-stu-id="df5cd-129">**Exception**: Links going towards non-Microsoft sites should only have a URL</span></span>
* <span data-ttu-id="df5cd-130">底部“相关链接”部分中的所有项都应具有超链接。</span><span class="sxs-lookup"><span data-stu-id="df5cd-130">All items in the "related links" section at the bottom should be hyperlinked.</span></span> 

## <a name="line-breaks"></a><span data-ttu-id="df5cd-131">换行符</span><span class="sxs-lookup"><span data-stu-id="df5cd-131">Line breaks</span></span>

* <span data-ttu-id="df5cd-132">必须包括语义换行符</span><span class="sxs-lookup"><span data-stu-id="df5cd-132">You must include semantic line breaks</span></span>
* <span data-ttu-id="df5cd-133">应将行限制为 100 个字符（打开项目：可帮助我们验证此限制的工具）</span><span class="sxs-lookup"><span data-stu-id="df5cd-133">You should limit lines to 100char (Open item: tooling to help us validate this)</span></span>
* <span data-ttu-id="df5cd-134">你可以删除 PS4+、非 ps3（需要验证）的其他换行符</span><span class="sxs-lookup"><span data-stu-id="df5cd-134">You CAN remove additional line breaks for PS4+, NOT ps3 (needs validation)</span></span>
