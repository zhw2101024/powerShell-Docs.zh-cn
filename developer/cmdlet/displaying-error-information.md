---
title: 显示错误信息 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858273"
---
# <a name="displaying-error-information"></a>显示错误信息

本主题讨论用户可在其中显示错误的信息的方法。

当你的 cmdlet 时遇到错误时，错误信息的演示文稿，默认情况下，类似于以下的错误输出。

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

但是，用户可以查看错误按类别通过设置`$ErrorView`变量`"CategoryView"`。 类别视图中显示的错误记录而不是错误的自定义文本说明中的特定信息。 此视图可以是如果您有要扫描的错误的长列表。 在类别视图中，按如下所示显示以前的错误消息。

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

有关错误类别的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。

## <a name="see-also"></a>另请参阅

[Windows PowerShell 错误记录](./windows-powershell-error-records.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
