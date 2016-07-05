# 提取和分析字符串外的结构化对象
这也为 ConvertFrom-String cmdlet 引入了一些附加功能：

-   默认情况下删除盘区文本属性。 可以将其包含于 -IncludeExtent 参数中。

-   来自 MVP 和社区反馈的许多学习算法 Bug 修复。

-   新 -UpdateTemplate 参数，用于将学习算法的结果保存到模板文件中的注释内。 这使得学习过程（速度最慢的阶段）成为一次性完成的过程。 使用包含已编码学习算法的模板来运行 Convert-String 现为近即时行为。


从字符串内容中提取并分析结构化对象
----------------------------------------------------------

与 [Microsoft Research](http://research.microsoft.com/) 协作添加了一个新的 **ConvertFrom-String** cmdlet。

此 cmdlet 支持两种模式：基本分隔分析和自动生成的示例驱动的分析。

默认情况下，分隔分析会在空格处将输入拆分，并为得到的组分配属性名称。 你可以自定义分隔符：

> 1 \[C:\\temp\]
> &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto

P1    P2
--    --

该 cmdlet 还支持[Microsoft Research](http://research.microsoft.com) 的 [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) 研究工作的自动生成的示例驱动的分析。

首先，请考虑基于文本的通讯簿：

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

将几个示例复制到一个文件，将该文件用作模板：

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

   

为你想要提取的数据添加大括号，同时为其命名。 由于 **Name** 属性（及其关联的其他属性）可能多次出现，因此请使用星号 (\*) 来表示这会导致出现多个记录（而不是将多个属性提取到单个记录中）：

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

由这组示例可知，**ConvertFrom-String** 现在可以从具有类似结构的输入文件中自动提取基于对象的输出。

> 2 \[C:\\temp\]
>
> &gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto
>
> ExtentText                     姓名               城市     州
> ----------                     ----               ----     -----
> Ana Trujillo...              Ana Trujillo       雷德蒙市  华盛顿州 Antonio Moreno...            Antonio Moreno     兰顿市   华盛顿州 Thomas Hardy...              Thomas Hardy       西雅图  华盛顿州 Christina Berglund...        Christina Berglund 雷德蒙市  华盛顿州 Hanna Moos...                Hanna Moos         皮阿拉普市 华盛顿州

为了对提取的文本进行其他数据操作，则 **ExtentText** 属性将捕获从中提取记录的原始文本。 若要提供有关此功能的反馈或共享无法为其写入示例的内容，请发送电子邮件至 <psdmfb@microsoft.com>。



<!--HONumber=Jun16_HO4-->


