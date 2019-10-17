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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369966"
---
# <a name="displaying-error-information"></a><span data-ttu-id="450db-102">显示错误信息</span><span class="sxs-lookup"><span data-stu-id="450db-102">Displaying Error Information</span></span>

<span data-ttu-id="450db-103">本主题讨论用户显示错误信息的方式。</span><span class="sxs-lookup"><span data-stu-id="450db-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="450db-104">当 cmdlet 遇到错误时，默认情况下，将显示错误信息，这与以下错误输出类似。</span><span class="sxs-lookup"><span data-stu-id="450db-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="450db-105">但是，用户可以通过将 `$ErrorView` 变量设置为 @no__t，按类别查看错误。</span><span class="sxs-lookup"><span data-stu-id="450db-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="450db-106">类别视图显示来自错误记录的特定信息，而不是错误的自由文本说明。</span><span class="sxs-lookup"><span data-stu-id="450db-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="450db-107">如果要扫描的错误的列表很长，此视图会很有用。</span><span class="sxs-lookup"><span data-stu-id="450db-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="450db-108">在类别视图中，以前的错误消息显示如下。</span><span class="sxs-lookup"><span data-stu-id="450db-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="450db-109">有关错误类别的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="450db-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="450db-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="450db-110">See Also</span></span>

[<span data-ttu-id="450db-111">Windows PowerShell 错误记录</span><span class="sxs-lookup"><span data-stu-id="450db-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="450db-112">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="450db-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
