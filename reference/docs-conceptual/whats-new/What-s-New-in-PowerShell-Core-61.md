---
title: PowerShell Core 6.1 中的新增内容
description: PowerShell Core 6.1 中发布的新功能和更改
ms.date: 09/13/2018
ms.openlocfilehash: fe1e892d4a13a7758f5405867fdd7488c059f5cc
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293310"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="8ac70-103">PowerShell Core 6.1 中的新增内容</span><span class="sxs-lookup"><span data-stu-id="8ac70-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="8ac70-104">以下是 PowerShell Core 6.1 中引入的一系列新功能和更改。</span><span class="sxs-lookup"><span data-stu-id="8ac70-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="8ac70-105">此外还有使 PowerShell 更快更稳定的“无数”“无聊的东西”（以及很多 bug 修复）！</span><span class="sxs-lookup"><span data-stu-id="8ac70-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="8ac70-106">若要获取更改的完整列表，请查看我们 [GitHub 上的更改日志](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="8ac70-107">尽管我们在下面公布了一些名字，但是同样感谢实现此版本的[所有社区参与者](https://github.com/PowerShell/PowerShell/graphs/contributors)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="8ac70-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-108">.NET Core 2.1</span></span>

<span data-ttu-id="8ac70-109">在[于 5 月发布](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/)后，PowerShell Core 6.1 已移动至 .NET Core 2.1，从而对 PowerShell 进行了很多改进，其中包括：</span><span class="sxs-lookup"><span data-stu-id="8ac70-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="8ac70-110">性能改进（参见[下方](#performance-improvements)）</span><span class="sxs-lookup"><span data-stu-id="8ac70-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="8ac70-111">Alpine Linux 支持（预览版）</span><span class="sxs-lookup"><span data-stu-id="8ac70-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="8ac70-112">[.NET 全局工具支持](/dotnet/core/tools/global-tools) - 即将在 PowerShell 中推出</span><span class="sxs-lookup"><span data-stu-id="8ac70-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="8ac70-113">.NET Core 的 Windows 兼容包</span><span class="sxs-lookup"><span data-stu-id="8ac70-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="8ac70-114">在 Windows 上，.NET 团队发布了 [.NET Core 的 Windows 兼容包](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/)，这是一组程序集，可将大量已删除的 API 重新添加至 Windows 上的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="8ac70-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="8ac70-115">我们已将 Windows 兼容包添加到 PowerShell Core 6.1 版本中，让使用这些 API 的任何模块或脚本都能处于可用状态。</span><span class="sxs-lookup"><span data-stu-id="8ac70-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="8ac70-116">Windows兼容包使 PowerShell Core 能使用 Windows 10 2018 年 10 月更新和 Windows Server 2019 附带的 1900 多个 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ac70-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="8ac70-117">对应用程序允许列表的支持</span><span class="sxs-lookup"><span data-stu-id="8ac70-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="8ac70-118">PowerShell Core 6.1 与支持 [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) 和 [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) 应用程序允许列表的 Windows PowerShell 5.1 具有奇偶一致性。</span><span class="sxs-lookup"><span data-stu-id="8ac70-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="8ac70-119">根据应用程序允许列表，可使用 PowerShell [受限语言模式](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/)精确地控制允许执行的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="8ac70-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="8ac70-120">性能改进</span><span class="sxs-lookup"><span data-stu-id="8ac70-120">Performance improvements</span></span>

<span data-ttu-id="8ac70-121">PowerShell Core 6.0 取得了一些显着的性能提升。</span><span class="sxs-lookup"><span data-stu-id="8ac70-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="8ac70-122">PowerShell Core 6.1 持续提高部分操作的速度。</span><span class="sxs-lookup"><span data-stu-id="8ac70-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="8ac70-123">例如，`Group-Object` 的速度提高了 66%：</span><span class="sxs-lookup"><span data-stu-id="8ac70-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="8ac70-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="8ac70-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="8ac70-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="8ac70-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="8ac70-127">时间 (秒)</span><span class="sxs-lookup"><span data-stu-id="8ac70-127">Time (sec)</span></span>   | <span data-ttu-id="8ac70-128">25.178</span><span class="sxs-lookup"><span data-stu-id="8ac70-128">25.178</span></span>                 | <span data-ttu-id="8ac70-129">19.653</span><span class="sxs-lookup"><span data-stu-id="8ac70-129">19.653</span></span>              | <span data-ttu-id="8ac70-130">6.641</span><span class="sxs-lookup"><span data-stu-id="8ac70-130">6.641</span></span>               |
| <span data-ttu-id="8ac70-131">加快 (%)</span><span class="sxs-lookup"><span data-stu-id="8ac70-131">Speed-up (%)</span></span> | <span data-ttu-id="8ac70-132">N/A</span><span class="sxs-lookup"><span data-stu-id="8ac70-132">N/A</span></span>                    | <span data-ttu-id="8ac70-133">21.9%</span><span class="sxs-lookup"><span data-stu-id="8ac70-133">21.9%</span></span>               | <span data-ttu-id="8ac70-134">66.2%</span><span class="sxs-lookup"><span data-stu-id="8ac70-134">66.2%</span></span>               |

<span data-ttu-id="8ac70-135">同样，像这样的排序方案提高了 15% 以上：</span><span class="sxs-lookup"><span data-stu-id="8ac70-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="8ac70-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="8ac70-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="8ac70-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="8ac70-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="8ac70-139">时间 (秒)</span><span class="sxs-lookup"><span data-stu-id="8ac70-139">Time (sec)</span></span>   | <span data-ttu-id="8ac70-140">12.170</span><span class="sxs-lookup"><span data-stu-id="8ac70-140">12.170</span></span>                 | <span data-ttu-id="8ac70-141">8.493</span><span class="sxs-lookup"><span data-stu-id="8ac70-141">8.493</span></span>               | <span data-ttu-id="8ac70-142">7.08</span><span class="sxs-lookup"><span data-stu-id="8ac70-142">7.08</span></span>                |
| <span data-ttu-id="8ac70-143">加快 (%)</span><span class="sxs-lookup"><span data-stu-id="8ac70-143">Speed-up (%)</span></span> | <span data-ttu-id="8ac70-144">N/A</span><span class="sxs-lookup"><span data-stu-id="8ac70-144">N/A</span></span>                    | <span data-ttu-id="8ac70-145">30.2%</span><span class="sxs-lookup"><span data-stu-id="8ac70-145">30.2%</span></span>               | <span data-ttu-id="8ac70-146">16.6%</span><span class="sxs-lookup"><span data-stu-id="8ac70-146">16.6%</span></span>               |

`Import-Csv` <span data-ttu-id="8ac70-147">在从 Windows PowerShell 回归后，速度也显著提升了。</span><span class="sxs-lookup"><span data-stu-id="8ac70-147">has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="8ac70-148">以下示例使用具有 26,616 行和 6 列的测试 CSV：</span><span class="sxs-lookup"><span data-stu-id="8ac70-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="8ac70-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="8ac70-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="8ac70-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="8ac70-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="8ac70-152">时间 (秒)</span><span class="sxs-lookup"><span data-stu-id="8ac70-152">Time (sec)</span></span>   | <span data-ttu-id="8ac70-153">0.441</span><span class="sxs-lookup"><span data-stu-id="8ac70-153">0.441</span></span>                  | <span data-ttu-id="8ac70-154">1.069</span><span class="sxs-lookup"><span data-stu-id="8ac70-154">1.069</span></span>               | <span data-ttu-id="8ac70-155">0.268</span><span class="sxs-lookup"><span data-stu-id="8ac70-155">0.268</span></span>                  |
| <span data-ttu-id="8ac70-156">加快 (%)</span><span class="sxs-lookup"><span data-stu-id="8ac70-156">Speed-up (%)</span></span> | <span data-ttu-id="8ac70-157">N/A</span><span class="sxs-lookup"><span data-stu-id="8ac70-157">N/A</span></span>                    | <span data-ttu-id="8ac70-158">-142.4%</span><span class="sxs-lookup"><span data-stu-id="8ac70-158">-142.4%</span></span>             | <span data-ttu-id="8ac70-159">74.9%（来自 WPS 的 39.2%）</span><span class="sxs-lookup"><span data-stu-id="8ac70-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="8ac70-160">最后，使用 Windows PowerShell，从 JSON 到 `PSObject` 的转换速度提高了 50% 以上。</span><span class="sxs-lookup"><span data-stu-id="8ac70-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="8ac70-161">以下示例使用大约 2MB 的测试 JSON 文件：</span><span class="sxs-lookup"><span data-stu-id="8ac70-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="8ac70-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="8ac70-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="8ac70-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="8ac70-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="8ac70-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="8ac70-165">时间 (秒)</span><span class="sxs-lookup"><span data-stu-id="8ac70-165">Time (sec)</span></span>   | <span data-ttu-id="8ac70-166">0.259</span><span class="sxs-lookup"><span data-stu-id="8ac70-166">0.259</span></span>                  | <span data-ttu-id="8ac70-167">0.577</span><span class="sxs-lookup"><span data-stu-id="8ac70-167">0.577</span></span>               | <span data-ttu-id="8ac70-168">0.125</span><span class="sxs-lookup"><span data-stu-id="8ac70-168">0.125</span></span>                  |
| <span data-ttu-id="8ac70-169">加快 (%)</span><span class="sxs-lookup"><span data-stu-id="8ac70-169">Speed-up (%)</span></span> | <span data-ttu-id="8ac70-170">N/A</span><span class="sxs-lookup"><span data-stu-id="8ac70-170">N/A</span></span>                    | <span data-ttu-id="8ac70-171">-122.8%</span><span class="sxs-lookup"><span data-stu-id="8ac70-171">-122.8%</span></span>             | <span data-ttu-id="8ac70-172">78.3%（从 WPS 为 51.7%）</span><span class="sxs-lookup"><span data-stu-id="8ac70-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="8ac70-173">在 Windows 上检查 `system32` 以获取兼容的内置模块</span><span class="sxs-lookup"><span data-stu-id="8ac70-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="8ac70-174">在 Windows 10 1809 更新和 Windows Server 2019 中，我们更新了许多内置 PowerShell 模块，将其标记为与 PowerShell Core 兼容。</span><span class="sxs-lookup"><span data-stu-id="8ac70-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="8ac70-175">当 PowerShell Core 6.1 启动时，它会自动将 `$windir\System32` 包含为 `PSModulePath` 环境变量的一部分。</span><span class="sxs-lookup"><span data-stu-id="8ac70-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="8ac70-176">但是，如果模块 `CompatiblePSEdition` 被标记为与 `Core` 兼容，则它仅将模块公开给 `Get-Module` 和 `Import-Module`。</span><span class="sxs-lookup"><span data-stu-id="8ac70-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="8ac70-177">可能会看到不同的可用模块，具体取决于安装的角色和功能。</span><span class="sxs-lookup"><span data-stu-id="8ac70-177">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="8ac70-178">可以替代此行为，使用 `-SkipEditionCheck` 开关参数显示所有模块。</span><span class="sxs-lookup"><span data-stu-id="8ac70-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="8ac70-179">我们还在表输出中添加了 `PSEdition` 属性。</span><span class="sxs-lookup"><span data-stu-id="8ac70-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="8ac70-180">有关此行为的更多信息，请查看 [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="8ac70-181">Markdown cmdlet 和呈现</span><span class="sxs-lookup"><span data-stu-id="8ac70-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="8ac70-182">Markdown 是创建可读明文文档的标准，其基本格式可以呈现为 HTML。</span><span class="sxs-lookup"><span data-stu-id="8ac70-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="8ac70-183">我们在 6.1 中添加了一些 cmdlet，允许在控制台中转换和呈现 Markdown 文档，包括：</span><span class="sxs-lookup"><span data-stu-id="8ac70-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="8ac70-184">例如，`Show-Markdown` 在控制台中呈现 Markdown 文件：</span><span class="sxs-lookup"><span data-stu-id="8ac70-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Show-Markdown 示例](./images/markdown_example.png)

<span data-ttu-id="8ac70-186">若要详细了解这些 cmdlet 的工作方式，请查看[此 RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="8ac70-187">实验性功能标志</span><span class="sxs-lookup"><span data-stu-id="8ac70-187">Experimental feature flags</span></span>

<span data-ttu-id="8ac70-188">实验性功能标志使用户可以打开尚未最终确定的功能。</span><span class="sxs-lookup"><span data-stu-id="8ac70-188">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="8ac70-189">这些实验性功能不受支持，可能存在 bug。</span><span class="sxs-lookup"><span data-stu-id="8ac70-189">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="8ac70-190">可以在 [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md) 中了解有关此功能的更多信息。</span><span class="sxs-lookup"><span data-stu-id="8ac70-190">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="8ac70-191">Web cmdlet 的改进</span><span class="sxs-lookup"><span data-stu-id="8ac70-191">Web cmdlet improvements</span></span>

<span data-ttu-id="8ac70-192">感谢 [@markekraus ](https://github.com/markekraus)，我们对 Web cmdlet 进行了一系列改进：[`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="8ac70-192">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="8ac70-193">和 [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-193">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="8ac70-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - 对于 `application-json` 响应，默认编码设置为 UTF-8</span><span class="sxs-lookup"><span data-stu-id="8ac70-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="8ac70-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` 参数允许不符合标准的 `Content-Type` 标头</span><span class="sxs-lookup"><span data-stu-id="8ac70-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="8ac70-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` 参数支持简化的 `multipart/form-data` 支持</span><span class="sxs-lookup"><span data-stu-id="8ac70-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="8ac70-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - 合规且不区分大小写的关系键处理</span><span class="sxs-lookup"><span data-stu-id="8ac70-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="8ac70-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) -添加 Web cmdlet 的 `-Resume` 参数</span><span class="sxs-lookup"><span data-stu-id="8ac70-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="8ac70-199">远程处理的改进</span><span class="sxs-lookup"><span data-stu-id="8ac70-199">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="8ac70-200">适用于容器的 PowerShell Direct 尝试先使用 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8ac70-200">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="8ac70-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) 是 PowerShell 和 Hyper-V 的一项功能，允许在没有网络连接或其他远程管理服务的情况下连接到 Hyper-V VM 或容器。</span><span class="sxs-lookup"><span data-stu-id="8ac70-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="8ac70-202">在过去，PowerShell Direct 使用容器上的收件箱 Windows PowerShell 实例进行连接。</span><span class="sxs-lookup"><span data-stu-id="8ac70-202">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span>
<span data-ttu-id="8ac70-203">现在，PowerShell Direct 先尝试使用 `PATH` 环境变量上任何可用的 `pwsh.exe` 进行连接。</span><span class="sxs-lookup"><span data-stu-id="8ac70-203">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="8ac70-204">如果 `pwsh.exe` 不可用，PowerShell Direct 则会回退为使用 `powershell.exe`。</span><span class="sxs-lookup"><span data-stu-id="8ac70-204">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="8ac70-205">`Enable-PSRemoting` 现在为预览版本创建单独的远程处理终结点</span><span class="sxs-lookup"><span data-stu-id="8ac70-205">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

`Enable-PSRemoting` <span data-ttu-id="8ac70-206">现在创建两个远程会话配置：</span><span class="sxs-lookup"><span data-stu-id="8ac70-206">now creates two remoting session configurations:</span></span>

- <span data-ttu-id="8ac70-207">一个用于 PowerShell 的主要版本。</span><span class="sxs-lookup"><span data-stu-id="8ac70-207">One for the major version of PowerShell.</span></span> <span data-ttu-id="8ac70-208">例如，`PowerShell.6`。</span><span class="sxs-lookup"><span data-stu-id="8ac70-208">For example, `PowerShell.6`.</span></span> <span data-ttu-id="8ac70-209">根据“系统范围”的 PowerShell 6 会话配置，次要版本更新可依赖于此终结点</span><span class="sxs-lookup"><span data-stu-id="8ac70-209">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="8ac70-210">一个版本特定的会话配置，例如：</span><span class="sxs-lookup"><span data-stu-id="8ac70-210">One version-specific session configuration, for example:</span></span> `PowerShell.6.1.0`

<span data-ttu-id="8ac70-211">如果要在同一台计算机上安装并访问多个 PowerShell 6 版本，则此行为会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="8ac70-211">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="8ac70-212">此外，预览版本的 PowerShell 现在可以在运行 `Enable-PSRemoting` cmdlet 后获取自己的远程会话配置：</span><span class="sxs-lookup"><span data-stu-id="8ac70-212">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="8ac70-213">如果之前未设置 WinRM，则输出可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="8ac70-213">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="8ac70-214">然后可以查看 PowerShell 6 的预览版和稳定版本以及每个特定版本单独的 PowerShell 会话配置。</span><span class="sxs-lookup"><span data-stu-id="8ac70-214">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="8ac70-215">SSH 支持的 `user@host:port` 语法</span><span class="sxs-lookup"><span data-stu-id="8ac70-215">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="8ac70-216">SSH 客户端通常支持格式为 `user@host:port` 的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="8ac70-216">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="8ac70-217">我们通过将 SSH 添加为 PowerShell 远程处理的协议，增加了对这种连接字符串格式的支持：</span><span class="sxs-lookup"><span data-stu-id="8ac70-217">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="8ac70-218">用于在 Windows 上添加资源管理器 shell 上下文菜单的 MSI 选项</span><span class="sxs-lookup"><span data-stu-id="8ac70-218">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="8ac70-219">感谢 [@bergmeister](https://github.com/bergmeister) 的帮助，现在可以在 Windows 上启用上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="8ac70-219">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="8ac70-220">现在，可以从 Windows 资源管理器中的任何文件夹打开系统范围的 PowerShell 6.1 安装：</span><span class="sxs-lookup"><span data-stu-id="8ac70-220">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![PowerShell 6 的 Shell 上下文菜单](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="8ac70-222">超值服务</span><span class="sxs-lookup"><span data-stu-id="8ac70-222">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="8ac70-223">Windows 快捷方式跳转列表中的“以管理员身份运行”</span><span class="sxs-lookup"><span data-stu-id="8ac70-223">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="8ac70-224">感谢 [@bergmeister](https://github.com/bergmeister) 的帮助，PowerShell Core 快捷方式的跳转列表现已包含“以管理员身份运行”：</span><span class="sxs-lookup"><span data-stu-id="8ac70-224">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![PowerShell 6 跳转列表中的“以管理员身份运行”](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="8ac70-226">`cd -` 返回到上一目录</span><span class="sxs-lookup"><span data-stu-id="8ac70-226">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="8ac70-227">或者，在 Linux 上：</span><span class="sxs-lookup"><span data-stu-id="8ac70-227">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="8ac70-228">`cd` 和 `cd --` 也更改为 `$HOME`。</span><span class="sxs-lookup"><span data-stu-id="8ac70-228">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="8ac70-229">感谢 [@iSazonov](https://github.com/iSazonov) 的帮助，[`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet 已移植到 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="8ac70-229">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="8ac70-230">`Update-Help` 更改为非管理员命令</span><span class="sxs-lookup"><span data-stu-id="8ac70-230">`Update-Help` as non-admin</span></span>

<span data-ttu-id="8ac70-231">根据大众需求，`Update-Help` 不再需要以管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="8ac70-231">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
`Update-Help` <span data-ttu-id="8ac70-232">现在默认将帮助保存到用户范围的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8ac70-232">now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="8ac70-233">`PSCustomObject` 上的新方法/属性</span><span class="sxs-lookup"><span data-stu-id="8ac70-233">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="8ac70-234">感谢 [@iSazonov](https://github.com/iSazonov) 的帮助，我们为 `PSCustomObject` 添加了新的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="8ac70-234">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span>
`PSCustomObject` <span data-ttu-id="8ac70-235">现在包括类似于其他对象的 `Count`/`Length` 属性。</span><span class="sxs-lookup"><span data-stu-id="8ac70-235">now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="8ac70-236">此工作还包括 `ForEach` 和 `Where` 方法，这些方法允许对 `PSCustomObject` 项进行操作和筛选：</span><span class="sxs-lookup"><span data-stu-id="8ac70-236">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="8ac70-237">感谢 @SimonWahlin 的帮助，我们已将 `-Not` 参数添加到 `Where-Object`。</span><span class="sxs-lookup"><span data-stu-id="8ac70-237">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="8ac70-238">现在可在管道中筛选对象，查看是否有不存在的属性或 null/空属性值。</span><span class="sxs-lookup"><span data-stu-id="8ac70-238">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="8ac70-239">例如，此命令返回未定义任何依赖服务的所有服务：</span><span class="sxs-lookup"><span data-stu-id="8ac70-239">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="8ac70-240">`New-ModuleManifest` 创建无 BOM 的 UTF-8 文档</span><span class="sxs-lookup"><span data-stu-id="8ac70-240">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="8ac70-241">由于我们在 PowerShell 6.0 中推出无 BOM 的 UTF-8，更新了 `New-ModuleManifest` cmdlet 以创建无 BOM 的 UTF-8 文档，而不是 UTF-16 文档。</span><span class="sxs-lookup"><span data-stu-id="8ac70-241">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="8ac70-242">从 PSMethod 到委托的转换</span><span class="sxs-lookup"><span data-stu-id="8ac70-242">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="8ac70-243">感谢 [@powercode ](https://github.com/powercode) 的帮助，我们现已支持将 `PSMethod` 转换为委托。</span><span class="sxs-lookup"><span data-stu-id="8ac70-243">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="8ac70-244">这允许执行类似于将 `PSMethod` `[M]::DoubleStrLen` 作为委托值传递到 `[M]::AggregateString` 中的操作：</span><span class="sxs-lookup"><span data-stu-id="8ac70-244">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="8ac70-245">有关此更改的详细信息，请参阅 [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-245">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="8ac70-246">`Measure-Object` 中的标准偏差</span><span class="sxs-lookup"><span data-stu-id="8ac70-246">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="8ac70-247">感谢 [@CloudyDino](https://github.com/CloudyDino) 的帮助，我们已向 `Measure-Object` 添加了 `StandardDeviation` 属性：</span><span class="sxs-lookup"><span data-stu-id="8ac70-247">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="8ac70-248">感谢 [@maybe-hello-world](https://github.com/maybe-hello-world) 的帮助，`Get-PfxCertificate` 现已具备采用 `SecureString` 的 `Password` 参数。</span><span class="sxs-lookup"><span data-stu-id="8ac70-248">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="8ac70-249">这允许以非交互方式使用它：</span><span class="sxs-lookup"><span data-stu-id="8ac70-249">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="8ac70-250">删除 `more` 函数</span><span class="sxs-lookup"><span data-stu-id="8ac70-250">Removal of the `more` function</span></span>

<span data-ttu-id="8ac70-251">在过去，PowerShell 在 Windows 上发布了一个名为 `more` 的函数，它包含 `more.com`。</span><span class="sxs-lookup"><span data-stu-id="8ac70-251">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="8ac70-252">该函数现在已删除。</span><span class="sxs-lookup"><span data-stu-id="8ac70-252">That function has now been removed.</span></span>

<span data-ttu-id="8ac70-253">此外，`help` 函数已改为在 Windows 上使用 `more.com`，或在非 Windows 平台上使用 `$env:PAGER` 指定的系统默认页导航。</span><span class="sxs-lookup"><span data-stu-id="8ac70-253">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="8ac70-254">`cd DriveName:` 现在将用户返回到该驱动器中的当前工作目录</span><span class="sxs-lookup"><span data-stu-id="8ac70-254">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="8ac70-255">以前使用 `Set-Location` 或 `cd` 返回到 PSDrive 会将用户发送到该驱动器的默认位置。</span><span class="sxs-lookup"><span data-stu-id="8ac70-255">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="8ac70-256">感谢 [@mcbobke](https://github.com/mcbobke) 的帮助，现在会将用户发送到该会话最后一个已知的当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="8ac70-256">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="8ac70-257">Windows PowerShell 类型加速器</span><span class="sxs-lookup"><span data-stu-id="8ac70-257">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="8ac70-258">我们已在 Windows PowerShell 中包括以下类型加速器，以便更轻松地处理它们对应的类型：</span><span class="sxs-lookup"><span data-stu-id="8ac70-258">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- `[adsi]`<span data-ttu-id="8ac70-259">：</span><span class="sxs-lookup"><span data-stu-id="8ac70-259">:</span></span> `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`<span data-ttu-id="8ac70-260">：</span><span class="sxs-lookup"><span data-stu-id="8ac70-260">:</span></span> `System.DirectoryServices.DirectorySearcher`
- `[wmi]`<span data-ttu-id="8ac70-261">：</span><span class="sxs-lookup"><span data-stu-id="8ac70-261">:</span></span> `System.Management.ManagementObject`
- `[wmiclass]`<span data-ttu-id="8ac70-262">：</span><span class="sxs-lookup"><span data-stu-id="8ac70-262">:</span></span> `System.Management.ManagementClass`
- `[wmisearcher]`<span data-ttu-id="8ac70-263">：</span><span class="sxs-lookup"><span data-stu-id="8ac70-263">:</span></span> `System.Management.ManagementObjectSearcher`

<span data-ttu-id="8ac70-264">这些类型的加速器未包含在 PowerShell 6 中，但已添加到在 Windows 上运行的 PowerShell 6.1 中。</span><span class="sxs-lookup"><span data-stu-id="8ac70-264">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="8ac70-265">这些类型可用于轻松构建 AD 和 WMI 对象。</span><span class="sxs-lookup"><span data-stu-id="8ac70-265">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="8ac70-266">例如，可以使用 LDAP 进行查询：</span><span class="sxs-lookup"><span data-stu-id="8ac70-266">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="8ac70-267">以下示例创建 Win32_OperatingSystem CIM 对象：</span><span class="sxs-lookup"><span data-stu-id="8ac70-267">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="8ac70-268">此示例返回 Win32_OperatingSystem 类的 ManagementClass 对象。</span><span class="sxs-lookup"><span data-stu-id="8ac70-268">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="8ac70-269">所有 `-LiteralPath` 参数的 `-lp` 别名</span><span class="sxs-lookup"><span data-stu-id="8ac70-269">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="8ac70-270">感谢 [@kvprasoon](https://github.com/kvprasoon) 的帮助，我们现在为所有具有 `-LiteralPath` 参数的内置 PowerShell cmdlet 提供了参数别名 `-lp`。</span><span class="sxs-lookup"><span data-stu-id="8ac70-270">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="8ac70-271">重大更改</span><span class="sxs-lookup"><span data-stu-id="8ac70-271">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="8ac70-272">Windows 上基于 MSI 的安装路径</span><span class="sxs-lookup"><span data-stu-id="8ac70-272">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="8ac70-273">在 Windows 上，MSI 包现在会安装到以下路径：</span><span class="sxs-lookup"><span data-stu-id="8ac70-273">On Windows, the MSI package now installs to the following path:</span></span>

- `$env:ProgramFiles\PowerShell\6\` <span data-ttu-id="8ac70-274">用于稳定安装 6.x</span><span class="sxs-lookup"><span data-stu-id="8ac70-274">for the stable installation of 6.x</span></span>
- `$env:ProgramFiles\PowerShell\6-preview\` <span data-ttu-id="8ac70-275">用于 6.x 的预览安装</span><span class="sxs-lookup"><span data-stu-id="8ac70-275">for the preview installation of 6.x</span></span>

<span data-ttu-id="8ac70-276">此更改确保 Microsoft Update 可以更新/服务于 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="8ac70-276">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="8ac70-277">有关详细信息，请查看 [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-277">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="8ac70-278">只能使用环境变量禁用遥测</span><span class="sxs-lookup"><span data-stu-id="8ac70-278">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="8ac70-279">PowerShell Core 在启动时会向 Microsoft 发送基本的遥测数据。</span><span class="sxs-lookup"><span data-stu-id="8ac70-279">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="8ac70-280">该数据包括 OS 名称、OS 版本和 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="8ac70-280">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="8ac70-281">此数据帮助我们更好地了解使用 PowerShell 的环境，并能确定新功能和修复的优先级。</span><span class="sxs-lookup"><span data-stu-id="8ac70-281">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="8ac70-282">要选择退出此遥测，请将环境变量 `POWERSHELL_TELEMETRY_OPTOUT` 设置为 `true`、`yes` 或 `1`。</span><span class="sxs-lookup"><span data-stu-id="8ac70-282">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="8ac70-283">我们不再支持删除文件 `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` 以禁用遥测。</span><span class="sxs-lookup"><span data-stu-id="8ac70-283">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="8ac70-284">在 Unix 平台上的 PowerShell 远程处理中禁用 HTTP 基本身份验证</span><span class="sxs-lookup"><span data-stu-id="8ac70-284">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="8ac70-285">为了防止使用未加密的流量，Unix 平台上的 PowerShell 远程处理现在需要使用 NTLM/Negotiate 或 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="8ac70-285">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="8ac70-286">有关这些更改的详细信息，请查看[问题 #6779](https://github.com/PowerShell/PowerShell/issues/6779)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-286">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="8ac70-287">已在 Add-Type 中删除作为受支持语言的 `VisualBasic`</span><span class="sxs-lookup"><span data-stu-id="8ac70-287">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="8ac70-288">在过去，可以使用 `Add-Type` cmdlet 编译 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="8ac70-288">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="8ac70-289">Visual Basic 很少与 `Add-Type` 一起使用。</span><span class="sxs-lookup"><span data-stu-id="8ac70-289">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="8ac70-290">我们已删除此功能以减小 PowerShell 的大小。</span><span class="sxs-lookup"><span data-stu-id="8ac70-290">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="8ac70-291">已清理 `CommandTypes.Workflow` 和 `WorkflowInfoCleaned` 的使用</span><span class="sxs-lookup"><span data-stu-id="8ac70-291">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="8ac70-292">有关这些更改的详细信息，请查看 [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-292">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="8ac70-293">组对象现在对组进行排序</span><span class="sxs-lookup"><span data-stu-id="8ac70-293">Group-Object now sorts the groups</span></span>

<span data-ttu-id="8ac70-294">作为性能改进的一部分，`Group-Object` 现在返回组的已排序列表。</span><span class="sxs-lookup"><span data-stu-id="8ac70-294">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="8ac70-295">虽然不应依赖于顺序，但如果想要第一组，则可能会被此更改所破坏。</span><span class="sxs-lookup"><span data-stu-id="8ac70-295">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="8ac70-296">我们认为这种性能改进是值得更改的，因为依赖于以前行为的影响很小。</span><span class="sxs-lookup"><span data-stu-id="8ac70-296">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="8ac70-297">有关此更改的详细信息，请参阅[问题 #7409](https://github.com/PowerShell/PowerShell/issues/7409)。</span><span class="sxs-lookup"><span data-stu-id="8ac70-297">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>
