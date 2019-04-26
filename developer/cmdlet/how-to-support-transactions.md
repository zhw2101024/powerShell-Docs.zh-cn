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
# <a name="how-to-support-transactions"></a><span data-ttu-id="b6d5a-102">如何支持事务</span><span class="sxs-lookup"><span data-stu-id="b6d5a-102">How to Support Transactions</span></span>

<span data-ttu-id="b6d5a-103">此示例演示将对事务的支持添加到 cmdlet 的基本代码元素。</span><span class="sxs-lookup"><span data-stu-id="b6d5a-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6d5a-104">有关 Windows PowerShell 如何处理事务的详细信息，请参阅[有关事务][about_Transactions]。</span><span class="sxs-lookup"><span data-stu-id="b6d5a-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="b6d5a-105">若要支持事务</span><span class="sxs-lookup"><span data-stu-id="b6d5a-105">To support transactions</span></span>

1. <span data-ttu-id="b6d5a-106">Cmdlet 属性声明时，指定该 cmdlet 支持事务。</span><span class="sxs-lookup"><span data-stu-id="b6d5a-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="b6d5a-107">Windows PowerShell 时该 cmdlet 支持事务，将添加`UseTransaction`cmdlet 将在运行时参数。</span><span class="sxs-lookup"><span data-stu-id="b6d5a-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="b6d5a-108">在输入处理方法之一，添加`if`块来确定事务是否可用。</span><span class="sxs-lookup"><span data-stu-id="b6d5a-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="b6d5a-109">如果`if`语句解析为`true`，可以在当前事务的上下文中执行此语句中的操作。</span><span class="sxs-lookup"><span data-stu-id="b6d5a-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="b6d5a-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6d5a-110">See Also</span></span>

[<span data-ttu-id="b6d5a-111">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6d5a-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
