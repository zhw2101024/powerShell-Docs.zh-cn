---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 核心提供程序"
ms.assetid: 6e24bf6d-4c70-4edf-956a-1e8e4779ba10
ms.openlocfilehash: fdfdfee86884d3ac18a33ac424828faa96ecd8bd
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-core-providers"></a><span data-ttu-id="27908-103">Windows PowerShell 核心提供程序</span><span class="sxs-lookup"><span data-stu-id="27908-103">Windows PowerShell Core Providers</span></span>
<span data-ttu-id="27908-104">此部分包含的帮助主题介绍了 **Microsoft.PowerShell.Core** 模块中的 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="27908-104">This section contains help topics that describe the Windows PowerShell providers in the **Microsoft.PowerShell.Core** module.</span></span>

<span data-ttu-id="27908-105">Windows PowerShell 提供程序是 .NET 程序，用于使专用数据存储中的数据在 Windows PowerShell 中可用，以便你可以轻松地查看和管理它。</span><span class="sxs-lookup"><span data-stu-id="27908-105">Windows PowerShell providers are .NET programs that make the data in a specialized data store available in Windows PowerShell so that you can easily view and manage it.</span></span> <span data-ttu-id="27908-106">提供程序公开的数据显示在驱动器中，它与文件系统驱动器非常相似。</span><span class="sxs-lookup"><span data-stu-id="27908-106">The data that a provider exposes appears in a drive, much like a file system drive.</span></span> <span data-ttu-id="27908-107">有关详细信息，请参阅 [about_Providers [v4]](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242)。</span><span class="sxs-lookup"><span data-stu-id="27908-107">For more information, see [about_Providers [v4]](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242).</span></span>

|<span data-ttu-id="27908-108">提供程序</span><span class="sxs-lookup"><span data-stu-id="27908-108">Provider</span></span>|<span data-ttu-id="27908-109">说明</span><span class="sxs-lookup"><span data-stu-id="27908-109">Description</span></span>|
|------------|---------------|
|[<span data-ttu-id="27908-110">Alias 提供程序 [v3]</span><span class="sxs-lookup"><span data-stu-id="27908-110">Alias Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/dce3f872-aeff-4eb2-8b38-876cd612fc29)|<span data-ttu-id="27908-111">提供对 Windows PowerShell 别名及其值的访问权限。</span><span class="sxs-lookup"><span data-stu-id="27908-111">Provides access to the Windows PowerShell aliases and their values.</span></span>|
|[<span data-ttu-id="27908-112">Environment 提供程序 [v3]</span><span class="sxs-lookup"><span data-stu-id="27908-112">Environment Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/94fcd05d-e702-4706-9b7d-ad7e5fd0ec09)|<span data-ttu-id="27908-113">提供对 Windows 环境变量的访问权限。</span><span class="sxs-lookup"><span data-stu-id="27908-113">Provides access to the Windows environment variables.</span></span>|
|[<span data-ttu-id="27908-114">FileSystem 提供程序 [v3]</span><span class="sxs-lookup"><span data-stu-id="27908-114">FileSystem Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/0e494537-dfdf-437a-8b27-c21e30aa1f9f)|<span data-ttu-id="27908-115">提供对文件和目录的访问权限。</span><span class="sxs-lookup"><span data-stu-id="27908-115">Provides access to files and directories.</span></span>|
|[<span data-ttu-id="27908-116">Function 提供程序 [v3]</span><span class="sxs-lookup"><span data-stu-id="27908-116">Function Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/7dfc92f4-9a88-4399-978d-6d5d224b3e76)|<span data-ttu-id="27908-117">提供对 Windows PowerShell 中所定义函数的访问权限。</span><span class="sxs-lookup"><span data-stu-id="27908-117">Provides access to the functions defined in Windows PowerShell.</span></span>|
|[<span data-ttu-id="27908-118">Registry 提供程序 [v3]</span><span class="sxs-lookup"><span data-stu-id="27908-118">Registry Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/d3c8013c-8caa-48d7-9feb-bfef0d95926e)|<span data-ttu-id="27908-119">提供对系统注册表项和值的访问权限。</span><span class="sxs-lookup"><span data-stu-id="27908-119">Provides access to the system registry keys and values.</span></span>|
|[<span data-ttu-id="27908-120">Variable 提供程序 [v3]</span><span class="sxs-lookup"><span data-stu-id="27908-120">Variable Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/78dbcbbd-7946-4b9b-b75b-146f247f821c)|<span data-ttu-id="27908-121">提供对 Windows PowerShell 变量及其值的访问权限。</span><span class="sxs-lookup"><span data-stu-id="27908-121">Provides access to Windows PowerShell variables and their values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="27908-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27908-122">See Also</span></span>
- [<span data-ttu-id="27908-123">Certificate 提供程序 [v3]</span><span class="sxs-lookup"><span data-stu-id="27908-123">Certificate Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/3f743541-d0c6-4670-809a-b16fb01f7c4d)
- [<span data-ttu-id="27908-124">WSMan 提供程序 [v3]</span><span class="sxs-lookup"><span data-stu-id="27908-124">WSMan Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/4c3d8d36-4f7a-4211-996f-64110e4b2eb7)
- [<span data-ttu-id="27908-125">about_Providers [v4]</span><span class="sxs-lookup"><span data-stu-id="27908-125">about_Providers [v4]</span></span>](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242)
- [<span data-ttu-id="27908-126">Microsoft.PowerShell.Core 模块</span><span class="sxs-lookup"><span data-stu-id="27908-126">Microsoft.PowerShell.Core Module</span></span>](Microsoft.PowerShell.Core-Module.md)

