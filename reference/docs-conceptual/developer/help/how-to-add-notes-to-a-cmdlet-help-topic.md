---
title: 如何向 Cmdlet 帮助主题添加注释 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361266"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="6614b-102">如何向 Cmdlet 帮助主题添加备注</span><span class="sxs-lookup"><span data-stu-id="6614b-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="6614b-103">本部分介绍如何向 Windows PowerShell® cmdlet 帮助主题添加注释部分。</span><span class="sxs-lookup"><span data-stu-id="6614b-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="6614b-104">"注释" 部分用于解释不能轻松地加入其他结构化部分的详细信息，如更详细的参数说明。</span><span class="sxs-lookup"><span data-stu-id="6614b-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="6614b-105">此内容可能包括有关 cmdlet 如何与特定提供程序一起使用的注释、对 cmdlet 的一些独特但重要的使用，或者用于避免可能的错误情况的方法。</span><span class="sxs-lookup"><span data-stu-id="6614b-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="6614b-106">可以添加到注释部分的便笺数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="6614b-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="6614b-107">对于每个注释，请将一对 \<maml： alert > 标记添加到 \<maml： alertset > 节点。</span><span class="sxs-lookup"><span data-stu-id="6614b-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="6614b-108">每个注释的内容将添加到一组 \<maml： > 标记中。</span><span class="sxs-lookup"><span data-stu-id="6614b-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="6614b-109">使用空白 \<maml：段落 > 标记进行间距。</span><span class="sxs-lookup"><span data-stu-id="6614b-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="6614b-110">下面的 XML 显示了一个具有两个注释的 \<maml： alertset > 节点。</span><span class="sxs-lookup"><span data-stu-id="6614b-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="6614b-111">请注意，每个注释都有一个可选的 \<maml： title > 标记（标题可用于对任何一组 \<maml： alert > 标记）进行分组，并且每个注释在内容后均为空格。</span><span class="sxs-lookup"><span data-stu-id="6614b-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



