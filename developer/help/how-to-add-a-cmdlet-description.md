---
title: 如何添加的 Cmdlet 说明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862593"
---
# <a name="how-to-add-a-cmdlet-description"></a>如何添加 Cmdlet 说明

本部分介绍如何添加的 cmdlet 帮助描述部分中显示的内容。 在帮助文件中，此内容添加到每个 cmdlet 的命令节点。

> [!NOTE]
> 查看完整的帮助文件，打开一个 dll Help.xml 文件位于 Windows PowerShell 安装目录。 例如，Microsoft.PowerShell.Commands.Management.dll Help.xml 文件包含内容的多个 Windows PowerShell cmdlet。

### <a name="to-add-a-description"></a>若要添加说明

- 首先介绍更多详细信息中的 cmdlet 的基本功能。 在许多情况下，可以解释的 cmdlet 名称中使用的条款和说明的示例不熟悉的概念。 例如，如果该 cmdlet 将数据追加到文件，说明它将数据添加到现有文件的末尾。

- 若要查找所有 cmdlet 的功能，请查看参数列表。 描述主要功能的 cmdlet，并随后包括其他功能和特性。 例如，如果该 cmdlet 的主要功能是若要更改一个属性，但该 cmdlet 可以更改的所有属性，这样说中详细说明。 如果 cmdlet 参数让不同的方式收集信息的用户，则说明它。

- 包括的用户可以使用 cmdlet，除了明显的使用方式的信息。 例如，可以使用该对象的`Get-Host`cmdlet 检索要更改 Windows PowerShell 命令窗口中的文本颜色。

  例如：" `Get-Acl` Cmdlet 获取表示文件或资源的安全描述符的对象。 安全描述符包含资源的访问控制列表 (ACL)。 ACL 可指定用户和用户组具有访问该资源的权限。"

- 详细的说明应描述 cmdlet，但它应描述此 cmdlet 将使用的概念。 将概念定义放置在其他说明。

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)
