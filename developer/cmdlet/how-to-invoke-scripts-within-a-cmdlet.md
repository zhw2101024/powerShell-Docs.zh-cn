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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>如何调用 Cmdlet 中的脚本

此示例演示如何调用脚本提供给 cmdlet。 脚本执行 cmdlet，而其结果返回到该 cmdlet 作为一系列[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)对象。

## <a name="to-invoke-a-script-block"></a>若要调用的脚本块

1. 该命令将验证脚本块已提供给 cmdlet。 如果提供的脚本块，该命令将调用其所需的参数的脚本块。

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

2. 然后，该脚本循环访问返回的集合[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)对象，并执行必要的操作。

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

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
