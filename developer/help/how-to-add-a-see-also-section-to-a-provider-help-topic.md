---
title: 如何，请参阅还将节添加到提供程序帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858343"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>如何向提供程序帮助主题添加“另请参阅”部分

本部分介绍了如何填充**另请参阅**提供程序帮助主题的部分。

**另请参阅**部分包含的主题相关的提供程序或可能会帮助用户更好地了解和使用的提供程序的列表。 主题列表可以包含 cmdlet 的帮助，提供程序帮助和概念 （"关于"） 在 Windows PowerShell 的帮助主题。 它还可以包含对书籍、 白皮书和联机主题，包括当前提供程序帮助主题的联机版本的引用。

如果是指联机主题，提供 URI 或以纯文本形式的搜索词。 `Get-Help` Cmdlet 不会链接或重定向到任何列表中的主题。 此外，`Online`参数的`Get-Help`cmdlet 提供程序的帮助下无法正常工作。

另请参阅部分创建从`RelatedLinks`元素和它所包含的标记。 下面的 XML 演示如何将标记添加。

### <a name="to-add-see-also-topics"></a>若要添加"另请参阅"主题

1. 在中*AssemblyName*.dll help.xml 文件内,`providerHelp`元素中，添加`RelatedLinks`元素。 `RelatedLinks`元素中的最后一个元素应`providerHelp`元素。 只有一个`RelatedLinks`元素允许在每个提供程序帮助主题。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. 中的每个主题**另请参见**部分中，在`RelatedLinks`元素中，添加`navigationLink`元素。 然后，在每个`navigationLink`元素中，添加一个`linkText`元素和一个`uri`元素。 如果不使用`uri`元素中，您可以将其添加为一个空元素 (\<uri / >)。

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

3. 键入主题名称之间`linkText`标记。 如果你要提供一个 URI，请键入该之间`uri`标记。 若要指示当前提供程序帮助主题的联机版本之间`linkText`标记中，键入"联机版本:"而不是主题名称。 通常情况下，"联机版本:"链接是另请参阅主题列表中的第一个主题。

   下面的示例包括三个另请参阅主题。 第一个引用当前主题的联机版本。 第二个是指 Windows PowerShell cmdlet 帮助主题。 第三个引用另一个联机主题。

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