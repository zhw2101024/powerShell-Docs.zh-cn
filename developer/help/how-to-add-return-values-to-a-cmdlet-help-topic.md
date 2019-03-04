---
title: 如何添加返回值复制到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859433"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加返回值

本部分介绍如何将 OUTPUTS 节添加到 Windows PowerShell® cmdlet 帮助主题。 OUTPUTS 节列出了该 cmdlet 返回或管道向下传递对象的.NET 的类。

你可以将它们添加到输出部分的类的数目没有限制。 Cmdlet 的返回类型括在\<命令： returnValues > 节点，而且中所包含的每个类\<命令： returnValue > 元素。

如果 cmdlet 不生成任何输出，使用此部分以指示没有任何输出。 例如，而不是类名称，编写"None"，并提供简要说明。 如果该 cmdlet 将有条件地生成输出，使用此节点进行解释条件和说明条件的输出。

架构包含两个\<maml:description > 中每个元素\<命令： returnValue > 元素。 但是， `Get-Help` cmdlet 将显示的内容\<命令： returnValue > /\<maml:description > 元素。

从 Windows PowerShell 3.0 开始`Get-Help`cmdlet 将显示的内容\<: uri > 元素。 此元素允许你将用户定向到主题，介绍.NET 类。

下面的 XML 演示\<maml:returnValues > 节点。

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

下面的 XML 演示使用的示例\<maml:returnValues > 节点以文档输出类型。

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



