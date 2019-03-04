---
title: 显示错误信息 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858273"
---
# <a name="displaying-error-information"></a><span data-ttu-id="017df-102">显示错误信息</span><span class="sxs-lookup"><span data-stu-id="017df-102">Displaying Error Information</span></span>

<span data-ttu-id="017df-103">本主题讨论用户可在其中显示错误的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="017df-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="017df-104">当你的 cmdlet 时遇到错误时，错误信息的演示文稿，默认情况下，类似于以下的错误输出。</span><span class="sxs-lookup"><span data-stu-id="017df-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="017df-105">但是，用户可以查看错误按类别通过设置`$ErrorView`变量`"CategoryView"`。</span><span class="sxs-lookup"><span data-stu-id="017df-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="017df-106">类别视图中显示的错误记录而不是错误的自定义文本说明中的特定信息。</span><span class="sxs-lookup"><span data-stu-id="017df-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="017df-107">此视图可以是如果您有要扫描的错误的长列表。</span><span class="sxs-lookup"><span data-stu-id="017df-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="017df-108">在类别视图中，按如下所示显示以前的错误消息。</span><span class="sxs-lookup"><span data-stu-id="017df-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="017df-109">有关错误类别的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="017df-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="017df-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="017df-110">See Also</span></span>

[<span data-ttu-id="017df-111">Windows PowerShell 错误记录</span><span class="sxs-lookup"><span data-stu-id="017df-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="017df-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="017df-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
