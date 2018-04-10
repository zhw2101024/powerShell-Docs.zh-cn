---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 库,powershell,cmdlet,psget
title: Test-ScriptFileInfo
ms.openlocfilehash: 56f75007be6e952572aaed7942a1e8714d4104b0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="test-scriptfileinfo"></a><span data-ttu-id="6a62d-103">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="6a62d-103">Test-ScriptFileInfo</span></span>

<span data-ttu-id="6a62d-104">验证脚本文件的元数据注释块。</span><span class="sxs-lookup"><span data-stu-id="6a62d-104">Validates the metadata comment block of a script file.</span></span>

## <a name="description"></a><span data-ttu-id="6a62d-105">说明</span><span class="sxs-lookup"><span data-stu-id="6a62d-105">Description</span></span>

<span data-ttu-id="6a62d-106">Test-ScriptFileInfo cmdlet 验证将使用 Publish-Script cmdlet.发布的脚本的开头部分的注释块。</span><span class="sxs-lookup"><span data-stu-id="6a62d-106">The Test-ScriptFileInfo cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="6a62d-107">如果元数据注释块中有错误，则此 cmdlet 将返回错误的位置或更正方法的相关信息。</span><span class="sxs-lookup"><span data-stu-id="6a62d-107">If the metadata comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="6a62d-108">Cmdlet 语法</span><span class="sxs-lookup"><span data-stu-id="6a62d-108">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Test-ScriptFileInfo -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="6a62d-109">Cmdlet 联机帮助参考</span><span class="sxs-lookup"><span data-stu-id="6a62d-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="6a62d-110">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="6a62d-110">Test-ScriptFileInfo</span></span>](http://go.microsoft.com/fwlink/?LinkId=619791)

## <a name="example-commands"></a><span data-ttu-id="6a62d-111">示例命令</span><span class="sxs-lookup"><span data-stu-id="6a62d-111">Example commands</span></span>
```powershell
# Create a new script file with minimum required metadata values
New-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Description "Script file description goes here"

Get-Content -Path C:\ScriptSharingDemo\Demo-Script.ps1
<#PSScriptInfo
.VERSION 1.0
.GUID 926b47c3-6af2-4b18-b6f5-8b813a9e93ab
.AUTHOR manikb
.COMPANYNAME
.COPYRIGHT
.TAGS
.LICENSEURI
.PROJECTURI
.ICONURI
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
#>
<#
.DESCRIPTION
Script file description goes here
#>
Param()

# Validate and get the script metadata
Test-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1
Version Name Author Description
------- ---- ------ -----------
1.0 Demo-Script manikb Script file description goes here

# This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.
Test-ScriptFileInfo -Path D:\code\Test-Runbook.ps1 | Format-List *

# This command tests the script file Hello-World.ps1, which has no metadata associated with it.
Test-ScriptFileInfo -Path C:\code\Hello-World.ps1
Test-ScriptFileInfo : PSScriptInfo is not specified in the script file 'C:\code\Hello-World.ps1'. You can use the Update-ScriptFileInfo with -Force or New-ScriptFileInfo cmdlet to add the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo -Path C:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (C:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException
    + FullyQualifiedErrorId : MissingPSScriptInfo,Test-ScriptFileInfo

```