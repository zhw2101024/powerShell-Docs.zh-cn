---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="new-guid"></a><span data-ttu-id="45ee7-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="45ee7-102">New-Guid</span></span>
<span data-ttu-id="45ee7-103">通常脚本（或写入 DSC 资源）需要唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="45ee7-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="45ee7-104">GUID 使用效果良好，并且调用 .NET Framework Guid 类即可轻松生成 GUID，但使用 cmdlet 可让尚不熟悉 .NET Framework 类的终端用户更容易发现此操作：</span><span class="sxs-lookup"><span data-stu-id="45ee7-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="45ee7-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="45ee7-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="45ee7-106">Guid</span><span class="sxs-lookup"><span data-stu-id="45ee7-106">Guid</span></span>

----

<span data-ttu-id="45ee7-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="45ee7-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
