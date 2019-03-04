---
title: 如何将 Cmdlet 名称和摘要添加到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861823"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>如何向 Cmdlet 帮助主题添加 Cmdlet 名称和摘要

本部分介绍如何添加的 cmdlet 帮助在名称和摘要部分中显示的内容。 在帮助文件中，此内容添加到每个 cmdlet 的命令节点。

> [!NOTE]
> 查看完整的帮助文件，打开一个 dll Help.xml 文件位于 Windows PowerShell 安装目录。 例如，Microsoft.PowerShell.Commands.Management.dll Help.xml 文件包含内容的多个 Windows PowerShell cmdlet。

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>若要添加的 Cmdlet 名称和摘要

- Cmdlet 帮助可以显示两个 cmdlet 的说明。 第一个描述是被称为摘要的简短说明。 第二个说明是更详细的说明中所讨论[添加到 Cmdlet 帮助主题的详细说明](./how-to-add-a-cmdlet-description.md)。 这两个这些说明应编写为一个段落。

- 摘要不会重复 cmdlet 名称。 通知用户 Get-server cmdlet 获取的服务器是简短，但不是提供信息。 相反，使用同义词功能，并添加到说明的详细信息。

  例如："获取一个对象，表示本地或远程计算机"。

- 使用简单的谓词，如"get"、"创建"和"更改"摘要。 避免使用"设置"，因为它是含糊不清，和复杂单词如"修改。"

  例如："在文件中获取有关验证码签名的信息。"

- 编写使用主动语态。 例如，"使用 TimeSpan 对象..."是更清晰，不是"时间跨度对象可用于..."

- 描述 cmdlet 获取对象时避免"display"的谓词。 尽管 Windows PowerShell 会显示 cmdlet 的数据，但是非常重要，向用户介绍该 cmdlet 将返回可能不会显示其数据的.NET Framework 对象的概念。 如果突出显示，请用户可能不知道，该 cmdlet 返回可能返回的许多其他有用的属性和方法不会显示。

## <a name="see-also"></a>另请参阅

 [Windows PowerShell SDK](../windows-powershell-reference.md)