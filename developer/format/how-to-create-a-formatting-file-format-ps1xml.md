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
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>如何创建格式设置文件 (.format.ps1xml)

本主题介绍如何创建格式设置文件 (。 format.ps1xml)。

> [!NOTE]
> 此外可以通过创建一个 Windows powershell 提供的文件的副本创建格式设置文件。 如果创建的现有文件的副本，删除现有的数字签名，并将您自己的签名添加到新文件。

### <a name="to-create-a-formatps1xml-file"></a>若要创建。 format.ps1xml 文件。

1. 创建文本文件 (.txt) 使用文本编辑器 （如记事本）。

2. 将以下行复制到格式设置文件。

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - \<配置 >\</Configuration > 标记定义根`Configuration`节点。 所有其他 XML 标记将包含在此节点内。

   - <ViewDefinitions> </ViewDefinitions>标记定义`ViewDefinitions`节点。 此节点中定义的所有视图。

3. 将文件保存到 Windows PowerShell 安装文件夹、 您的模块文件夹，或模块文件夹的子文件夹。 保存文件时使用以下名称格式： `MyFile.format.ps1xml`。 必须使用格式设置文件`.format.ps1xml`扩展。

   现在你现可将视图添加到的格式设置文件。 可在格式设置文件中定义的视图数目没有限制。 您可以添加每个对象、 多个视图的同一个对象或由多个对象的单个视图的单一视图。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 格式设置和文件类型](./writing-a-powershell-formatting-file.md)
