---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="new-temporaryfile"></a><span data-ttu-id="961a4-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="961a4-102">New-TemporaryFile</span></span>
<span data-ttu-id="961a4-103">有时必须在脚本中创建临时文件。</span><span class="sxs-lookup"><span data-stu-id="961a4-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="961a4-104">可以使用 **New-TemporaryFile** cmdlet 轻松实现此操作：</span><span class="sxs-lookup"><span data-stu-id="961a4-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="961a4-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="961a4-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="961a4-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="961a4-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="961a4-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="961a4-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>

