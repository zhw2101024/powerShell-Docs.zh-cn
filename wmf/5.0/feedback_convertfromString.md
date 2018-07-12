---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892340"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>提取和分析字符串外的结构化对象

这也为 `ConvertFrom-String` cmdlet 引入了一些附加功能：

- 默认情况下删除盘区文本属性。 可以将其包含于 -IncludeExtent 参数中。

- 来自 MVP 和社区反馈的许多学习算法 Bug 修复。

- 新 -UpdateTemplate 参数，用于将学习算法的结果保存到模板文件中的注释内。 这使得学习过程（速度最慢的阶段）成为一次性完成的过程。 使用包含已编码学习算法的模板来运行 Convert-String 现为近即时行为。

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>从字符串内容中提取并分析结构化对象

与 [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F) 协作添加了一个新的 `ConvertFrom-String` cmdlet。

此 cmdlet 支持两种模式：基本分隔分析和自动生成的示例驱动的分析。

默认情况下，分隔分析会在空格处将输入拆分，并为得到的组分配属性名称。 你可以自定义分隔符：

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

该 cmdlet 还支持[Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F) 的 [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) 研究工作的自动生成的示例驱动的分析。

首先，请考虑基于文本的通讯簿：

```
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
```

将几个示例复制到一个文件，将该文件用作模板：

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

为你想要提取的数据添加大括号，同时为其命名。 由于 **Name** 属性（及其关联的其他属性）可能多次出现，因此请使用星号 (\*) 来表示这会导致出现多个记录（而不是将多个属性提取到单个记录中）：

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

由这组示例可知，`ConvertFrom-String` 现在可以从具有类似结构的输入文件中自动提取基于对象的输出。

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

为了对提取的文本进行其他数据操作，则 **ExtentText** 属性将捕获从中提取记录的原始文本。 若要对于此功能给出反馈，或告诉我们无法为其编写示例的内容，请发送电子邮件至 <psdmfb@microsoft.com>。