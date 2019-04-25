---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085315"
---
# <a name="new-guid"></a><span data-ttu-id="ca85b-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="ca85b-102">New-Guid</span></span>
<span data-ttu-id="ca85b-103">通常脚本（或写入 DSC 资源）需要唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="ca85b-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="ca85b-104">GUID 使用效果良好，并且调用 .NET Framework Guid 类即可轻松生成 GUID，但使用 cmdlet 可让尚不熟悉 .NET Framework 类的终端用户更容易发现此操作：</span><span class="sxs-lookup"><span data-stu-id="ca85b-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="ca85b-105">PS C:\\&gt;New-Guid</span><span class="sxs-lookup"><span data-stu-id="ca85b-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="ca85b-106">Guid</span><span class="sxs-lookup"><span data-stu-id="ca85b-106">Guid</span></span>

----

<span data-ttu-id="ca85b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="ca85b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
