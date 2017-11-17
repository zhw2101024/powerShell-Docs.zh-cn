---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a><span data-ttu-id="7287b-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="7287b-102">New-Guid</span></span>
<span data-ttu-id="7287b-103">通常脚本（或写入 DSC 资源）需要唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="7287b-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="7287b-104">GUID 使用效果良好，并且调用 .NET Framework Guid 类即可轻松生成 GUID，但使用 cmdlet 可让尚不熟悉 .NET Framework 类的终端用户更容易发现此操作：</span><span class="sxs-lookup"><span data-stu-id="7287b-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="7287b-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="7287b-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="7287b-106">Guid</span><span class="sxs-lookup"><span data-stu-id="7287b-106">Guid</span></span>

----

<span data-ttu-id="7287b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="7287b-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

