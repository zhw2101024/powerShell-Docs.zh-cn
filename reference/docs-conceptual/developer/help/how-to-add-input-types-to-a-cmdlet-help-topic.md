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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加输入类型

本部分介绍如何将输入部分添加到 Windows PowerShell® cmdlet 帮助主题。 "输入" 部分列出了 cmdlet 作为管道的输入接受的对象的 .NET 类，可以通过值或按属性名称。

可以添加到输入部分的类的数量没有限制。 输入类型括在 \<命令中： inputTypes > node，其中每个类都包含在一个 \<命令中： inputType > 元素。

此架构包括两个 \<maml： description > 元素在每个 \<命令中： inputType > 元素。 但 `Get-Help` cmdlet 只显示 \<命令的内容： inputType >/\<maml： description >）元素。

从 Windows PowerShell 3.0 开始，`Get-Help` cmdlet 显示 \<maml： uri > 元素的内容。 此元素使用户能够将用户定向到描述 .NET 类的主题。

下面的 XML 演示 \<maml： inputTypes > 节点。

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

下面的 XML 演示使用 \<maml： inputTypes > 节点记录输入类型的示例。

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