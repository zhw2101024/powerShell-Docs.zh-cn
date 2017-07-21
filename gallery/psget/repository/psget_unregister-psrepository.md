---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Unregister-PSRepository
ms.openlocfilehash: 91380210f262208fce39d596bd6c2ad05a819fbf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="unregister-psrepository"></a><span data-ttu-id="47bec-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="47bec-103">Unregister-PSRepository</span></span>

<span data-ttu-id="47bec-104">取消注册存储库。</span><span class="sxs-lookup"><span data-stu-id="47bec-104">Unregisters a repository.</span></span>

## <a name="description"></a><span data-ttu-id="47bec-105">说明</span><span class="sxs-lookup"><span data-stu-id="47bec-105">Description</span></span>

<span data-ttu-id="47bec-106">Unregister-PSRepository cmdlet 为当前用户注销存储库。</span><span class="sxs-lookup"><span data-stu-id="47bec-106">The Unregister-PSRepository cmdlet unregisters a repository for the current user.</span></span>
- <span data-ttu-id="47bec-107">允许为企业和断开连接的方案注销和重新注册 PSGallery 存储库。</span><span class="sxs-lookup"><span data-stu-id="47bec-107">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
- <span data-ttu-id="47bec-108">用户可重新注册 PSGallery，只需运行 `Register-PSRepository -Default`</span><span class="sxs-lookup"><span data-stu-id="47bec-108">Users can re-register the PSGallery by simply running `Register-PSRepository -Default`</span></span>
- <span data-ttu-id="47bec-109">由于 PSGallery 是 Publish-Module 和 Publish-Script cmdlet 中的默认发布存储库，如果 PSGallery 在已注册的存储库列表中不可用，将会引发错误。</span><span class="sxs-lookup"><span data-stu-id="47bec-109">Since PSGallery is the default publish repository in Publish-Module and Publish-Script cmdlets, an error will be thrown if PSGallery is not available in the registered repository list.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="47bec-110">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="47bec-110">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="47bec-111">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="47bec-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="47bec-112">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="47bec-112">Unregister-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a><span data-ttu-id="47bec-113">示例命令</span><span class="sxs-lookup"><span data-stu-id="47bec-113">Example commands</span></span>

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a><span data-ttu-id="47bec-114">允许为企业和断开连接的方案注销和重新注册 PSGallery 存储库。</span><span class="sxs-lookup"><span data-stu-id="47bec-114">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

