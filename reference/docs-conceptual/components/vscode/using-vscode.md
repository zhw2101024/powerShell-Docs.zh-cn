---
title: 使用 Visual Studio Code 进行 PowerShell 开发
description: 使用 Visual Studio Code 进行 PowerShell 开发
ms.date: 08/06/2018
ms.openlocfilehash: 1e9b9d811a39656327af2810bd6dc8aaf3fde3a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086712"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="a0f91-103">使用 Visual Studio Code 进行 PowerShell 开发</span><span class="sxs-lookup"><span data-stu-id="a0f91-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="a0f91-104">除 [PowerShell ISE][ise] 外，PowerShell 还高度支持 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="a0f91-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="a0f91-105">此外，PowerShell Core 不支持 ISE，但是 Visual Studio Code 在所有平台上（Windows、macOS 和 Linux）均支持 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a0f91-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="a0f91-106">通过使用 Windows 10 或安装适用于低版本 Windows OS（例如 Windows 8.1 等）的 [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395)，可在 Windows 上结合使用 Visual Studio Code 和 PowerShell 版本 5.</span><span class="sxs-lookup"><span data-stu-id="a0f91-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="a0f91-107">开始前，请确保系统上安装有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a0f91-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="a0f91-108">有关 Windows、macOS 和 Linux 上的新式工作负荷，请参阅：</span><span class="sxs-lookup"><span data-stu-id="a0f91-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="a0f91-109">[在 Linux 上安装 PowerShell Core][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="a0f91-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="a0f91-110">[在 macOS 上安装 PowerShell Core][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="a0f91-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="a0f91-111">[在 Windows 上安装 PowerShell Core][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="a0f91-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="a0f91-112">有关传统 Windows PowerShell 工作负荷，请参阅[安装 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="a0f91-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="a0f91-113">使用 Visual Studio Code 进行编辑</span><span class="sxs-lookup"><span data-stu-id="a0f91-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="a0f91-114">1.安装 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a0f91-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="a0f91-115">**Linux**：请按照[在 Linux 上运行 VS Code](https://code.visualstudio.com/docs/setup/linux) 页面上的安装说明进行操作</span><span class="sxs-lookup"><span data-stu-id="a0f91-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="a0f91-116">**macOS**：请按照[在 macOS 上运行 VS Code](https://code.visualstudio.com/docs/setup/mac) 页面上的安装说明进行操作</span><span class="sxs-lookup"><span data-stu-id="a0f91-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="a0f91-117">在 macOS 上，必须安装 OpenSSL 后 PowerShell 扩展方可正常运行。</span><span class="sxs-lookup"><span data-stu-id="a0f91-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="a0f91-118">实现此要求的最简单方法是安装 [Homebrew](https://brew.sh/)，然后运行 `brew install openssl`。</span><span class="sxs-lookup"><span data-stu-id="a0f91-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="a0f91-119">VS Code 现可成功加载 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="a0f91-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="a0f91-120">**Windows**：按照[在 Windows 上运行 VS Code](https://code.visualstudio.com/docs/setup/windows) 页面上的安装说明进行操作</span><span class="sxs-lookup"><span data-stu-id="a0f91-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="a0f91-121">2.安装 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="a0f91-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="a0f91-122">按照如下方式启动 Visual Studio Code 应用：</span><span class="sxs-lookup"><span data-stu-id="a0f91-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="a0f91-123">**Windows**：在 PowerShell 会话中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="a0f91-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="a0f91-124">**Linux**：在终端中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="a0f91-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="a0f91-125">**macOS**：在终端中键入 `code`</span><span class="sxs-lookup"><span data-stu-id="a0f91-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="a0f91-126">通过按 Ctrl+P（Mac 上为 Cmd+P）启动“Quick Open”。</span><span class="sxs-lookup"><span data-stu-id="a0f91-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="a0f91-127">在“Quick Open”中，键入 `ext install powershell` 并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="a0f91-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="a0f91-128">“扩展”视图随即在侧边栏上打开。</span><span class="sxs-lookup"><span data-stu-id="a0f91-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="a0f91-129">从 Microsoft 中选择 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="a0f91-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="a0f91-130">应看到如下内容：</span><span class="sxs-lookup"><span data-stu-id="a0f91-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="a0f91-132">在 Microsoft 下单击 PowerShell 扩展上的“安装”按钮。</span><span class="sxs-lookup"><span data-stu-id="a0f91-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="a0f91-133">安装后，“安装”按钮将变为“重载”。</span><span class="sxs-lookup"><span data-stu-id="a0f91-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="a0f91-134">单击“重载”。</span><span class="sxs-lookup"><span data-stu-id="a0f91-134">Click on **Reload**.</span></span>
- <span data-ttu-id="a0f91-135">重载 Visual Studio Code 后即可开始编辑。</span><span class="sxs-lookup"><span data-stu-id="a0f91-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="a0f91-136">例如，若要创建新文件，请单击“文件”->“新建”。</span><span class="sxs-lookup"><span data-stu-id="a0f91-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="a0f91-137">若要保存，请单击“文件”->“保存”，然后提供一个文件名，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="a0f91-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="a0f91-138">若要关闭文件，则单击文件名旁的“x”。</span><span class="sxs-lookup"><span data-stu-id="a0f91-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="a0f91-139">若要退出 Visual Studio Code，请单击“文件”->“退出”。</span><span class="sxs-lookup"><span data-stu-id="a0f91-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="a0f91-140">在受限制的系统上安装 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="a0f91-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="a0f91-141">有些系统的设置要求检查所有代码签名，因此需要手动批准 PowerShell 编辑器服务才能在系统上运行。</span><span class="sxs-lookup"><span data-stu-id="a0f91-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="a0f91-142">如果已经安装 PowerShell 扩展，但出现以下错误，那么更改执行策略的组策略更新可能是原因之一：</span><span class="sxs-lookup"><span data-stu-id="a0f91-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="a0f91-143">若要手动批准 PowerShell 编辑器服务，则适用于 VSCode 的 PowerShell 扩展打开 PowerShell 提示符并运行：</span><span class="sxs-lookup"><span data-stu-id="a0f91-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="a0f91-144">系统会提示你“是否要运行来自此不可信发布者的软件？”</span><span class="sxs-lookup"><span data-stu-id="a0f91-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="a0f91-145">键入 `R` 以运行该文件。</span><span class="sxs-lookup"><span data-stu-id="a0f91-145">Type `R` to run the file.</span></span> <span data-ttu-id="a0f91-146">然后打开 Visual Studio Code，并检查 PowerShell 扩展是否工作正常。</span><span class="sxs-lookup"><span data-stu-id="a0f91-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="a0f91-147">如果在开始使用时仍有问题，请在 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) 上告诉我们。</span><span class="sxs-lookup"><span data-stu-id="a0f91-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="a0f91-148">使用 PowerShell 特定安装版</span><span class="sxs-lookup"><span data-stu-id="a0f91-148">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="a0f91-149">如果要通过 Visual Studio Code 使用 PowerShell 的特定安装版，则需要将新的变量添加到用户设置文件。</span><span class="sxs-lookup"><span data-stu-id="a0f91-149">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="a0f91-150">单击“文件”->“首选项”->“设置”</span><span class="sxs-lookup"><span data-stu-id="a0f91-150">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="a0f91-151">此时会出现两个编辑器窗格。</span><span class="sxs-lookup"><span data-stu-id="a0f91-151">Two editor panes appear.</span></span>
   <span data-ttu-id="a0f91-152">在最右侧窗格 (`settings.json`) 中，在两个花括号（`{` 和 `}`）之间的某处插入下面的 OS 对应设置，并将 \<版本\> 替换为已安装的 PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="a0f91-152">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="a0f91-153">将设置替换为所需 PowerShell 可执行文件的路径</span><span class="sxs-lookup"><span data-stu-id="a0f91-153">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="a0f91-154">保存设置文件并重启 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a0f91-154">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="a0f91-155">Visual Studio Code 的配置设置</span><span class="sxs-lookup"><span data-stu-id="a0f91-155">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="a0f91-156">按照上一段落中的步骤可在 `settings.json` 中添加配置设置。</span><span class="sxs-lookup"><span data-stu-id="a0f91-156">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="a0f91-157">我们建议对 Visual Studio Code 添加以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="a0f91-157">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="a0f91-158">如果不希望这些设置影响所有文件类型，则 VSCode 还允许按语言进行配置。</span><span class="sxs-lookup"><span data-stu-id="a0f91-158">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="a0f91-159">通过将设置置于 `[<language-name>]` 字段，创建语言特定的设置。</span><span class="sxs-lookup"><span data-stu-id="a0f91-159">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="a0f91-160">例如：</span><span class="sxs-lookup"><span data-stu-id="a0f91-160">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="a0f91-161">有关 VS Code 中文件编码的详细信息，请参阅[了解文件编码](understanding-file-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="a0f91-161">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="a0f91-162">使用 Visual Studio Code 进行调试</span><span class="sxs-lookup"><span data-stu-id="a0f91-162">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="a0f91-163">无工作区调试</span><span class="sxs-lookup"><span data-stu-id="a0f91-163">No-workspace debugging</span></span>

<span data-ttu-id="a0f91-164">从 Visual Studio Code 版本 1.9 开始，无需打开包含 PowerShell 脚本的文件夹即可调试 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="a0f91-164">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="a0f91-165">单击“文件”->“打开文件...”打开 PowerShell 脚本文件，在行上设一个断点（按 F9），然后按 F5 即可开始调试。</span><span class="sxs-lookup"><span data-stu-id="a0f91-165">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="a0f91-166">此时应出现“调试”操作窗格，通过该窗格可以中断调试器、执行、继续和停止调试。</span><span class="sxs-lookup"><span data-stu-id="a0f91-166">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="a0f91-167">工作区调试</span><span class="sxs-lookup"><span data-stu-id="a0f91-167">Workspace debugging</span></span>

<span data-ttu-id="a0f91-168">工作区调试是指文件夹上下文中的调试，该文件夹是使用“文件”菜单的“打开文件夹...”在 Visual Studio Code 中打开的。</span><span class="sxs-lookup"><span data-stu-id="a0f91-168">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="a0f91-169">打开的文件夹通常是 PowerShell 项目文件夹和/或 Git 存储库的根文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0f91-169">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="a0f91-170">即使在此模式下，按 F5 也可开始调试当前所选的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="a0f91-170">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="a0f91-171">但是，通过工作区调试可以定义多个调试配置，而不是只调试当前打开的文件。</span><span class="sxs-lookup"><span data-stu-id="a0f91-171">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="a0f91-172">例如，可通过添加配置执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a0f91-172">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="a0f91-173">在调试器中启动 Pester 测试</span><span class="sxs-lookup"><span data-stu-id="a0f91-173">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="a0f91-174">使用调试器中的参数启动特定文件</span><span class="sxs-lookup"><span data-stu-id="a0f91-174">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="a0f91-175">在调试器中启动交互会话</span><span class="sxs-lookup"><span data-stu-id="a0f91-175">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="a0f91-176">将调试器附加到 PowerShell 主机进程</span><span class="sxs-lookup"><span data-stu-id="a0f91-176">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="a0f91-177">按照以下步骤创建调试配置文件：</span><span class="sxs-lookup"><span data-stu-id="a0f91-177">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="a0f91-178">按 Ctrl+Shift+D（Mac 上为 Cmd+Shift+D）打开“调试”视图。</span><span class="sxs-lookup"><span data-stu-id="a0f91-178">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="a0f91-179">按工具栏中的“配置”齿轮图标。</span><span class="sxs-lookup"><span data-stu-id="a0f91-179">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="a0f91-180">Visual Studio Code 将提示“选择环境”。</span><span class="sxs-lookup"><span data-stu-id="a0f91-180">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="a0f91-181">选择“PowerShell”。</span><span class="sxs-lookup"><span data-stu-id="a0f91-181">Choose **PowerShell**.</span></span>

  <span data-ttu-id="a0f91-182">执行此操作时，Visual Studio Code 会在工作区文件夹的根中创建一个目录和一个“.vscode\launch.json”文件。</span><span class="sxs-lookup"><span data-stu-id="a0f91-182">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="a0f91-183">这是调试配置的存储位置。</span><span class="sxs-lookup"><span data-stu-id="a0f91-183">This is where your debug configuration is stored.</span></span> <span data-ttu-id="a0f91-184">如果文件位于 Git 存储库中，则通常需要提交 launch.json 文件。</span><span class="sxs-lookup"><span data-stu-id="a0f91-184">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="a0f91-185">launch.json 文件的内容为：</span><span class="sxs-lookup"><span data-stu-id="a0f91-185">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="a0f91-186">这表示常见调试方案。</span><span class="sxs-lookup"><span data-stu-id="a0f91-186">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="a0f91-187">但是，在编辑器中打开此文件时，会显示“添加配置...”按钮。</span><span class="sxs-lookup"><span data-stu-id="a0f91-187">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="a0f91-188">按此按钮可添加更多 PowerShell 调试配置。</span><span class="sxs-lookup"><span data-stu-id="a0f91-188">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="a0f91-189">其中可添加的一个便捷配置是“PowerShell:**Launch Script**。</span><span class="sxs-lookup"><span data-stu-id="a0f91-189">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="a0f91-190">通过此配置，可以使用可选参数指定特定文件，无论编辑器中哪个文件处于活动状态，无论何时按 F5 时，此文件都会启动。</span><span class="sxs-lookup"><span data-stu-id="a0f91-190">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="a0f91-191">调试配置建立后，可以在“调试”视图工具栏中的调试配置下拉列表中选择要在调试会话中使用的配置。</span><span class="sxs-lookup"><span data-stu-id="a0f91-191">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="a0f91-192">以下博客提供有关将 PowerShell 扩展用于 Visual Studio Code 的有用入门帮助：</span><span class="sxs-lookup"><span data-stu-id="a0f91-192">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="a0f91-193">[PowerShell 扩展插件][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="a0f91-193">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="a0f91-194">[在 Visual Studio Code 中编写和调试 PowerShell 脚本][debug]</span><span class="sxs-lookup"><span data-stu-id="a0f91-194">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="a0f91-195">[Visual Studio Code 调试指南][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="a0f91-195">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="a0f91-196">[在 Visual Studio Code 中调试 PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="a0f91-196">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="a0f91-197">[在 Visual Studio Code 中进行 PowerShell 开发][getting-started]</span><span class="sxs-lookup"><span data-stu-id="a0f91-197">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="a0f91-198">[适用于 PowerShell 开发的 Visual Studio Code 编辑功能 – 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="a0f91-198">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="a0f91-199">[适用于 PowerShell 开发的 Visual Studio Code 编辑功能 – 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="a0f91-199">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="a0f91-200">[在 Visual Studio Code 中调试 PowerShell 脚本 – 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="a0f91-200">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="a0f91-201">[在 Visual Studio Code 中调试 PowerShell 脚本 – 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="a0f91-201">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="a0f91-202">适用于 Visual Studio Code 的 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="a0f91-202">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="a0f91-203">可以在 [GitHub](https://github.com/PowerShell/vscode-powershell) 上找到 PowerShell 扩展的源代码。</span><span class="sxs-lookup"><span data-stu-id="a0f91-203">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
