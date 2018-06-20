---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217985"
---
# <a name="new-temporaryfile"></a><span data-ttu-id="0299a-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="0299a-102">New-TemporaryFile</span></span>
<span data-ttu-id="0299a-103">有时必须在脚本中创建临时文件。</span><span class="sxs-lookup"><span data-stu-id="0299a-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="0299a-104">可以使用 **New-TemporaryFile** cmdlet 轻松实现此操作：</span><span class="sxs-lookup"><span data-stu-id="0299a-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="0299a-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="0299a-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="0299a-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="0299a-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="0299a-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="0299a-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
