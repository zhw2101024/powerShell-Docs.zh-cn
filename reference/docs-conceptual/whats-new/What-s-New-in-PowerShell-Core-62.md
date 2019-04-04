---
title: PowerShell Core 6.2 中的新增功能
description: PowerShell Core 6.2 中发布的新功能和更改
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750046"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="c3d6d-103">PowerShell Core 6.2 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="c3d6d-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="c3d6d-104">以下是 PowerShell Core 6.2 中引入的一系列主要新功能和更改。</span><span class="sxs-lookup"><span data-stu-id="c3d6d-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="c3d6d-105">此外还有使 PowerShell 更快更稳定的“无数”“无聊的东西”（以及很多 bug 修复）！</span><span class="sxs-lookup"><span data-stu-id="c3d6d-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="c3d6d-106">若要获取更改的完整列表，请查看我们 [GitHub 上的更改日志](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)。</span><span class="sxs-lookup"><span data-stu-id="c3d6d-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="c3d6d-107">尽管我们在下面公布了一些名字，但是同样感谢实现此版本的[所有社区参与者](https://github.com/PowerShell/PowerShell/graphs/contributors)。</span><span class="sxs-lookup"><span data-stu-id="c3d6d-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="c3d6d-108">引擎更新和修补程序</span><span class="sxs-lookup"><span data-stu-id="c3d6d-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="c3d6d-109">添加 PowerShell 远程处理启用/禁用 cmdlet 警告消息 ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="c3d6d-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="c3d6d-110">`FormatTable` 远程反序列化回归的修补程序 ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="c3d6d-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="c3d6d-111">更新已添加到 PowerShell 的基于任务的 `async` API 以直接返回任务对象 ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="c3d6d-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="c3d6d-112">将 5 个 `InvokeAsync` 重载和 `StopAsync` 添加到 `PowerShell` 类型 ([#8056][])（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="c3d6d-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="c3d6d-113">常规 Cmdlet 更新和修补程序</span><span class="sxs-lookup"><span data-stu-id="c3d6d-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="c3d6d-114">通过存储纯文本来启用适用于非 Windows 的 `SecureString` cmdlet ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="c3d6d-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="c3d6d-115">将已过时的消息添加到 `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="c3d6d-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="c3d6d-116">修复 `Restart-Computer`，以便在 WinRM 不存在时处理 `localhost` ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="c3d6d-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="c3d6d-117">正在托管 PowerShell 时，使 `Start-Job` 引发终止错误 ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="c3d6d-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="c3d6d-118">`PowerShell.Native` 的更新版本和托管测试 ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="c3d6d-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="c3d6d-119">重大更改</span><span class="sxs-lookup"><span data-stu-id="c3d6d-119">Breaking Changes</span></span>

<span data-ttu-id="c3d6d-120">修复写入输出中的 -NoEnumerate 行为，以便与 Windows PowerShell 保持一致 ([#9069][])（感谢 @vexx32！）</span><span class="sxs-lookup"><span data-stu-id="c3d6d-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
