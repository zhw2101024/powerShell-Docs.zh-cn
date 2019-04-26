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
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083240"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="3f2e5-102">如何创建 Cmdlet 帮助文件</span><span class="sxs-lookup"><span data-stu-id="3f2e5-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="3f2e5-103">本部分介绍如何创建有效的 XML 文件包含 Windows PowerShell cmdlet 帮助主题的内容。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="3f2e5-104">本部分讨论如何命名的帮助文件、 如何添加适当的 XML 标头，以及如何添加将包含 cmdlet 的帮助内容的不同部分的节点。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="3f2e5-105">查看完整的帮助文件，打开一个 dll Help.xml 文件位于 Windows PowerShell 安装目录。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="3f2e5-106">例如，Microsoft.PowerShell.Commands.Management.dll Help.xml 文件包含内容的多个 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="3f2e5-107">如何创建 Cmdlet 帮助文件</span><span class="sxs-lookup"><span data-stu-id="3f2e5-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="3f2e5-108">创建一个文本文件并保存使用 UTF8 编码。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="3f2e5-109">文件名称必须具有以下格式，以便 Windows PowerShell 可以将其检测为 cmdlet 帮助文件。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="3f2e5-110">将以下 XML 标头添加到文本文件。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="3f2e5-111">请注意，将根据多个代理建模语言 （maml） 进行架构验证该文件。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="3f2e5-112">目前，Windows PowerShell 不提供任何工具来验证文件。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="3f2e5-113">将命令节点添加到程序集中的每个 cmdlet 的 cmdlet 帮助文件。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="3f2e5-114">命令节点中的每个节点与相关的 cmdlet 帮助主题的不同部分。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="3f2e5-115">下表列出了每个节点后, 跟每个节点的说明的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="3f2e5-116">节点</span><span class="sxs-lookup"><span data-stu-id="3f2e5-116">Node</span></span>|<span data-ttu-id="3f2e5-117">说明</span><span class="sxs-lookup"><span data-stu-id="3f2e5-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="3f2e5-118">添加的名称和摘要部分的 cmdlet 帮助主题的内容。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-119">有关详细信息，请参阅[How to Add 的 Cmdlet 名称和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="3f2e5-120">添加的 cmdlet 帮助主题的描述部分的内容。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-121">有关详细信息，请参阅[如何添加到 Cmdlet 的帮助主题的详细说明](./how-to-add-a-cmdlet-description.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="3f2e5-122">添加的 cmdlet 帮助主题语法部分的内容。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-123">有关详细信息，请参阅[如何添加语法为 Cmdlet 帮助主题](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="3f2e5-124">添加的 cmdlet 帮助主题的 PARAMETERS 节的内容。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-125">有关详细信息，请参阅[如何添加参数向 Cmdlet 帮助主题](./how-to-add-parameter-information.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="3f2e5-126">添加的 cmdlet 帮助主题的输入部分的内容。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-127">有关详细信息，请参阅[如何将输入类型添加到 Cmdlet 帮助主题](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="3f2e5-128">添加内容的输出部分的 cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-129">有关详细信息，请参阅[如何添加返回的值为 Cmdlet 帮助主题](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="3f2e5-130">将内容添加到 cmdlet 帮助主题的说明部分。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-131">有关详细信息，请参阅[How to add 说明 Cmdlet 帮助主题到](./how-to-add-notes-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="3f2e5-132">添加的 cmdlet 帮助主题的示例部分的内容。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-133">有关详细信息，请参阅[示例添加到 Cmdlet 帮助主题如何](./how-to-add-examples-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="3f2e5-134">添加内容的相关链接部分的 cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3f2e5-135">有关详细信息，请参阅[如何添加相关链接到 Cmdlet 帮助主题](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="3f2e5-136">示例</span><span class="sxs-lookup"><span data-stu-id="3f2e5-136">Example</span></span>

 <span data-ttu-id="3f2e5-137">下面是命令节点，包括 cmdlet 帮助主题的各个部分的节点的示例。</span><span class="sxs-lookup"><span data-stu-id="3f2e5-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
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

## <a name="see-also"></a><span data-ttu-id="3f2e5-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f2e5-138">See Also</span></span>

 [<span data-ttu-id="3f2e5-139">如何添加的 Cmdlet 名称和摘要</span><span class="sxs-lookup"><span data-stu-id="3f2e5-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f2e5-140">如何将详细的说明添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="3f2e5-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="3f2e5-141">如何将语法添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="3f2e5-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f2e5-142">如何将参数添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="3f2e5-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="3f2e5-143">如何将输入的类型添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="3f2e5-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f2e5-144">如何将返回值添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="3f2e5-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f2e5-145">如何添加说明到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="3f2e5-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f2e5-146">如何添加到 Cmdlet 帮助主题的示例</span><span class="sxs-lookup"><span data-stu-id="3f2e5-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f2e5-147">如何将相关的链接添加到 Cmdlet 帮助主题</span><span class="sxs-lookup"><span data-stu-id="3f2e5-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3f2e5-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3f2e5-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)