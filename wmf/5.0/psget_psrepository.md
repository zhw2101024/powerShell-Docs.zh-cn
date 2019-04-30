---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058006"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="7a12d-102">注册 PowerShell 存储库</span><span class="sxs-lookup"><span data-stu-id="7a12d-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="7a12d-103">你可以配置 PowerShellGet 以针对内部存储库进行操作。</span><span class="sxs-lookup"><span data-stu-id="7a12d-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="7a12d-104">可通过使用以下附加内容完成此配置：</span><span class="sxs-lookup"><span data-stu-id="7a12d-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="7a12d-105">Register-PSRepository：为当前用户注册存储库。</span><span class="sxs-lookup"><span data-stu-id="7a12d-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="7a12d-106">Unregister-PSRepository：删除当前用户已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="7a12d-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="7a12d-107">Set-PSRepository：为已注册的存储库设置值。</span><span class="sxs-lookup"><span data-stu-id="7a12d-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="7a12d-108">Get-PSRepository：为当前用户获取所有已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="7a12d-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="7a12d-109">注册存储库后，可以使用 Find-Module 和 Install-Module 对它进行操作。</span><span class="sxs-lookup"><span data-stu-id="7a12d-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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
