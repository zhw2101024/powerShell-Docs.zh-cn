---
title: 如何将输入的类型添加到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083427"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加输入类型

本部分介绍如何将输入部分添加到 Windows PowerShell® cmdlet 帮助主题。 输入部分列出了该 cmdlet 接受作为输入通过管道，通过值或属性名称的对象的.NET 类。

可以将它们添加到输入部分的类的数目没有限制。 输入的类型括在\<命令： inputTypes > 节点，而且中所包含的每个类\<命令： inputType > 元素。

架构包含两个\<maml:description > 中每个元素\<命令： inputType > 元素。 但是， `Get-Help` cmdlet 将显示的内容\<命令： inputType > /\<maml:description >) 元素。

从 Windows PowerShell 3.0 开始`Get-Help`cmdlet 将显示的内容\<: uri > 元素。 此元素允许你将用户定向到主题，介绍.NET 类。

下面的 XML 演示\<maml:inputTypes > 节点。

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

下面的 XML 演示使用的示例\<maml:inputTypes > 节点来记录输入的类型。

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```