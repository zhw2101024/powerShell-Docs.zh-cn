---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 3413672e73705252225300a853c10a514500baa2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="24123-102">提取和分析字符串外的结构化对象</span><span class="sxs-lookup"><span data-stu-id="24123-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="24123-103">这也为 ConvertFrom-String cmdlet 引入了一些附加功能：</span><span class="sxs-lookup"><span data-stu-id="24123-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="24123-104">默认情况下删除盘区文本属性。</span><span class="sxs-lookup"><span data-stu-id="24123-104">Removes the extent text property by default.</span></span> <span data-ttu-id="24123-105">可以将其包含于 -IncludeExtent 参数中。</span><span class="sxs-lookup"><span data-stu-id="24123-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="24123-106">来自 MVP 和社区反馈的许多学习算法 Bug 修复。</span><span class="sxs-lookup"><span data-stu-id="24123-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="24123-107">新 -UpdateTemplate 参数，用于将学习算法的结果保存到模板文件中的注释内。</span><span class="sxs-lookup"><span data-stu-id="24123-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="24123-108">这使得学习过程（速度最慢的阶段）成为一次性完成的过程。</span><span class="sxs-lookup"><span data-stu-id="24123-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="24123-109">使用包含已编码学习算法的模板来运行 Convert-String 现为近即时行为。</span><span class="sxs-lookup"><span data-stu-id="24123-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="24123-110">从字符串内容中提取并分析结构化对象</span><span class="sxs-lookup"><span data-stu-id="24123-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="24123-111">与 [Microsoft Research](http://research.microsoft.com/) 协作添加了一个新的 **ConvertFrom-String** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="24123-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="24123-112">此 cmdlet 支持两种模式：基本分隔分析和自动生成的示例驱动的分析。</span><span class="sxs-lookup"><span data-stu-id="24123-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="24123-113">默认情况下，分隔分析会在空格处将输入拆分，并为得到的组分配属性名称。</span><span class="sxs-lookup"><span data-stu-id="24123-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="24123-114">你可以自定义分隔符：</span><span class="sxs-lookup"><span data-stu-id="24123-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="24123-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="24123-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="24123-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="24123-116">P1    P2</span></span>
--    --

<span data-ttu-id="24123-117">该 cmdlet 还支持[Microsoft Research](http://research.microsoft.com) 的 [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) 研究工作的自动生成的示例驱动的分析。</span><span class="sxs-lookup"><span data-stu-id="24123-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="24123-118">首先，请考虑基于文本的通讯簿：</span><span class="sxs-lookup"><span data-stu-id="24123-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="24123-119">将几个示例复制到一个文件，将该文件用作模板：</span><span class="sxs-lookup"><span data-stu-id="24123-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

   

<span data-ttu-id="24123-120">为你想要提取的数据添加大括号，同时为其命名。</span><span class="sxs-lookup"><span data-stu-id="24123-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="24123-121">由于 **Name** 属性（及其关联的其他属性）可能多次出现，因此请使用星号 (\*) 来表示这会导致出现多个记录（而不是将多个属性提取到单个记录中）：</span><span class="sxs-lookup"><span data-stu-id="24123-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="24123-122">由这组示例可知，**ConvertFrom-String** 现在可以从具有类似结构的输入文件中自动提取基于对象的输出。</span><span class="sxs-lookup"><span data-stu-id="24123-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="24123-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="24123-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="24123-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="24123-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="24123-125">ExtentText                     姓名               城市     州</span><span class="sxs-lookup"><span data-stu-id="24123-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="24123-126">Ana Trujillo...              Ana Trujillo       雷德蒙市  华盛顿州 Antonio Moreno...            Antonio Moreno     兰顿市   华盛顿州 Thomas Hardy...              Thomas Hardy       西雅图  华盛顿州 Christina Berglund...        Christina Berglund 雷德蒙市  华盛顿州 Hanna Moos...                Hanna Moos         皮阿拉普市 华盛顿州</span><span class="sxs-lookup"><span data-stu-id="24123-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="24123-127">为了对提取的文本进行其他数据操作，则 **ExtentText** 属性将捕获从中提取记录的原始文本。</span><span class="sxs-lookup"><span data-stu-id="24123-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="24123-128">若要提供有关此功能的反馈或共享无法为其写入示例的内容，请发送电子邮件至 <psdmfb@microsoft.com>。</span><span class="sxs-lookup"><span data-stu-id="24123-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>

