---
title: 如何添加 Cmdlet 说明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361276"
---
# <a name="how-to-add-a-cmdlet-description"></a>如何添加 Cmdlet 说明

本部分介绍如何添加在 cmdlet 帮助的 "描述" 部分中显示的内容。 在帮助文件中，此内容将添加到每个 cmdlet 的命令节点。

> [!NOTE]
> 若要获取帮助文件的完整视图，请打开位于 Windows PowerShell 安装目录中的 dll-Help 文件之一。 例如，dll-Help 文件包含多个 Windows PowerShell cmdlet 的内容，则不会。

### <a name="to-add-a-description"></a>添加说明

- 首先，更详细地介绍 cmdlet 的基本功能。 在许多情况下，你可以解释 cmdlet 名称中使用的术语，并举例说明不熟悉的概念。 例如，如果 cmdlet 将数据追加到文件，则说明它会将数据添加到现有文件的末尾。

- 若要查找 cmdlet 的所有功能，请查看参数列表。 描述 cmdlet 的主要功能，然后包含其他函数和功能。 例如，如果该 cmdlet 的主要功能是更改一个属性，但该 cmdlet 可以更改所有属性，例如，在详细说明中。 如果 cmdlet 参数允许用户以不同的方式请求信息，请对其进行说明。

- 除了明显的使用之外，还包括有关用户可以使用 cmdlet 的方式的信息。 例如，可以使用 `Get-Host` cmdlet 检索的对象来更改 Windows PowerShell 命令窗口中的文本颜色。

  示例： "`Get-Acl` cmdlet 可获取表示文件或资源的安全描述符的对象。 安全描述符包含资源的访问控制列表 (ACL)。 ACL 指定用户和用户组访问资源所需的权限。

- 详细描述应描述 cmdlet，但它不应描述 cmdlet 使用的概念。 在其他说明中放置概念定义。

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)
