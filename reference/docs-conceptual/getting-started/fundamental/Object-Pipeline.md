---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "对象管道"
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="object-pipeline"></a><span data-ttu-id="b971a-103">对象管道</span><span class="sxs-lookup"><span data-stu-id="b971a-103">Object Pipeline</span></span>
<span data-ttu-id="b971a-104">管道的行为就像一系列连接的管道段一样。</span><span class="sxs-lookup"><span data-stu-id="b971a-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="b971a-105">沿着管道移动的项会通过每个管道段。</span><span class="sxs-lookup"><span data-stu-id="b971a-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="b971a-106">若要在 Windows PowerShell 中创建管道，请使用管道运算符“|”将命令连接在一起。</span><span class="sxs-lookup"><span data-stu-id="b971a-106">To create a pipeline in Windows PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="b971a-107">每个命令的输出都将被用作下一命令的输入。</span><span class="sxs-lookup"><span data-stu-id="b971a-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="b971a-108">管道可能是命令行界面中使用的最有价值的概念。</span><span class="sxs-lookup"><span data-stu-id="b971a-108">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="b971a-109">正确使用管道不仅可以减少输入复杂命令的工作量，还可使查看命令中的工作流变得更加简单。</span><span class="sxs-lookup"><span data-stu-id="b971a-109">Properly used, pipelines not only reduce the effort involved in entering complex commands, but also make it easier to see the flow of work in the commands.</span></span> <span data-ttu-id="b971a-110">管道的相关有用特征是：因为它们单独对每个项进行操作，所以不需要基于你将在管道中拥有零个、一个或多个项而对其进行修改。</span><span class="sxs-lookup"><span data-stu-id="b971a-110">A related useful characteristic of pipelines is that because they operate on each item separately, you do not have to modify them based on whether you will have zero, one, or many items in the pipeline.</span></span> <span data-ttu-id="b971a-111">此外，管道中的每个命令（称为管道元素）通常将其输出逐项传递到管道中的下一个命令。</span><span class="sxs-lookup"><span data-stu-id="b971a-111">Furthermore, each command in a pipeline (called a pipeline element) usually passes its output to the next command in the pipeline item-by-item.</span></span> <span data-ttu-id="b971a-112">这通常会降低复杂命令的资源需求，可让你立即开始获取输出。</span><span class="sxs-lookup"><span data-stu-id="b971a-112">This usually reduces the resource demand of complex commands and allows you to begin getting the output immediately.</span></span>

<span data-ttu-id="b971a-113">在本章中，我们将讲述 Windows PowerShell 管道与最常用 shell 的管道的不同之处，然后介绍一些可用于控制管道输出并查看管道运作方式的基本工具。</span><span class="sxs-lookup"><span data-stu-id="b971a-113">In this chapter, we will describe how the Windows PowerShell pipeline differs from the pipelines of most popular shells, and then demonstrate some basic tools that you can use to help control pipeline output and also to see how the pipeline operates.</span></span>

