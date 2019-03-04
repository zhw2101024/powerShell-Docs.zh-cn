---
title: 创建自定义用户界面 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863713"
---
# <a name="creating-a-custom-user-interface"></a>创建自定义用户界面

Windows PowerShell 提供了抽象类和接口，可用于创建托管 Windows PowerShell 引擎的自定义交互式 UI。 若要创建自定义 UI，必须实现[System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost)类。 （可选） 还可以实现[System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)并[System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface)类，以及[System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession)并[System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection)接口。
