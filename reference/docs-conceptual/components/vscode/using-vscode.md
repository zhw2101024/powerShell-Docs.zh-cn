---
title: 使用 Visual Studio Code 进行 PowerShell 开发
description: 使用 Visual Studio Code 进行 PowerShell 开发
ms.date: 08/06/2018
ms.openlocfilehash: 5badffd49252e0d72ae2c20d3147ad4b1e92d5ed
ms.sourcegitcommit: cf1a281cce9f7239c440c90f8b2798d32a13778d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882576"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="6454b-103">使用 Visual Studio Code 进行 PowerShell 开发</span><span class="sxs-lookup"><span data-stu-id="6454b-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="6454b-104">除 [PowerShell ISE][ise] 外，PowerShell 还高度支持 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="6454b-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="6454b-105">此外，PowerShell Core 不支持 ISE，但是 Visual Studio Code 在所有平台上（Windows、macOS 和 Linux）均支持 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6454b-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="6454b-106">通过使用 Windows 10 或安装适用于低版本 Windows OS（例如 Windows 8.1 等）的 [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395)，可在 Windows 上结合使用 Visual Studio Code 和 PowerShell 版本 5.</span><span class="sxs-lookup"><span data-stu-id="6454b-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="6454b-107">开始前，请确保系统上安装有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6454b-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="6454b-108">有关 Windows、macOS 和 Linux 上的新式工作负荷，请参阅：</span><span class="sxs-lookup"><span data-stu-id="6454b-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="6454b-109">[在 Linux 上安装 PowerShell Core][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="6454b-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="6454b-110">[在 macOS 上安装 PowerShell Core][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="6454b-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="6454b-111">[在 Windows 上安装 PowerShell Core][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="6454b-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="6454b-112">有关传统 Windows PowerShell 工作负荷，请参阅[安装 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="6454b-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="6454b-113">使用 Visual Studio Code 进行编辑</span><span class="sxs-lookup"><span data-stu-id="6454b-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="6454b-114">1.安装 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6454b-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="6454b-115">**Linux**：请按照[在 Linux 上运行 VS Code](https://code.visualstudio.com/docs/setup/linux) 页面上的安装说明进行操作</span><span class="sxs-lookup"><span data-stu-id="6454b-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="6454b-116">**macOS**：请按照[在 macOS 上运行 VS Code](https://code.visualstudio.com/docs/setup/mac) 页面上的安装说明进行操作</span><span class="sxs-lookup"><span data-stu-id="6454b-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="6454b-117">在 macOS 上，必须安装 OpenSSL 后 PowerShell 扩展方可正常运行。</span><span class="sxs-lookup"><span data-stu-id="6454b-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="6454b-118">实现此要求的最简单方法是安装 [Homebrew](https://brew.sh/)，然后运行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="6454b-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="6454b-119">VS Code 现可成功加载 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="6454b-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="6454b-120">**Windows**：按照[在 Windows 上运行 VS Code](https://code.visualstudio.com/docs/setup/windows) 页面上的安装说明进行操作</span><span class="sxs-lookup"><span data-stu-id="6454b-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="6454b-121">2.安装 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="6454b-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="6454b-122">按照如下方式启动 Visual Studio Code 应用：</span><span class="sxs-lookup"><span data-stu-id="6454b-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="6454b-123">**Windows**：在 PowerShell 会话中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="6454b-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="6454b-124">**Linux**：在终端中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="6454b-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="6454b-125">**macOS**：在终端中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="6454b-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="6454b-126">通过按 Ctrl+P（Mac 上为 Cmd+P）启动“Quick Open”。</span><span class="sxs-lookup"><span data-stu-id="6454b-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="6454b-127">在“Quick Open”中，键入 `ext install powershell` 并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="6454b-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="6454b-128">“扩展”视图随即在侧边栏上打开。</span><span class="sxs-lookup"><span data-stu-id="6454b-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="6454b-129">从 Microsoft 中选择 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="6454b-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="6454b-130">应看到如下内容：</span><span class="sxs-lookup"><span data-stu-id="6454b-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="6454b-132">在 Microsoft 下单击 PowerShell 扩展上的“安装”按钮。</span><span class="sxs-lookup"><span data-stu-id="6454b-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="6454b-133">安装后，“安装”按钮将变为“重载”。</span><span class="sxs-lookup"><span data-stu-id="6454b-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="6454b-134">单击“重载”。</span><span class="sxs-lookup"><span data-stu-id="6454b-134">Click on **Reload**.</span></span>
- <span data-ttu-id="6454b-135">重载 Visual Studio Code 后即可开始编辑。</span><span class="sxs-lookup"><span data-stu-id="6454b-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="6454b-136">例如，若要创建新文件，请单击“文件”->“新建”。</span><span class="sxs-lookup"><span data-stu-id="6454b-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="6454b-137">若要保存，请单击“文件”->“保存”，然后提供一个文件名，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="6454b-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="6454b-138">若要关闭文件，则单击文件名旁的“x”。</span><span class="sxs-lookup"><span data-stu-id="6454b-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="6454b-139">若要退出 Visual Studio Code，请单击“文件”->“退出”。</span><span class="sxs-lookup"><span data-stu-id="6454b-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="6454b-140">在受限制的系统上安装 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="6454b-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="6454b-141">有些系统的设置要求检查所有代码签名，因此需要手动批准 PowerShell 编辑器服务才能在系统上运行。</span><span class="sxs-lookup"><span data-stu-id="6454b-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="6454b-142">如果已经安装 PowerShell 扩展，但出现以下错误，那么更改执行策略的组策略更新可能是原因之一：</span><span class="sxs-lookup"><span data-stu-id="6454b-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="6454b-143">若要手动批准 PowerShell 编辑器服务，则适用于 VSCode 的 PowerShell 扩展打开 PowerShell 提示符并运行：</span><span class="sxs-lookup"><span data-stu-id="6454b-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="6454b-144">系统会提示你“是否要运行来自此不可信发布者的软件？”</span><span class="sxs-lookup"><span data-stu-id="6454b-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="6454b-145">键入 `R` 以运行该文件。</span><span class="sxs-lookup"><span data-stu-id="6454b-145">Type `R` to run the file.</span></span> <span data-ttu-id="6454b-146">然后打开 Visual Studio Code，并检查 PowerShell 扩展是否工作正常。</span><span class="sxs-lookup"><span data-stu-id="6454b-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="6454b-147">如果在开始使用时仍有问题，请在 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) 上告诉我们。</span><span class="sxs-lookup"><span data-stu-id="6454b-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="6454b-148">选择要与扩展一起使用的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="6454b-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="6454b-149">将 PowerShell Core 与 Windows PowerShell 并行安装后，现在可以将特定版本的 PowerShell 与 PowerShell 扩展一起使用。</span><span class="sxs-lookup"><span data-stu-id="6454b-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="6454b-150">使用以下步骤选择版本：</span><span class="sxs-lookup"><span data-stu-id="6454b-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="6454b-151">打开命令托盘（在 Windows 和 Linux 上为 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>，在 macOS 上为 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>）。</span><span class="sxs-lookup"><span data-stu-id="6454b-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="6454b-152">搜索“会话”。</span><span class="sxs-lookup"><span data-stu-id="6454b-152">Search for "Session".</span></span>
1. <span data-ttu-id="6454b-153">单击“PowerShell:显示会话菜单”。</span><span class="sxs-lookup"><span data-stu-id="6454b-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="6454b-154">选择要从列表中使用的 PowerShell 版本 - 例如，“PowerShell Core”。</span><span class="sxs-lookup"><span data-stu-id="6454b-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="6454b-155">此功能通过不同操作系统上的几个已知路径来发现 PowerShell 的安装位置。</span><span class="sxs-lookup"><span data-stu-id="6454b-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="6454b-156">如果已将 PowerShell 安装到非典型位置，则最初可能不会显示在会话菜单中。</span><span class="sxs-lookup"><span data-stu-id="6454b-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="6454b-157">可以按如下所述[添加你自己的自定义路径](#adding-your-own-powershell-paths-to-the-session-menu)来扩展会话菜单。</span><span class="sxs-lookup"><span data-stu-id="6454b-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="6454b-158">还有一种方法可以获取会话菜单。</span><span class="sxs-lookup"><span data-stu-id="6454b-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="6454b-159">当 PowerShell 文件在编辑器中打开时，你会看到右下角的绿色版本号。</span><span class="sxs-lookup"><span data-stu-id="6454b-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="6454b-160">单击此版本号将为你提供会话菜单。</span><span class="sxs-lookup"><span data-stu-id="6454b-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="6454b-161">将你自己的 PowerShell 路径添加到会话菜单</span><span class="sxs-lookup"><span data-stu-id="6454b-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="6454b-162">可以通过 VS Code 设置将其他 PowerShell 可执行文件路径添加到会话菜单。</span><span class="sxs-lookup"><span data-stu-id="6454b-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="6454b-163">向列表 `powershell.powerShellAdditionalExePaths` 添加项或创建该列表（如果它不存在于 `settings.json` 中）：</span><span class="sxs-lookup"><span data-stu-id="6454b-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    // other settings...
}
```

<span data-ttu-id="6454b-164">每个项必须具有：</span><span class="sxs-lookup"><span data-stu-id="6454b-164">Each item must have:</span></span>

* <span data-ttu-id="6454b-165">`exePath`：`pwsh` 或 `powershell` 可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="6454b-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="6454b-166">`versionName`：将显示在会话菜单中的文本。</span><span class="sxs-lookup"><span data-stu-id="6454b-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="6454b-167">可以将默认 PowerShell 版本设置为使用 `powershell.powerShellDefaultVersion` 设置，方法是将其设置为显示在会话菜单中的文本（也称为最后一个设置中的 `versionName`）：</span><span class="sxs-lookup"><span data-stu-id="6454b-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",
    
    // other settings...
}
```

<span data-ttu-id="6454b-168">进行此设置后，重新启动 Visual Studio Code 或使用“开发人员:重新加载窗口”命令托盘操作来重新加载当前的 vscode 窗口。</span><span class="sxs-lookup"><span data-stu-id="6454b-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="6454b-169">如果打开会话菜单，你现在会看到其他 PowerShell 版本！</span><span class="sxs-lookup"><span data-stu-id="6454b-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="6454b-170">如果从源生成 PowerShell，则这是测试 PowerShell 的本地生成的好办法。</span><span class="sxs-lookup"><span data-stu-id="6454b-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="6454b-171">Visual Studio Code 的配置设置</span><span class="sxs-lookup"><span data-stu-id="6454b-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="6454b-172">按照上一段落中的步骤可在 `settings.json` 中添加配置设置。</span><span class="sxs-lookup"><span data-stu-id="6454b-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="6454b-173">我们建议对 Visual Studio Code 添加以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="6454b-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="6454b-174">如果不希望这些设置影响所有文件类型，则 VSCode 还允许按语言进行配置。</span><span class="sxs-lookup"><span data-stu-id="6454b-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="6454b-175">通过将设置置于 `[<language-name>]` 字段，创建语言特定的设置。</span><span class="sxs-lookup"><span data-stu-id="6454b-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="6454b-176">例如：</span><span class="sxs-lookup"><span data-stu-id="6454b-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="6454b-177">有关 VS Code 中文件编码的详细信息，请参阅[了解文件编码](understanding-file-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="6454b-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="6454b-178">使用 Visual Studio Code 进行调试</span><span class="sxs-lookup"><span data-stu-id="6454b-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="6454b-179">无工作区调试</span><span class="sxs-lookup"><span data-stu-id="6454b-179">No-workspace debugging</span></span>

<span data-ttu-id="6454b-180">从 Visual Studio Code 版本 1.9 开始，无需打开包含 PowerShell 脚本的文件夹即可调试 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="6454b-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="6454b-181">单击“文件”->“打开文件...”打开 PowerShell 脚本文件，在行上设一个断点（按 F9），然后按 F5 即可开始调试。</span><span class="sxs-lookup"><span data-stu-id="6454b-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="6454b-182">此时应出现“调试”操作窗格，通过该窗格可以中断调试器、执行、继续和停止调试。</span><span class="sxs-lookup"><span data-stu-id="6454b-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="6454b-183">工作区调试</span><span class="sxs-lookup"><span data-stu-id="6454b-183">Workspace debugging</span></span>

<span data-ttu-id="6454b-184">工作区调试是指文件夹上下文中的调试，该文件夹是使用“文件”菜单的“打开文件夹...”在 Visual Studio Code 中打开的。</span><span class="sxs-lookup"><span data-stu-id="6454b-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="6454b-185">打开的文件夹通常是 PowerShell 项目文件夹和/或 Git 存储库的根文件夹。</span><span class="sxs-lookup"><span data-stu-id="6454b-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="6454b-186">即使在此模式下，按 F5 也可开始调试当前所选的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="6454b-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="6454b-187">但是，通过工作区调试可以定义多个调试配置，而不是只调试当前打开的文件。</span><span class="sxs-lookup"><span data-stu-id="6454b-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="6454b-188">例如，可通过添加配置执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6454b-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="6454b-189">在调试器中启动 Pester 测试</span><span class="sxs-lookup"><span data-stu-id="6454b-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="6454b-190">使用调试器中的参数启动特定文件</span><span class="sxs-lookup"><span data-stu-id="6454b-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="6454b-191">在调试器中启动交互会话</span><span class="sxs-lookup"><span data-stu-id="6454b-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="6454b-192">将调试器附加到 PowerShell 主机进程</span><span class="sxs-lookup"><span data-stu-id="6454b-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="6454b-193">按照以下步骤创建调试配置文件：</span><span class="sxs-lookup"><span data-stu-id="6454b-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="6454b-194">按 Ctrl+Shift+D（Mac 上为 Cmd+Shift+D）打开“调试”视图。</span><span class="sxs-lookup"><span data-stu-id="6454b-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="6454b-195">按工具栏中的“配置”齿轮图标。</span><span class="sxs-lookup"><span data-stu-id="6454b-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="6454b-196">Visual Studio Code 将提示“选择环境”。</span><span class="sxs-lookup"><span data-stu-id="6454b-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="6454b-197">选择“PowerShell”。</span><span class="sxs-lookup"><span data-stu-id="6454b-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="6454b-198">执行此操作时，Visual Studio Code 会在工作区文件夹的根中创建一个目录和一个“.vscode\launch.json”文件。</span><span class="sxs-lookup"><span data-stu-id="6454b-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="6454b-199">这是调试配置的存储位置。</span><span class="sxs-lookup"><span data-stu-id="6454b-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="6454b-200">如果文件位于 Git 存储库中，则通常需要提交 launch.json 文件。</span><span class="sxs-lookup"><span data-stu-id="6454b-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="6454b-201">launch.json 文件的内容为：</span><span class="sxs-lookup"><span data-stu-id="6454b-201">The contents of the launch.json file are:</span></span>

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  <span data-ttu-id="6454b-202">这表示常见调试方案。</span><span class="sxs-lookup"><span data-stu-id="6454b-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="6454b-203">但是，在编辑器中打开此文件时，会显示“添加配置...”按钮。</span><span class="sxs-lookup"><span data-stu-id="6454b-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="6454b-204">按此按钮可添加更多 PowerShell 调试配置。</span><span class="sxs-lookup"><span data-stu-id="6454b-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="6454b-205">其中可添加的一个便捷配置是“PowerShell:**Launch Script**。</span><span class="sxs-lookup"><span data-stu-id="6454b-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="6454b-206">通过此配置，可以使用可选参数指定特定文件，无论编辑器中哪个文件处于活动状态，无论何时按 F5 时，此文件都会启动。</span><span class="sxs-lookup"><span data-stu-id="6454b-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="6454b-207">调试配置建立后，可以在“调试”视图工具栏中的调试配置下拉列表中选择要在调试会话中使用的配置。</span><span class="sxs-lookup"><span data-stu-id="6454b-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="6454b-208">以下博客提供有关将 PowerShell 扩展用于 Visual Studio Code 的有用入门帮助：</span><span class="sxs-lookup"><span data-stu-id="6454b-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="6454b-209">[PowerShell 扩展插件][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="6454b-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="6454b-210">[在 Visual Studio Code 中编写和调试 PowerShell 脚本][debug]</span><span class="sxs-lookup"><span data-stu-id="6454b-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="6454b-211">[Visual Studio Code 调试指南][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="6454b-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="6454b-212">[在 Visual Studio Code 中调试 PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="6454b-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="6454b-213">[在 Visual Studio Code 中进行 PowerShell 开发][getting-started]</span><span class="sxs-lookup"><span data-stu-id="6454b-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="6454b-214">[适用于 PowerShell 开发的 Visual Studio Code 编辑功能 – 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="6454b-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="6454b-215">[适用于 PowerShell 开发的 Visual Studio Code 编辑功能 – 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="6454b-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="6454b-216">[在 Visual Studio Code 中调试 PowerShell 脚本 – 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="6454b-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="6454b-217">[在 Visual Studio Code 中调试 PowerShell 脚本 – 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="6454b-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="6454b-218">适用于 Visual Studio Code 的 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="6454b-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="6454b-219">可以在 [GitHub](https://github.com/PowerShell/vscode-powershell) 上找到 PowerShell 扩展的源代码。</span><span class="sxs-lookup"><span data-stu-id="6454b-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
