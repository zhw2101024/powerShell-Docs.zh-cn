---
title: 如何支持事务 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067852"
---
# <a name="how-to-support-transactions"></a>如何支持事务

此示例演示将对事务的支持添加到 cmdlet 的基本代码元素。

> [!IMPORTANT]
> 有关 Windows PowerShell 如何处理事务的详细信息，请参阅[有关事务][about_Transactions]。

## <a name="to-support-transactions"></a>若要支持事务

1. Cmdlet 属性声明时，指定该 cmdlet 支持事务。
   Windows PowerShell 时该 cmdlet 支持事务，将添加`UseTransaction`cmdlet 将在运行时参数。

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. 在输入处理方法之一，添加`if`块来确定事务是否可用。
   如果`if`语句解析为`true`，可以在当前事务的上下文中执行此语句中的操作。

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
