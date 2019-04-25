---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.1 中的已知问题
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084957"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="fd111-103">WMF 5.1 中的已知问题</span><span class="sxs-lookup"><span data-stu-id="fd111-103">Known Issues in WMF 5.1</span></span>

> [!Note]
> <span data-ttu-id="fd111-104">此信息可能随时发生更改。</span><span class="sxs-lookup"><span data-stu-id="fd111-104">This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="fd111-105">以管理员身份启动 PowerShell 快捷方式</span><span class="sxs-lookup"><span data-stu-id="fd111-105">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="fd111-106">在安装 WMF 时，如果尝试以管理员身份通过该快捷方式启动 PowerShell，可能会显示“未指定的错误”消息。</span><span class="sxs-lookup"><span data-stu-id="fd111-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="fd111-107">以非管理员身份重新打开快捷方式，快捷方式现在甚至可以管理员身份工作。</span><span class="sxs-lookup"><span data-stu-id="fd111-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="fd111-108">Pester</span><span class="sxs-lookup"><span data-stu-id="fd111-108">Pester</span></span>

<span data-ttu-id="fd111-109">在本版本中，在 Nano 服务器上使用 Pester 时应注意两个问题：</span><span class="sxs-lookup"><span data-stu-id="fd111-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="fd111-110">由于 FULL CLR 和 CORE CLR 之间的差异，针对 Pester 自身运行测试可能导致一些失败。</span><span class="sxs-lookup"><span data-stu-id="fd111-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="fd111-111">特别是，Validate 方法不可用于 XmlDocument 类型。</span><span class="sxs-lookup"><span data-stu-id="fd111-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="fd111-112">众所周知，尝试验证 NUnit 输出日志的架构的六个测试都将失败。</span><span class="sxs-lookup"><span data-stu-id="fd111-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="fd111-113">一个代码覆盖率测试失败的原因是当前 Nano 服务器中不存在 *WindowsFeature* DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="fd111-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="fd111-114">但是，这些故障通常是无害的，可以放心地忽略。</span><span class="sxs-lookup"><span data-stu-id="fd111-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="fd111-115">操作验证</span><span class="sxs-lookup"><span data-stu-id="fd111-115">Operation Validation</span></span>

- <span data-ttu-id="fd111-116">由于帮助 URI 不起作用，针对 Microsoft.PowerShell.Operation.Validation 模块的 `Update-Help` 将失败</span><span class="sxs-lookup"><span data-stu-id="fd111-116">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="fd111-117">卸载 WMF 后的 DSC</span><span class="sxs-lookup"><span data-stu-id="fd111-117">DSC after uninstall WMF</span></span>

- <span data-ttu-id="fd111-118">卸载 WMF 不会从配置文件夹中删除 DSC MOF 文档。</span><span class="sxs-lookup"><span data-stu-id="fd111-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="fd111-119">如果 MOF 文档包含在较旧系统中不可用的较新属性，DSC 将无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="fd111-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="fd111-120">在这种情况下，请从提升的 PowerShell 控制台运行以下脚本，以清理 DSC 状态。</span><span class="sxs-lookup"><span data-stu-id="fd111-120">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="fd111-121">JEA 虚拟帐户</span><span class="sxs-lookup"><span data-stu-id="fd111-121">JEA Virtual Accounts</span></span>

<span data-ttu-id="fd111-122">升级到 WMF 5.1 后，在 WMF 5.0 中配置为使用虚拟帐户的 JEA 终结点和会话配置不会配置为使用虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="fd111-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="fd111-123">也就是说，在 JEA 会话中运行的命令将在连接用户的身份（而不是临时管理员帐户）下运行，这可能会导致用户无法运行需要提升的权限的命令。</span><span class="sxs-lookup"><span data-stu-id="fd111-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="fd111-124">若要还原虚拟帐户，需要先取消注册，然后重新注册使用虚拟帐户的所有会话配置。</span><span class="sxs-lookup"><span data-stu-id="fd111-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```