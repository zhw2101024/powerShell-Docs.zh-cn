---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="3e7cf-102">注册 PowerShell 存储库</span><span class="sxs-lookup"><span data-stu-id="3e7cf-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="3e7cf-103">你可以配置 PowerShellGet 以针对内部存储库进行操作。</span><span class="sxs-lookup"><span data-stu-id="3e7cf-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="3e7cf-104">可通过使用以下附加内容完成此配置：</span><span class="sxs-lookup"><span data-stu-id="3e7cf-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="3e7cf-105">Register-PSRepository：为当前用户注册存储库。</span><span class="sxs-lookup"><span data-stu-id="3e7cf-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="3e7cf-106">Unregister-PSRepository：为当前用户删除已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="3e7cf-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="3e7cf-107">Set-PSRepository：为已注册的存储库设置值。</span><span class="sxs-lookup"><span data-stu-id="3e7cf-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="3e7cf-108">Get-PSRepository：为当前用户获取所有已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="3e7cf-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="3e7cf-109">注册存储库后，可以使用 Find-Module 和 Install-Module 对它进行操作。</span><span class="sxs-lookup"><span data-stu-id="3e7cf-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```