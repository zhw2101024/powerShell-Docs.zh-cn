---
title: 如何调用一个 Cmdlet 中的脚本 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055778"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="4a40b-102">如何调用 Cmdlet 中的脚本</span><span class="sxs-lookup"><span data-stu-id="4a40b-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="4a40b-103">此示例演示如何调用脚本提供给 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a40b-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="4a40b-104">脚本执行 cmdlet，而其结果返回到该 cmdlet 作为一系列[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)对象。</span><span class="sxs-lookup"><span data-stu-id="4a40b-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="4a40b-105">若要调用的脚本块</span><span class="sxs-lookup"><span data-stu-id="4a40b-105">To invoke a script block</span></span>

1. <span data-ttu-id="4a40b-106">该命令将验证脚本块已提供给 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a40b-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="4a40b-107">如果提供的脚本块，该命令将调用其所需的参数的脚本块。</span><span class="sxs-lookup"><span data-stu-id="4a40b-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="4a40b-108">然后，该脚本循环访问返回的集合[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)对象，并执行必要的操作。</span><span class="sxs-lookup"><span data-stu-id="4a40b-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="4a40b-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a40b-109">See Also</span></span>

[<span data-ttu-id="4a40b-110">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4a40b-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
