---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 库,powershell,cmdlet,psget
title: Get-PSRepository
ms.openlocfilehash: 97279a8ed0087c835fb924991484959cd7237016
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="get-psrepository"></a><span data-ttu-id="4a01a-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4a01a-103">Get-PSRepository</span></span>

<span data-ttu-id="4a01a-104">获取计算机上的已注册存储库。</span><span class="sxs-lookup"><span data-stu-id="4a01a-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="4a01a-105">说明</span><span class="sxs-lookup"><span data-stu-id="4a01a-105">Description</span></span>

<span data-ttu-id="4a01a-106">Get-PSRepository cmdlet 获取计算机上为当前用户注册的 PowerShell 模块存储库。</span><span class="sxs-lookup"><span data-stu-id="4a01a-106">The Get-PSRepository cmdlet gets PowerShell module repositories that are registered for the current user on a computer.</span></span>

<span data-ttu-id="4a01a-107">对于每个已注册存储库，Get-PSRepository 将返回 PSRepository 对象，可根据需要将其通过管道传递到 Unregister-PSRepository 以注销已注册的存储库。</span><span class="sxs-lookup"><span data-stu-id="4a01a-107">For each registered repository, Get-PSRepository returns a PSRepository object which can optionally be piped to Unregister-PSRepository for unregistering a registered repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="4a01a-108">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="4a01a-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="4a01a-109">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="4a01a-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="4a01a-110">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4a01a-110">Get-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a><span data-ttu-id="4a01a-111">示例命令</span><span class="sxs-lookup"><span data-stu-id="4a01a-111">Example commands</span></span>

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```