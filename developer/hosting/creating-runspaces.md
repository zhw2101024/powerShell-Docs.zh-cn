---
title: 创建运行空间 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082934"
---
# <a name="creating-runspaces"></a>创建运行空间

在运行空间是由主机应用程序调用的命令的操作环境。 此环境包含命令和当前存在的数据和当前应用任何语言限制。

 主机应用程序可以使用默认的运行空间提供的 Windows PowerShell 中，其中包括所有可用的核心命令，或创建自定义的运行空间，包括可用命令的一个子集。 若要创建的自定义的运行空间，您创建[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，并将其分配给你的运行空间。

## <a name="runspace-tasks"></a>运行空间任务

1. [创建 InitialSessionState](./creating-an-initialsessionstate.md)

2. [创建受限运行空间](./creating-a-constrained-runspace.md)

3. [创建多个运行空间](./creating-multiple-runspaces.md)

## <a name="see-also"></a>另请参阅
