---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: 库,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a><span data-ttu-id="b3d9f-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="b3d9f-103">Save-Script</span></span>

<span data-ttu-id="b3d9f-104">Save-Script cmdlet 可通过将其保存到特定位置来查看脚本文件。</span><span class="sxs-lookup"><span data-stu-id="b3d9f-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="b3d9f-105">说明</span><span class="sxs-lookup"><span data-stu-id="b3d9f-105">Description</span></span>

<span data-ttu-id="b3d9f-106">Save-Script cmdlet 将保存指定脚本。</span><span class="sxs-lookup"><span data-stu-id="b3d9f-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="b3d9f-107">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="b3d9f-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="b3d9f-108">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="b3d9f-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="b3d9f-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="b3d9f-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="b3d9f-110">示例命令</span><span class="sxs-lookup"><span data-stu-id="b3d9f-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="b3d9f-111">示例 1：保存存储库中的脚本</span><span class="sxs-lookup"><span data-stu-id="b3d9f-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="b3d9f-112">此命令将 GalleryINT 存储库中 Fabrikam-ClientScript 脚本的最新版本保存到本地文件夹 C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="b3d9f-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="b3d9f-113">示例 2：通过从 Find-Script cmdlet 管道传递保存脚本的版本</span><span class="sxs-lookup"><span data-stu-id="b3d9f-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="b3d9f-114">第一个命令会从存储库 GalleryINT 中找到 Fabrikam-ClientScript 版本 1.5，并将其保存到文件夹 C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="b3d9f-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="b3d9f-115">第二个命令验证保存的脚本元数据。</span><span class="sxs-lookup"><span data-stu-id="b3d9f-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="b3d9f-116">示例 3：保存存储库中的预发行版脚本</span><span class="sxs-lookup"><span data-stu-id="b3d9f-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="b3d9f-117">此命令将 GalleryINT 存储库中 Fabrikam-ClientScript 脚本的最新版本保存到本地文件夹 C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="b3d9f-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```