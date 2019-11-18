---
title: 使用 Visual Studio Code 进行 PowerShell 开发
description: 使用 Visual Studio Code 进行 PowerShell 开发
ms.date: 11/07/2019
ms.openlocfilehash: b083388174dbae4a50da73156d2fce41412613a7
ms.sourcegitcommit: 14b50e5446f69729f72231f5dc6f536cdd1084c3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73933886"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="39ecc-103">使用 Visual Studio Code 进行 PowerShell 开发</span><span class="sxs-lookup"><span data-stu-id="39ecc-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="39ecc-104">除 [PowerShell ISE][ise] 外，PowerShell 还在 Visual Studio Code (VSCode) 中受到高度支持。</span><span class="sxs-lookup"><span data-stu-id="39ecc-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="39ecc-105">PowerShell Core 不支持 ISE，但 VSCode 在所有平台上均受到 PowerShell Core 支持：Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="39ecc-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="39ecc-106">通过使用 Windows 10 或安装适用于低版本 Windows OS（例如 Windows 8.1 ）的 Windows Management Framework 5.1，可在 Windows 上结合使用 VSCode 和 PowerShell 版本 5。</span><span class="sxs-lookup"><span data-stu-id="39ecc-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="39ecc-107">有关详细信息，请参阅[安装和配置 WMF 5.1](/powershell/scripting/wmf/setup/install-configure)。</span><span class="sxs-lookup"><span data-stu-id="39ecc-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="39ecc-108">开始前，请确保系统上安装有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="39ecc-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="39ecc-109">有关 Windows、macOS 和 Linux 上的新式工作负荷，请参阅以下链接：</span><span class="sxs-lookup"><span data-stu-id="39ecc-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="39ecc-110">[在 Linux 上安装 PowerShell Core][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="39ecc-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="39ecc-111">[在 macOS 上安装 PowerShell Core][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="39ecc-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="39ecc-112">[在 Windows 上安装 PowerShell Core][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="39ecc-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="39ecc-113">有关传统 Windows PowerShell 工作负载，请参阅[安装 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="39ecc-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="39ecc-114">使用 VSCode 进行编辑</span><span class="sxs-lookup"><span data-stu-id="39ecc-114">Editing with VSCode</span></span>

1. <span data-ttu-id="39ecc-115">安装 VSCode。</span><span class="sxs-lookup"><span data-stu-id="39ecc-115">Install VSCode.</span></span> <span data-ttu-id="39ecc-116">有关详细信息，请参阅[设置 Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview) 概述。</span><span class="sxs-lookup"><span data-stu-id="39ecc-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="39ecc-117">每个平台都有安装说明：</span><span class="sxs-lookup"><span data-stu-id="39ecc-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="39ecc-118">**Linux**：请按照[在 Linux 上运行 VSCode](https://code.visualstudio.com/docs/setup/linux) 页上的安装说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="39ecc-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="39ecc-119">**macOS**：请按照[在 macOS 上运行 VSCode](https://code.visualstudio.com/docs/setup/mac) 页上的安装说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="39ecc-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="39ecc-120">在 macOS 上，必须安装 OpenSSL 后 PowerShell 扩展方可正常运行。</span><span class="sxs-lookup"><span data-stu-id="39ecc-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="39ecc-121">实现此要求的最简单方法是安装 [Homebrew](https://brew.sh/)，然后运行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="39ecc-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="39ecc-122">VSCode 现可成功加载 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="39ecc-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="39ecc-123">**Windows**：请按照[在 Windows 上运行 VSCode](https://code.visualstudio.com/docs/setup/windows) 页上的安装说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="39ecc-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="39ecc-124">安装 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="39ecc-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="39ecc-125">通过以下方式启动 VSCode 应用：</span><span class="sxs-lookup"><span data-stu-id="39ecc-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="39ecc-126">**Windows**：在 PowerShell 会话中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="39ecc-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="39ecc-127">**Linux**：在终端中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="39ecc-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="39ecc-128">**macOS**：在终端中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="39ecc-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="39ecc-129">通过按 <kbd>Ctrl</kbd>+<kbd>P</kbd>，在 Windows 或 Linux 上启动“Quick Open”  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="39ecc-130">在 macOS 上，按 <kbd>Cmd</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="39ecc-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="39ecc-131">在“Quick Open”中，键入 `ext install powershell`，然后按 ENTER  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="39ecc-132">“扩展”视图随即在侧边栏上打开  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="39ecc-133">从 Microsoft 中选择 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="39ecc-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="39ecc-134">应会看到类似于下图的 VSCode 屏幕：</span><span class="sxs-lookup"><span data-stu-id="39ecc-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](../../images/using-vscode/vscode.png)

   1. <span data-ttu-id="39ecc-136">在 Microsoft 下单击 PowerShell 扩展上的“安装”按钮  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="39ecc-137">安装后，“安装”按钮将变为“重载”   。</span><span class="sxs-lookup"><span data-stu-id="39ecc-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="39ecc-138">单击“重载”  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="39ecc-139">重载 VSCode 后即可开始编辑。</span><span class="sxs-lookup"><span data-stu-id="39ecc-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="39ecc-140">例如，若要创建新文件，请单击“文件”>“新建”  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="39ecc-141">若要保存，请单击“文件”>“保存”  ，然后提供文件名，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="39ecc-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="39ecc-142">若要关闭文件，请单击文件名旁的 `X`。</span><span class="sxs-lookup"><span data-stu-id="39ecc-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="39ecc-143">若要退出 VSCode，请单击“文件”>“退出”  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="39ecc-144">在受限制的系统上安装 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="39ecc-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="39ecc-145">有些系统的设置要求检查所有代码签名，且需要手动批准 PowerShell 编辑器服务才能在系统上运行。</span><span class="sxs-lookup"><span data-stu-id="39ecc-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="39ecc-146">如果已经安装 PowerShell 扩展，但出现以下错误，那么更改执行策略的组策略更新可能是原因之一：</span><span class="sxs-lookup"><span data-stu-id="39ecc-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="39ecc-147">若要手动批准 PowerShell 编辑器服务和适用于 VSCode 的 PowerShell 扩展，则打开 PowerShell 提示符并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="39ecc-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="39ecc-148">系统会提示你“是否要运行来自此不可信发布者的软件？” </span><span class="sxs-lookup"><span data-stu-id="39ecc-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="39ecc-149">键入 `A` 以运行该文件。</span><span class="sxs-lookup"><span data-stu-id="39ecc-149">Type `A` to run the file.</span></span> <span data-ttu-id="39ecc-150">然后打开 VSCode，并检查 PowerShell 扩展是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="39ecc-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="39ecc-151">如果在开始使用时仍有问题，请在 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) 上告诉我们。</span><span class="sxs-lookup"><span data-stu-id="39ecc-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="39ecc-152">选择要与扩展一起使用的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="39ecc-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="39ecc-153">将 PowerShell Core 与 Windows PowerShell 并行安装后，现在可以将特定版本的 PowerShell 与 PowerShell 扩展一起使用。</span><span class="sxs-lookup"><span data-stu-id="39ecc-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="39ecc-154">使用以下步骤选择版本：</span><span class="sxs-lookup"><span data-stu-id="39ecc-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="39ecc-155">在 Windows 或 Linux 上，使用 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 打开“命令面板”  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="39ecc-156">在 macOS 上，使用 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="39ecc-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="39ecc-157">搜索“会话”  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-157">Search for **Session**.</span></span>
1. <span data-ttu-id="39ecc-158">单击“PowerShell:  显示会话菜单”。</span><span class="sxs-lookup"><span data-stu-id="39ecc-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="39ecc-159">选择要从列表中使用的 PowerShell 版本，例如：PowerShell Core  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39ecc-160">此功能通过不同操作系统上的几个已知路径来发现 PowerShell 的安装位置。</span><span class="sxs-lookup"><span data-stu-id="39ecc-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="39ecc-161">如果已将 PowerShell 安装到非典型位置，则最初可能不会显示在会话菜单中。</span><span class="sxs-lookup"><span data-stu-id="39ecc-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="39ecc-162">可以按如下所述[添加你自己的自定义路径](#adding-your-own-powershell-paths-to-the-session-menu)来扩展会话菜单。</span><span class="sxs-lookup"><span data-stu-id="39ecc-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="39ecc-163">还有一种方法可以获取会话菜单。</span><span class="sxs-lookup"><span data-stu-id="39ecc-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="39ecc-164">当 PowerShell 文件在编辑器中打开时，你会看到右下角的绿色版本号。</span><span class="sxs-lookup"><span data-stu-id="39ecc-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="39ecc-165">单击此版本号将为你提供会话菜单。</span><span class="sxs-lookup"><span data-stu-id="39ecc-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="39ecc-166">将你自己的 PowerShell 路径添加到会话菜单</span><span class="sxs-lookup"><span data-stu-id="39ecc-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="39ecc-167">可以通过 VSCode 设置将其他 PowerShell 可执行文件路径添加到会话菜单。</span><span class="sxs-lookup"><span data-stu-id="39ecc-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="39ecc-168">向列表 `powershell.powerShellAdditionalExePaths` 添加项或创建该列表（如果它不存在于 `settings.json` 中）：</span><span class="sxs-lookup"><span data-stu-id="39ecc-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="39ecc-169">每个项必须具有：</span><span class="sxs-lookup"><span data-stu-id="39ecc-169">Each item must have:</span></span>

* <span data-ttu-id="39ecc-170">`exePath`：`pwsh` 或 `powershell` 可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="39ecc-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="39ecc-171">`versionName`：将显示在会话菜单中的文本。</span><span class="sxs-lookup"><span data-stu-id="39ecc-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="39ecc-172">可以将默认 PowerShell 版本设置为使用 `powershell.powerShellDefaultVersion` 设置，方法是将其设置为显示在会话菜单中的文本（也是最后一个设置中的 `versionName`）：</span><span class="sxs-lookup"><span data-stu-id="39ecc-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="39ecc-173">配置此设置后，请重新启动 VSCode 或从“命令面板”  中重新加载当前 VSCode 窗口，键入“开发人员:  重载窗口”。</span><span class="sxs-lookup"><span data-stu-id="39ecc-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="39ecc-174">如果打开会话菜单，你现在会看到其他 PowerShell 版本！</span><span class="sxs-lookup"><span data-stu-id="39ecc-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="39ecc-175">如果从源生成 PowerShell，则这是测试 PowerShell 的本地生成的好办法。</span><span class="sxs-lookup"><span data-stu-id="39ecc-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="39ecc-176">VSCode 的配置设置</span><span class="sxs-lookup"><span data-stu-id="39ecc-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="39ecc-177">按照上一段落中的步骤可在 `settings.json` 中添加配置设置。</span><span class="sxs-lookup"><span data-stu-id="39ecc-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="39ecc-178">我们建议对 VSCode 进行以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="39ecc-178">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="39ecc-179">如果不希望这些设置影响所有文件类型，则 VSCode 还允许按语言进行配置。</span><span class="sxs-lookup"><span data-stu-id="39ecc-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="39ecc-180">创建在 `[<language-name>]` 字段中放置设置，可以配置特定于语言的设置。</span><span class="sxs-lookup"><span data-stu-id="39ecc-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="39ecc-181">例如：</span><span class="sxs-lookup"><span data-stu-id="39ecc-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="39ecc-182">有关 VSCode 中文件编码的详细信息，请参阅[了解文件编码](understanding-file-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="39ecc-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="39ecc-183">使用 VSCode 进行调试</span><span class="sxs-lookup"><span data-stu-id="39ecc-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="39ecc-184">无工作区调试</span><span class="sxs-lookup"><span data-stu-id="39ecc-184">No-workspace debugging</span></span>

<span data-ttu-id="39ecc-185">从 VSCode 版本 1.9 开始，无需打开包含 PowerShell 脚本的文件夹即可调试 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="39ecc-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="39ecc-186">单击“文件”>“打开文件...”  来打开 PowerShell 脚本文件，在行上设一个断点，按 <kbd>F9</kbd>，然后按 <kbd>F5</kbd> 即可开始调试。</span><span class="sxs-lookup"><span data-stu-id="39ecc-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="39ecc-187">此时应出现“调试”操作窗格，通过该窗格可以中断调试器、执行、继续和停止调试。</span><span class="sxs-lookup"><span data-stu-id="39ecc-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="39ecc-188">工作区调试</span><span class="sxs-lookup"><span data-stu-id="39ecc-188">Workspace debugging</span></span>

<span data-ttu-id="39ecc-189">工作区调试是指文件夹上下文中的调试，该文件夹是在 Visual Studio Code 中从“文件”  菜单使用“打开文件夹...”  打开的。打开的文件夹通常是 PowerShell 项目文件夹和/或 Git 存储库的根文件夹。</span><span class="sxs-lookup"><span data-stu-id="39ecc-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="39ecc-190">即使在此模式下，按 <kbd>F5</kbd> 也可开始调试当前所选的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="39ecc-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="39ecc-191">但是，通过工作区调试可以定义多个调试配置，而不是只调试当前打开的文件。</span><span class="sxs-lookup"><span data-stu-id="39ecc-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="39ecc-192">例如，可通过添加配置执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="39ecc-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="39ecc-193">在调试器中启动 Pester 测试。</span><span class="sxs-lookup"><span data-stu-id="39ecc-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="39ecc-194">使用调试器中的参数启动特定文件。</span><span class="sxs-lookup"><span data-stu-id="39ecc-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="39ecc-195">在调试器中启动交互会话。</span><span class="sxs-lookup"><span data-stu-id="39ecc-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="39ecc-196">将调试器附加到 PowerShell 主机进程。</span><span class="sxs-lookup"><span data-stu-id="39ecc-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="39ecc-197">按照以下步骤创建调试配置文件：</span><span class="sxs-lookup"><span data-stu-id="39ecc-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="39ecc-198">通过按 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>，在 Windows 或 Linux 上打开“调试”  视图。</span><span class="sxs-lookup"><span data-stu-id="39ecc-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="39ecc-199">在 macOS 上，按 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>。</span><span class="sxs-lookup"><span data-stu-id="39ecc-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="39ecc-200">单击工具栏中的“配置”齿轮图标  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="39ecc-201">VSCode 将提示“选择环境”  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="39ecc-202">选择“PowerShell”  。</span><span class="sxs-lookup"><span data-stu-id="39ecc-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="39ecc-203">结果是，VSCode 会在工作区文件夹的根目录中创建一个目录和一个 `.vscode\launch.json` 文件。</span><span class="sxs-lookup"><span data-stu-id="39ecc-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="39ecc-204">这是调试配置的存储位置。</span><span class="sxs-lookup"><span data-stu-id="39ecc-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="39ecc-205">如果文件位于 Git 存储库中，则通常需要提交 `launch.json` 文件。</span><span class="sxs-lookup"><span data-stu-id="39ecc-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="39ecc-206">`launch.json` 文件的内容为：</span><span class="sxs-lookup"><span data-stu-id="39ecc-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="39ecc-207">此文件表示常见调试方案。</span><span class="sxs-lookup"><span data-stu-id="39ecc-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="39ecc-208">在编辑器中打开此文件时，会显示“添加配置...”  按钮。</span><span class="sxs-lookup"><span data-stu-id="39ecc-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="39ecc-209">单击此按钮可添加更多 PowerShell 调试配置。</span><span class="sxs-lookup"><span data-stu-id="39ecc-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="39ecc-210">其中可添加的一个有用配置是“PowerShell:**Launch Script**。</span><span class="sxs-lookup"><span data-stu-id="39ecc-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="39ecc-211">通过此配置，可以使用可选参数指定文件，无论编辑器中哪个文件当前处于活动状态，无论何时按 <kbd>F5</kbd>，此文件都会启动。</span><span class="sxs-lookup"><span data-stu-id="39ecc-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="39ecc-212">建立调试配置后，可以选择要在调试会话期间使用的配置。</span><span class="sxs-lookup"><span data-stu-id="39ecc-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="39ecc-213">从“调试”  视图工具栏的调试配置下拉菜单中选择配置。</span><span class="sxs-lookup"><span data-stu-id="39ecc-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="39ecc-214">以下博客提供有关将 PowerShell 扩展用于 Visual Studio Code 的有用入门帮助：</span><span class="sxs-lookup"><span data-stu-id="39ecc-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="39ecc-215">[PowerShell 扩展][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="39ecc-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="39ecc-216">[在 Visual Studio Code 中编写和调试 PowerShell 脚本][debug]</span><span class="sxs-lookup"><span data-stu-id="39ecc-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="39ecc-217">[Visual Studio Code 调试指南][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="39ecc-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="39ecc-218">[在 Visual Studio Code 中调试 PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="39ecc-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="39ecc-219">[Visual Studio Code 中的 PowerShell 开发入门][getting-started]</span><span class="sxs-lookup"><span data-stu-id="39ecc-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="39ecc-220">[面向 PowerShell 开发的 Visual Studio Code 编辑功能 - 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="39ecc-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="39ecc-221">[面向 PowerShell 开发的 Visual Studio Code 编辑功能 - 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="39ecc-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="39ecc-222">[在 Visual Studio Code 中调试 PowerShell 脚本 - 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="39ecc-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="39ecc-223">[在 Visual Studio Code 中调试 PowerShell 脚本 - 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="39ecc-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="39ecc-224">适用于 VSCode 的 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="39ecc-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="39ecc-225">可以在 [GitHub](https://github.com/PowerShell/vscode-powershell) 上找到 PowerShell 扩展的源代码。</span><span class="sxs-lookup"><span data-stu-id="39ecc-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
