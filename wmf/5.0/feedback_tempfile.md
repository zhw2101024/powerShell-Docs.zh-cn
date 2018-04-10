---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: ada4fcc0beb3eb74b099f221762341abbf2c3b4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="10d01-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="10d01-102">New-TemporaryFile</span></span>
<span data-ttu-id="10d01-103">有时必须在脚本中创建临时文件。</span><span class="sxs-lookup"><span data-stu-id="10d01-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="10d01-104">可以使用 **New-TemporaryFile** cmdlet 轻松实现此操作：</span><span class="sxs-lookup"><span data-stu-id="10d01-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="10d01-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="10d01-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="10d01-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="10d01-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="10d01-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="10d01-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>