---
title: 如何向 Cmdlet 帮助主题添加返回值 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367796"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加返回值

本部分介绍如何将输出部分添加到 Windows PowerShell® cmdlet 帮助主题。 "输出" 部分列出了 cmdlet 返回或沿管道向下传递的对象的 .NET 类。

可以添加到 "输出" 部分的类的数量没有限制。 Cmdlet 的返回类型括在 \<command： returnValues > 节点中，其中每个类都包含在 \<command： returnValue > 元素中。

如果 cmdlet 未生成任何输出，请使用此部分来指示没有输出。 例如，若要替代类名称，请编写 "None" 并提供简短说明。 如果 cmdlet 按条件生成输出，请使用此节点解释条件并描述条件输出。

此架构包括两个 \<maml： description > 每个 \<command： returnValue > 元素中的元素。 但是，@no__t cmdlet 只显示 \<command： returnValue > @no__t/2maml： description > 元素的内容。

从 Windows PowerShell 3.0 开始，@no__t cmdlet 显示 \<maml： uri > 元素的内容。 此元素使用户能够将用户定向到描述 .NET 类的主题。

下面的 XML 显示 \<maml： returnValues > 节点。

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

下面的 XML 显示使用 \<maml： returnValues > 节点记录输出类型的示例。

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



