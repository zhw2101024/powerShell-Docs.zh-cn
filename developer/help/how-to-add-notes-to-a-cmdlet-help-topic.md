---
title: 如何将注释添加到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083410"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="97c89-102">如何向 Cmdlet 帮助主题添加备注</span><span class="sxs-lookup"><span data-stu-id="97c89-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="97c89-103">本部分介绍如何添加 Windows PowerShell® cmdlet 帮助主题的备注部分。</span><span class="sxs-lookup"><span data-stu-id="97c89-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="97c89-104">说明部分用于解释不适合轻松地为其他结构化部分，如参数的更详细的说明的详细信息。</span><span class="sxs-lookup"><span data-stu-id="97c89-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="97c89-105">此内容可能包括对特定的提供程序时，该 cmdlet 的工作原理、 一些唯一的但却很重要，使用的 cmdlet 或避免出现的错误情况的方法的注释。</span><span class="sxs-lookup"><span data-stu-id="97c89-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="97c89-106">时，可以将它们添加到说明部分的说明的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="97c89-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="97c89-107">对于每个说明，添加一对\<maml:alert > 标记，用于\<maml:alertset > 节点。</span><span class="sxs-lookup"><span data-stu-id="97c89-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="97c89-108">每个需要注意的内容添加一组内\<maml:para > 标记。</span><span class="sxs-lookup"><span data-stu-id="97c89-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="97c89-109">使用空白\<maml:para > 标记的间距。</span><span class="sxs-lookup"><span data-stu-id="97c89-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="97c89-110">下面的 XML 演示\<maml:alertset > 具有这两个说明节点。</span><span class="sxs-lookup"><span data-stu-id="97c89-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="97c89-111">请注意，每个注释包含一个可选\<maml:title > 标记 (标题可用于任何组的分组\<maml:alert > 标记)，并且每个说明具有一个空行间距的内容之后。</span><span class="sxs-lookup"><span data-stu-id="97c89-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



