---
title: GetProc03 (VB.NET) 的示例代码 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058243"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03 (VB.NET) 示例代码

下面的代码演示如何实现`Get-Process`cmdlet，它可以接受管道输入。 此实现中定义`Name`接受管道输入的参数从基于提供的名称，在本地计算机检索进程信息，然后使用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)作为将对象发送到管道的输出机制的方法。

## <a name="code-sample"></a>代码示例

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->