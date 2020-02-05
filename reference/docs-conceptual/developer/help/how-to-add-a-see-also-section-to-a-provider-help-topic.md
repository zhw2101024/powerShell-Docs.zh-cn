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
ms.openlocfilehash: 1c1b7f4cf56ea2f9e30438a60e7bee29d87b80ba
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995956"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="2fa31-102">如何向提供程序帮助主题添加“另请参阅”部分</span><span class="sxs-lookup"><span data-stu-id="2fa31-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="2fa31-103">本部分介绍如何填充提供程序帮助主题的 "**另请参阅**" 部分。</span><span class="sxs-lookup"><span data-stu-id="2fa31-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="2fa31-104">"**另请参阅**" 部分包含与提供程序相关的主题列表，或可帮助用户更好地了解和使用该提供程序。</span><span class="sxs-lookup"><span data-stu-id="2fa31-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="2fa31-105">主题列表可以包含 Windows PowerShell 中的 cmdlet 帮助、提供程序帮助和概念（"关于"）帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2fa31-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="2fa31-106">它还可以包括对书籍、纸张和联机主题的引用，包括当前提供程序帮助主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="2fa31-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="2fa31-107">请参阅联机主题，以纯文本形式提供 URI 或搜索词。</span><span class="sxs-lookup"><span data-stu-id="2fa31-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="2fa31-108">`Get-Help` cmdlet 不会链接或重定向到列表中的任何主题。</span><span class="sxs-lookup"><span data-stu-id="2fa31-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="2fa31-109">此外，`Get-Help` cmdlet 的 `Online` 参数不与提供程序帮助一起使用。</span><span class="sxs-lookup"><span data-stu-id="2fa31-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="2fa31-110">"另请参阅" 部分从 `RelatedLinks` 元素及其包含的标记创建。</span><span class="sxs-lookup"><span data-stu-id="2fa31-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="2fa31-111">下面的 XML 演示如何添加标记。</span><span class="sxs-lookup"><span data-stu-id="2fa31-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="2fa31-112">添加 "另请参阅" 主题</span><span class="sxs-lookup"><span data-stu-id="2fa31-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="2fa31-113">在 dll-help 文件*中的 `providerHelp`* 元素中，添加 `RelatedLinks` 元素。</span><span class="sxs-lookup"><span data-stu-id="2fa31-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="2fa31-114">`RelatedLinks` 元素应为 `providerHelp` 元素中的最后一个元素。</span><span class="sxs-lookup"><span data-stu-id="2fa31-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="2fa31-115">每个提供程序帮助主题中只允许有一个 `RelatedLinks` 元素。</span><span class="sxs-lookup"><span data-stu-id="2fa31-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="2fa31-116">例如：</span><span class="sxs-lookup"><span data-stu-id="2fa31-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="2fa31-117">对于 "**另请参见**" 部分中的每个主题，在 `RelatedLinks` 元素中添加 `navigationLink` 元素。</span><span class="sxs-lookup"><span data-stu-id="2fa31-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="2fa31-118">然后，在每个 `navigationLink` 元素中，添加一个 `linkText` 元素和一个 `uri` 元素。</span><span class="sxs-lookup"><span data-stu-id="2fa31-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="2fa31-119">如果使用的不是 `uri` 元素，则可以将其添加为空元素（\<uri/>）。</span><span class="sxs-lookup"><span data-stu-id="2fa31-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="2fa31-120">例如：</span><span class="sxs-lookup"><span data-stu-id="2fa31-120">For example:</span></span>

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

3. <span data-ttu-id="2fa31-121">在 `linkText` 标记之间键入主题名称。</span><span class="sxs-lookup"><span data-stu-id="2fa31-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="2fa31-122">如果提供了 URI，请在 `uri` 标记之间键入。</span><span class="sxs-lookup"><span data-stu-id="2fa31-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="2fa31-123">若要指示当前提供程序帮助主题的联机版本，请在 `linkText` 标记之间键入 "Online version："，而不是主题名称。</span><span class="sxs-lookup"><span data-stu-id="2fa31-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="2fa31-124">通常，"Online 版本：" 链接是 "另请参见" 主题列表中的第一个主题。</span><span class="sxs-lookup"><span data-stu-id="2fa31-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="2fa31-125">下面的示例包括三个 "另请参阅" 主题。</span><span class="sxs-lookup"><span data-stu-id="2fa31-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="2fa31-126">第一个引用当前主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="2fa31-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="2fa31-127">第二个引用 Windows PowerShell cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2fa31-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="2fa31-128">第三个引用其他联机主题。</span><span class="sxs-lookup"><span data-stu-id="2fa31-128">The third refers to another online topic.</span></span>

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```