---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057838"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="ceae9-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="ceae9-102">New-TemporaryFile</span></span>
<span data-ttu-id="ceae9-103">有时必须在脚本中创建临时文件。</span><span class="sxs-lookup"><span data-stu-id="ceae9-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="ceae9-104">可以使用 **New-TemporaryFile** cmdlet 轻松实现此操作：</span><span class="sxs-lookup"><span data-stu-id="ceae9-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="ceae9-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="ceae9-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="ceae9-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="ceae9-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="ceae9-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="ceae9-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
