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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863563"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>向 Visual Studio 工具箱添加 Windows PowerShell 活动

创作使用工作流设计器的 PowerShell 工作流之前，首先必须将 PowerShell 活动添加到 Visual Studio 工作流控制台应用程序项目中的工具箱中。 以下过程说明如何将活动从 Microsoft.PowerShell.Core.Activities 程序集添加到 Visual Studio 工具箱。

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>将 Windows PowerShell 活动添加到工具箱

1. 在 Visual Studio 中创建新的工作流控制台应用程序项目。

2. 上**视图**菜单上，单击**工具箱**。

3. 通过在此工具箱内右键单击并单击工具箱中添加一个新选项卡**添加选项卡**，并提供一个名称，例如"PowerShell 活动"的新选项卡。

   添加选项卡可以分组 PowerShell 活动单独从工具箱中的其他工具。

4. 在新的工具箱选项卡上，单击**选择项...**.**选择工具箱项**此时将显示对话框。

5. 在中**选择工具箱项**对话框中，单击**System.Activities**选项卡。

6. 单击**浏览**。

7. 导航到 %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e 文件夹并双击 Microsoft.PowerShell.Core.Activities.dll。

8. 单击“确定” 。 定义由 Microsoft.PowerShell.Core.Activities 程序集的活动现可在工具箱中。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 工作流](./writing-a-windows-powershell-workflow.md)

[使用 Windows PowerShell 活动创建工作流](./creating-a-workflow-with-windows-powershell-activities.md)