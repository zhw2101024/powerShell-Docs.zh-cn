---
title: PowerShell Core 中的 WS-Management (WSMan) 远程处理
description: 在 PowerShell Core 中使用 WSMan 进行远程处理
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587340"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="db472-103">PowerShell Core 中的 WS-Management (WSMan) 远程处理</span><span class="sxs-lookup"><span data-stu-id="db472-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="db472-104">有关创建远程处理终结点的说明</span><span class="sxs-lookup"><span data-stu-id="db472-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="db472-105">适用于 Windows 的 PowerShell Core 包包括 WinRM 插件 (`pwrshplugin.dll`) 和 `$PSHome` 中的安装脚本 (`Install-PowerShellRemoting.ps1`)。</span><span class="sxs-lookup"><span data-stu-id="db472-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="db472-106">指定终结点时，这些文件可使 PowerShell 接受传入的 PowerShell 远程连接。</span><span class="sxs-lookup"><span data-stu-id="db472-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="db472-107">动机</span><span class="sxs-lookup"><span data-stu-id="db472-107">Motivation</span></span>

<span data-ttu-id="db472-108">安装 PowerShell 可使用 `New-PSSession` 和 `Enter-PSSession` 针对远程计算机创建 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="db472-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="db472-109">若要使其接受传入的 PowerShell 远程连接，用户必须创建一个 WinRM 远程处理终结点。</span><span class="sxs-lookup"><span data-stu-id="db472-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="db472-110">这是一个显式选择加入方案，其中用户运行 Install-PowerShellRemoting.ps1 创建 WinRM 终结点。</span><span class="sxs-lookup"><span data-stu-id="db472-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="db472-111">将其他功能添加到 `Enable-PSRemoting` 以执行相同操作前，安装脚本是一个短期解决方案。</span><span class="sxs-lookup"><span data-stu-id="db472-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="db472-112">有关详细信息，请参阅问题 [#1193](https://github.com/PowerShell/PowerShell/issues/1193)。</span><span class="sxs-lookup"><span data-stu-id="db472-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="db472-113">脚本操作</span><span class="sxs-lookup"><span data-stu-id="db472-113">Script Actions</span></span>

<span data-ttu-id="db472-114">脚本</span><span class="sxs-lookup"><span data-stu-id="db472-114">The script</span></span>

1. <span data-ttu-id="db472-115">在 %windir%\System32\PowerShell 中创建插件目录</span><span class="sxs-lookup"><span data-stu-id="db472-115">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="db472-116">将 pwrshplugin.dll 复制到该位置</span><span class="sxs-lookup"><span data-stu-id="db472-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="db472-117">生成配置文件</span><span class="sxs-lookup"><span data-stu-id="db472-117">Generates a configuration file</span></span>
1. <span data-ttu-id="db472-118">使用 WinRM 注册该插件</span><span class="sxs-lookup"><span data-stu-id="db472-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="db472-119">注册</span><span class="sxs-lookup"><span data-stu-id="db472-119">Registration</span></span>

<span data-ttu-id="db472-120">脚本必须在管理员级别的 PowerShell 会话中执行，并且以两种模式中运行。</span><span class="sxs-lookup"><span data-stu-id="db472-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="db472-121">由其将注册的 PowerShell 实例执行</span><span class="sxs-lookup"><span data-stu-id="db472-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="db472-122">由代表其注册实例的另一 PowerShell 实例执行</span><span class="sxs-lookup"><span data-stu-id="db472-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="db472-123">例如：</span><span class="sxs-lookup"><span data-stu-id="db472-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="db472-124">**注意：** 该远程处理注册脚本将重新启动 WinRM，因此该脚本运行后所有现有 PSRP 会话会立即终止。</span><span class="sxs-lookup"><span data-stu-id="db472-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="db472-125">如果在远程会话期间运行，则会终止连接。</span><span class="sxs-lookup"><span data-stu-id="db472-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="db472-126">如何连接到新的终结点</span><span class="sxs-lookup"><span data-stu-id="db472-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="db472-127">指定 `-ConfigurationName "some endpoint name"`，从而针对新 PowerShell 终结点创建一个 PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="db472-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="db472-128">若要连接到上述示例中的 PowerShell 实例，请使用以下任意一种方式：</span><span class="sxs-lookup"><span data-stu-id="db472-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="db472-129">请注意，未指定 `-ConfigurationName` 的 `New-PSSession` 和 `Enter-PSSession` 调用将以默认 PowerShell 终结点 `microsoft.powershell` 为目标。</span><span class="sxs-lookup"><span data-stu-id="db472-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>