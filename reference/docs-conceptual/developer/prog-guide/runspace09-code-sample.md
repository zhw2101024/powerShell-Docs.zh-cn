---
title: RunSpace09 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 122a40dea93d874a7c131774e3d1abb148bcd4fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360126"
---
# <a name="runspace09-code-sample"></a>RunSpace09 代码示例

下面是[创建一个以异步方式调用管道的控制台应用程序](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)中所述的 Runspace09 示例的源代码。 此示例应用程序创建并打开运行空间，创建并异步调用管道，然后使用管道事件异步处理脚本。 此应用程序运行的脚本将以0.5 秒为间隔创建整数1到10（500毫秒）。

## <a name="code-sample"></a>代码示例

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)
