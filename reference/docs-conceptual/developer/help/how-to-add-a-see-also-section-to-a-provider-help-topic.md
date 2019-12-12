---
title: 如何向提供程序帮助主题添加 "另请参阅" 部分 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367836"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>如何向提供程序帮助主题添加“另请参阅”部分

本部分介绍如何填充提供程序帮助主题的 "**另请参阅**" 部分。

"**另请参阅**" 部分包含与提供程序相关的主题列表，或可帮助用户更好地了解和使用该提供程序。 主题列表可以包含 Windows PowerShell 中的 cmdlet 帮助、提供程序帮助和概念（"关于"）帮助主题。 它还可以包括对书籍、纸张和联机主题的引用，包括当前提供程序帮助主题的联机版本。

请参阅联机主题，以纯文本形式提供 URI 或搜索词。 `Get-Help` cmdlet 不会链接或重定向到列表中的任何主题。 此外，`Get-Help` cmdlet 的 `Online` 参数不与提供程序帮助一起使用。

"另请参阅" 部分从 `RelatedLinks` 元素及其包含的标记创建。 下面的 XML 演示如何添加标记。

### <a name="to-add-see-also-topics"></a>添加 "另请参阅" 主题

1. 在 dll-help 文件*中的 `providerHelp`* 元素中，添加 `RelatedLinks` 元素。 `RelatedLinks` 元素应为 `providerHelp` 元素中的最后一个元素。 每个提供程序帮助主题中只允许有一个 `RelatedLinks` 元素。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. 对于 "**另请参见**" 部分中的每个主题，在 `RelatedLinks` 元素中添加 `navigationLink` 元素。 然后，在每个 `navigationLink` 元素中，添加一个 `linkText` 元素和一个 `uri` 元素。 如果使用的不是 `uri` 元素，则可以将其添加为空元素（\<uri/>）。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. 在 `linkText` 标记之间键入主题名称。 如果提供了 URI，请在 `uri` 标记之间键入。 若要指示当前提供程序帮助主题的联机版本，请在 `linkText` 标记之间键入 "Online version："，而不是主题名称。 通常，"Online 版本：" 链接是 "另请参见" 主题列表中的第一个主题。

   下面的示例包括三个 "另请参阅" 主题。 第一个引用当前主题的联机版本。 第二个引用 Windows PowerShell cmdlet 帮助主题。 第三个引用其他联机主题。

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```