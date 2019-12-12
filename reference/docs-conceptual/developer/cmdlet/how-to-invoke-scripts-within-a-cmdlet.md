---
title: 如何在 Cmdlet 中调用脚本 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364406"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>如何调用 Cmdlet 中的脚本

此示例演示如何调用提供给 cmdlet 的脚本。 此脚本由 cmdlet 执行，并将其结果作为[system.object](/dotnet/api/System.Management.Automation.PSObject)对象的集合返回给 cmdlet。

## <a name="to-invoke-a-script-block"></a>调用脚本块

1. 命令验证是否向 cmdlet 提供了脚本块。 如果提供了脚本块，则该命令将使用其所需的参数调用脚本块。

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

2. 然后，该脚本将循环访问返回的[system.object](/dotnet/api/System.Management.Automation.PSObject)对象集合，并执行所需的操作。

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
