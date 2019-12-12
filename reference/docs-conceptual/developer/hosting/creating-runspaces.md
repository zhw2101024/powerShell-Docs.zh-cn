---
title: 正在创建运行空间 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367576"
---
# <a name="creating-runspaces"></a>创建运行空间

运行空间是主机应用程序调用的命令的操作环境。 此环境包括当前存在的命令和数据，以及当前适用的任何语言限制。

 主机应用程序可以使用 Windows PowerShell 提供的默认运行空间，其中包括所有可用的核心命令，或创建仅包含可用命令子集的自定义运行空间。 若要创建自定义的运行空间，请创建一个[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)对象，并将其分配给运行空间。

## <a name="runspace-tasks"></a>运行空间任务

1. [创建 InitialSessionState](./creating-an-initialsessionstate.md)

2. [创建受限的运行空间](./creating-a-constrained-runspace.md)

3. [创建多个运行空间](./creating-multiple-runspaces.md)

## <a name="see-also"></a>另请参阅
