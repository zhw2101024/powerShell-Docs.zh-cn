---
title: 如何创建格式设置文件 (。 format.ps1xml) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862963"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="a812b-102">如何创建格式设置文件 (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="a812b-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="a812b-103">本主题介绍如何创建格式设置文件 (。 format.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="a812b-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="a812b-104">此外可以通过创建一个 Windows powershell 提供的文件的副本创建格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="a812b-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="a812b-105">如果创建的现有文件的副本，删除现有的数字签名，并将您自己的签名添加到新文件。</span><span class="sxs-lookup"><span data-stu-id="a812b-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="a812b-106">若要创建。 format.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="a812b-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="a812b-107">创建文本文件 (.txt) 使用文本编辑器 （如记事本）。</span><span class="sxs-lookup"><span data-stu-id="a812b-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="a812b-108">将以下行复制到格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="a812b-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="a812b-109">\<配置 >\</Configuration > 标记定义根`Configuration`节点。</span><span class="sxs-lookup"><span data-stu-id="a812b-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="a812b-110">所有其他 XML 标记将包含在此节点内。</span><span class="sxs-lookup"><span data-stu-id="a812b-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="a812b-111"><ViewDefinitions> </ViewDefinitions>标记定义`ViewDefinitions`节点。</span><span class="sxs-lookup"><span data-stu-id="a812b-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="a812b-112">此节点中定义的所有视图。</span><span class="sxs-lookup"><span data-stu-id="a812b-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="a812b-113">将文件保存到 Windows PowerShell 安装文件夹、 您的模块文件夹，或模块文件夹的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="a812b-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="a812b-114">保存文件时使用以下名称格式： `MyFile.format.ps1xml`。</span><span class="sxs-lookup"><span data-stu-id="a812b-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="a812b-115">必须使用格式设置文件`.format.ps1xml`扩展。</span><span class="sxs-lookup"><span data-stu-id="a812b-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="a812b-116">现在你现可将视图添加到的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="a812b-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="a812b-117">可在格式设置文件中定义的视图数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="a812b-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="a812b-118">您可以添加每个对象、 多个视图的同一个对象或由多个对象的单个视图的单一视图。</span><span class="sxs-lookup"><span data-stu-id="a812b-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a812b-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a812b-119">See Also</span></span>

[<span data-ttu-id="a812b-120">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="a812b-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
