---
title: 将 Windows PowerShell 活动添加到 Visual Studio 工具箱 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359646"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>向 Visual Studio 工具箱添加 Windows PowerShell 活动

使用工作流设计器创作 PowerShell 工作流之前，必须先将 PowerShell 活动添加到 Visual Studio 工作流控制台应用程序项目中的 "工具箱"。 下面的过程演示如何将活动从 Microsoft. Core 程序集添加到 Visual Studio 工具箱。

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>将 Windows PowerShell 活动添加到工具箱

1. 在 Visual Studio 中创建新的工作流控制台应用程序项目。

2. 在 "**视图**" 菜单上，单击 **"工具箱**"。

3. 右键单击 "工具箱"，然后单击 "**添加选项卡**"，并为新选项卡指定一个名称，如 "PowerShell 活动"，从而在 "工具箱" 中添加新选项卡。

   通过添加选项卡，可以将 PowerShell 活动与 "工具箱" 中的其他工具进行分组。

4. 在 "新建工具箱" 选项卡上，单击 "**选择项 ...** "。此时将显示 "**选择工具箱项**" 对话框。

5. 在 "**选择工具箱项**" 对话框中，单击 "**系统**" 选项卡。

6. 单击 "**浏览**"。

7. 导航到%WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e 文件夹，然后双击 ""。

8. 单击**确定**。 现在，"工具箱" 中提供了由 "Microsoft. Core" 程序集定义的活动。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 工作流](./writing-a-windows-powershell-workflow.md)

[使用 Windows PowerShell 活动创建工作流](./creating-a-workflow-with-windows-powershell-activities.md)