---
title: 如何创建 Cmdlet 帮助文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 186a8ceecea47564503dc181a76cc314033b6d3f
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996030"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="e31bf-102">如何创建 Cmdlet 帮助文件</span><span class="sxs-lookup"><span data-stu-id="e31bf-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="e31bf-103">本部分介绍如何创建包含 Windows PowerShell cmdlet 帮助主题内容的有效 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e31bf-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="e31bf-104">本部分讨论如何命名帮助文件，如何添加相应的 XML 标头，以及如何添加将包含 cmdlet 帮助内容的不同部分的节点。</span><span class="sxs-lookup"><span data-stu-id="e31bf-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="e31bf-105">若要获取帮助文件的完整视图，请打开位于 Windows PowerShell 安装目录中的 dll-Help 文件之一。</span><span class="sxs-lookup"><span data-stu-id="e31bf-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="e31bf-106">例如，dll-Help 文件包含多个 Windows PowerShell cmdlet 的内容，则不会。</span><span class="sxs-lookup"><span data-stu-id="e31bf-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="e31bf-107">如何创建 Cmdlet 帮助文件</span><span class="sxs-lookup"><span data-stu-id="e31bf-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="e31bf-108">创建一个文本文件，并使用 UTF8 编码保存该文件。</span><span class="sxs-lookup"><span data-stu-id="e31bf-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="e31bf-109">文件名必须具有以下格式，以便 Windows PowerShell 可以将其作为 cmdlet 帮助文件进行检测。</span><span class="sxs-lookup"><span data-stu-id="e31bf-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="e31bf-110">将以下 XML 标头添加到文本文件。</span><span class="sxs-lookup"><span data-stu-id="e31bf-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="e31bf-111">请注意，将根据多代理建模语言（MAML）架构对文件进行验证。</span><span class="sxs-lookup"><span data-stu-id="e31bf-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="e31bf-112">目前，Windows PowerShell 不提供任何工具来验证该文件。</span><span class="sxs-lookup"><span data-stu-id="e31bf-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="e31bf-113">将命令节点添加到程序集中每个 cmdlet 的 cmdlet 帮助文件。</span><span class="sxs-lookup"><span data-stu-id="e31bf-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="e31bf-114">命令节点内的每个节点都与 cmdlet 帮助主题的不同部分相关。</span><span class="sxs-lookup"><span data-stu-id="e31bf-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="e31bf-115">下表列出了每个节点的 XML 元素，后跟每个节点的说明。</span><span class="sxs-lookup"><span data-stu-id="e31bf-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="e31bf-116">节点</span><span class="sxs-lookup"><span data-stu-id="e31bf-116">Node</span></span>|<span data-ttu-id="e31bf-117">Description</span><span class="sxs-lookup"><span data-stu-id="e31bf-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="e31bf-118">为 cmdlet 帮助主题的名称和摘要部分添加内容。</span><span class="sxs-lookup"><span data-stu-id="e31bf-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-119">有关详细信息，请参阅[如何添加 Cmdlet 名称和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="e31bf-120">添加 cmdlet 帮助主题的 "描述" 部分的内容。</span><span class="sxs-lookup"><span data-stu-id="e31bf-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-121">有关详细信息，请参阅[如何将详细描述添加到 Cmdlet 的帮助主题](./how-to-add-a-cmdlet-description.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="e31bf-122">为 cmdlet 帮助主题的语法部分添加内容。</span><span class="sxs-lookup"><span data-stu-id="e31bf-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-123">有关详细信息，请参阅[如何将语法添加到 Cmdlet 的帮助主题](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="e31bf-124">添加 cmdlet 帮助主题的参数部分的内容。</span><span class="sxs-lookup"><span data-stu-id="e31bf-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-125">有关详细信息，请参阅[如何将参数添加到 Cmdlet 的帮助主题](./how-to-add-parameter-information.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="e31bf-126">添加 cmdlet 帮助主题的 "输入" 部分的内容。</span><span class="sxs-lookup"><span data-stu-id="e31bf-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-127">有关详细信息，请参阅[如何将输入类型添加到 Cmdlet 的帮助主题](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="e31bf-128">添加 cmdlet 帮助主题的 "输出" 部分的内容。</span><span class="sxs-lookup"><span data-stu-id="e31bf-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-129">有关详细信息，请参阅[如何将返回值添加到 Cmdlet 的帮助主题](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="e31bf-130">将内容添加到 cmdlet 帮助主题的 "注释" 部分。</span><span class="sxs-lookup"><span data-stu-id="e31bf-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-131">有关详细信息，请参阅[如何向 Cmdlet 帮助主题添加注释](./how-to-add-notes-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="e31bf-132">添加 cmdlet 帮助主题的 "示例" 部分的内容。</span><span class="sxs-lookup"><span data-stu-id="e31bf-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-133">有关详细信息，请参阅[如何将示例添加到 Cmdlet 的帮助主题](./how-to-add-examples-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="e31bf-134">添加 cmdlet 帮助主题的 "相关链接" 部分的内容。</span><span class="sxs-lookup"><span data-stu-id="e31bf-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e31bf-135">有关详细信息，请参阅[如何将相关链接添加到 Cmdlet 的帮助主题](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="e31bf-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="e31bf-136">示例</span><span class="sxs-lookup"><span data-stu-id="e31bf-136">Example</span></span>

 <span data-ttu-id="e31bf-137">下面是一个命令节点示例，其中包含 cmdlet 帮助主题各个部分的节点。</span><span class="sxs-lookup"><span data-stu-id="e31bf-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="https://schemas.microsoft.com/maml/2004/10"
  xmlns:command="https://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="https://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="e31bf-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e31bf-138">See Also</span></span>

 [<span data-ttu-id="e31bf-139">如何添加 Cmdlet 名称和摘要</span><span class="sxs-lookup"><span data-stu-id="e31bf-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e31bf-140">如何将详细描述添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="e31bf-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="e31bf-141">如何将语法添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="e31bf-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e31bf-142">如何将参数添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="e31bf-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="e31bf-143">如何将输入类型添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="e31bf-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e31bf-144">如何将返回值添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="e31bf-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e31bf-145">如何向 Cmdlet 帮助主题添加注释</span><span class="sxs-lookup"><span data-stu-id="e31bf-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e31bf-146">如何将示例添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="e31bf-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e31bf-147">如何将相关链接添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="e31bf-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e31bf-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e31bf-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)