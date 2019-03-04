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
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="e1891-102">如何向提供程序帮助主题添加“另请参阅”部分</span><span class="sxs-lookup"><span data-stu-id="e1891-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="e1891-103">本部分介绍了如何填充**另请参阅**提供程序帮助主题的部分。</span><span class="sxs-lookup"><span data-stu-id="e1891-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="e1891-104">**另请参阅**部分包含的主题相关的提供程序或可能会帮助用户更好地了解和使用的提供程序的列表。</span><span class="sxs-lookup"><span data-stu-id="e1891-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="e1891-105">主题列表可以包含 cmdlet 的帮助，提供程序帮助和概念 （"关于"） 在 Windows PowerShell 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="e1891-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="e1891-106">它还可以包含对书籍、 白皮书和联机主题，包括当前提供程序帮助主题的联机版本的引用。</span><span class="sxs-lookup"><span data-stu-id="e1891-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="e1891-107">如果是指联机主题，提供 URI 或以纯文本形式的搜索词。</span><span class="sxs-lookup"><span data-stu-id="e1891-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="e1891-108">`Get-Help` Cmdlet 不会链接或重定向到任何列表中的主题。</span><span class="sxs-lookup"><span data-stu-id="e1891-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="e1891-109">此外，`Online`参数的`Get-Help`cmdlet 提供程序的帮助下无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="e1891-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="e1891-110">另请参阅部分创建从`RelatedLinks`元素和它所包含的标记。</span><span class="sxs-lookup"><span data-stu-id="e1891-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="e1891-111">下面的 XML 演示如何将标记添加。</span><span class="sxs-lookup"><span data-stu-id="e1891-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="e1891-112">若要添加"另请参阅"主题</span><span class="sxs-lookup"><span data-stu-id="e1891-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="e1891-113">在中*AssemblyName*.dll help.xml 文件内,`providerHelp`元素中，添加`RelatedLinks`元素。</span><span class="sxs-lookup"><span data-stu-id="e1891-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="e1891-114">`RelatedLinks`元素中的最后一个元素应`providerHelp`元素。</span><span class="sxs-lookup"><span data-stu-id="e1891-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="e1891-115">只有一个`RelatedLinks`元素允许在每个提供程序帮助主题。</span><span class="sxs-lookup"><span data-stu-id="e1891-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="e1891-116">例如：</span><span class="sxs-lookup"><span data-stu-id="e1891-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="e1891-117">中的每个主题**另请参见**部分中，在`RelatedLinks`元素中，添加`navigationLink`元素。</span><span class="sxs-lookup"><span data-stu-id="e1891-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="e1891-118">然后，在每个`navigationLink`元素中，添加一个`linkText`元素和一个`uri`元素。</span><span class="sxs-lookup"><span data-stu-id="e1891-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="e1891-119">如果不使用`uri`元素中，您可以将其添加为一个空元素 (\<uri / >)。</span><span class="sxs-lookup"><span data-stu-id="e1891-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="e1891-120">例如：</span><span class="sxs-lookup"><span data-stu-id="e1891-120">For example:</span></span>

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

3. <span data-ttu-id="e1891-121">键入主题名称之间`linkText`标记。</span><span class="sxs-lookup"><span data-stu-id="e1891-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="e1891-122">如果你要提供一个 URI，请键入该之间`uri`标记。</span><span class="sxs-lookup"><span data-stu-id="e1891-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="e1891-123">若要指示当前提供程序帮助主题的联机版本之间`linkText`标记中，键入"联机版本:"而不是主题名称。</span><span class="sxs-lookup"><span data-stu-id="e1891-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="e1891-124">通常情况下，"联机版本:"链接是另请参阅主题列表中的第一个主题。</span><span class="sxs-lookup"><span data-stu-id="e1891-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="e1891-125">下面的示例包括三个另请参阅主题。</span><span class="sxs-lookup"><span data-stu-id="e1891-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="e1891-126">第一个引用当前主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="e1891-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="e1891-127">第二个是指 Windows PowerShell cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="e1891-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="e1891-128">第三个引用另一个联机主题。</span><span class="sxs-lookup"><span data-stu-id="e1891-128">The third refers to another online topic.</span></span>

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