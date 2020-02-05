---
title: 如何向 Cmdlet 帮助主题添加输入类型 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: 37af16d0279b6487c78f90eb19bcfe5c152ed9e7
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996059"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="b6246-102">如何向 Cmdlet 帮助主题添加输入类型</span><span class="sxs-lookup"><span data-stu-id="b6246-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="b6246-103">本部分介绍如何将输入部分添加到 Windows PowerShell® cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="b6246-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="b6246-104">"输入" 部分列出了 cmdlet 作为管道的输入接受的对象的 .NET 类，可以通过值或按属性名称。</span><span class="sxs-lookup"><span data-stu-id="b6246-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="b6246-105">可以添加到输入部分的类的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="b6246-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="b6246-106">输入类型括在 \<命令中： inputTypes > node，其中每个类都包含在一个 \<命令中： inputType > 元素。</span><span class="sxs-lookup"><span data-stu-id="b6246-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="b6246-107">此架构包括两个 \<maml： description > 元素在每个 \<命令中： inputType > 元素。</span><span class="sxs-lookup"><span data-stu-id="b6246-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="b6246-108">但 `Get-Help` cmdlet 只显示 \<命令的内容： inputType >/\<maml： description >）元素。</span><span class="sxs-lookup"><span data-stu-id="b6246-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="b6246-109">从 Windows PowerShell 3.0 开始，`Get-Help` cmdlet 显示 \<maml： uri > 元素的内容。</span><span class="sxs-lookup"><span data-stu-id="b6246-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="b6246-110">此元素使用户能够将用户定向到描述 .NET 类的主题。</span><span class="sxs-lookup"><span data-stu-id="b6246-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="b6246-111">下面的 XML 演示 \<maml： inputTypes > 节点。</span><span class="sxs-lookup"><span data-stu-id="b6246-111">The following XML shows the \<maml:inputTypes> node.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

<span data-ttu-id="b6246-112">下面的 XML 演示使用 \<maml： inputTypes > 节点记录输入类型的示例。</span><span class="sxs-lookup"><span data-stu-id="b6246-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```