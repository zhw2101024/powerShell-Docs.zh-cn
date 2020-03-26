---
title: 使用 Visual Studio Code 进行 PowerShell 开发
description: 使用 Visual Studio Code 进行 PowerShell 开发
ms.date: 11/07/2019
ms.openlocfilehash: 86739970b58460bef9686a75bf0604d0605d4888
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082440"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="53adb-103">使用 Visual Studio Code 进行 PowerShell 开发</span><span class="sxs-lookup"><span data-stu-id="53adb-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="53adb-104">[Visual Studio Code](https://code.visualstudio.com/) 是 Microsoft 开发的跨平台（Windows、macOS 和 Linux）脚本编辑器。</span><span class="sxs-lookup"><span data-stu-id="53adb-104">[Visual Studio Code](https://code.visualstudio.com/) is a cross-platform (Windows, macOS, and Linux) script editor by Microsoft.</span></span> <span data-ttu-id="53adb-105">与 [PowerShell 扩展](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell) 相结合，它提供了丰富的交互式脚本编辑体验，从而可以更轻松地编写可靠的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="53adb-105">Together with the [the PowerShell extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span>

<span data-ttu-id="53adb-106">建议使用带有 PowerShell 扩展的 Visual Studio Code 编辑器来编写 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="53adb-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>
<span data-ttu-id="53adb-107">它支持以下 PowerShell 版本：</span><span class="sxs-lookup"><span data-stu-id="53adb-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="53adb-108">PowerShell 7 及更高版本</span><span class="sxs-lookup"><span data-stu-id="53adb-108">PowerShell 7 and up</span></span>
- <span data-ttu-id="53adb-109">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="53adb-109">PowerShell Core 6</span></span>
- <span data-ttu-id="53adb-110">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="53adb-110">Windows PowerShell 5.1</span></span>

<span data-ttu-id="53adb-111">开始前，请确保系统上安装有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="53adb-111">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="53adb-112">有关 Windows、macOS 和 Linux 上的新式工作负荷，请参阅以下链接：</span><span class="sxs-lookup"><span data-stu-id="53adb-112">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="53adb-113">[在 Linux 上安装 PowerShell Core][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="53adb-113">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="53adb-114">[在 macOS 上安装 PowerShell Core][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="53adb-114">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="53adb-115">[在 Windows 上安装 PowerShell Core][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="53adb-115">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="53adb-116">有关传统 Windows PowerShell 工作负载，请参阅[安装 Windows PowerShell][install-winps]。</span><span class="sxs-lookup"><span data-stu-id="53adb-116">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!NOTE]
> <span data-ttu-id="53adb-117">Visual Studio Code 与 [Visual Studio](https://visualstudio.microsoft.com/) 不同。</span><span class="sxs-lookup"><span data-stu-id="53adb-117">Visual Studio Code is not the same as [Visual Studio](https://visualstudio.microsoft.com/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53adb-118">[Windows PowerShell ISE][ise] 仍可用于 Windows，但是，它不再处于活动功能开发状态，并且不适用于 PowerShell 7 及更高版本或 PowerShell Core 6。</span><span class="sxs-lookup"><span data-stu-id="53adb-118">The [Windows PowerShell ISE][ise] is also still available for Windows, however, it is no longer in active feature development and does not work with PowerShell 7 and up or PowerShell Core 6.</span></span>
> <span data-ttu-id="53adb-119">作为 Windows 的随附组件，它仍会获得安全性和高优先级服务修补程序的官方支持。</span><span class="sxs-lookup"><span data-stu-id="53adb-119">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span> <span data-ttu-id="53adb-120">目前没有从 Windows 中删除 ISE 的计划。</span><span class="sxs-lookup"><span data-stu-id="53adb-120">We currently have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="53adb-121">使用 Visual Studio Code 进行编辑</span><span class="sxs-lookup"><span data-stu-id="53adb-121">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="53adb-122">安装 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="53adb-122">Install Visual Studio Code.</span></span> <span data-ttu-id="53adb-123">有关详细信息，请参阅[设置 Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview) 概述。</span><span class="sxs-lookup"><span data-stu-id="53adb-123">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

    <span data-ttu-id="53adb-124">每个平台都有安装说明：</span><span class="sxs-lookup"><span data-stu-id="53adb-124">There are installation instructions for each platform:</span></span>

    - <span data-ttu-id="53adb-125">**Windows**：按照[在 Windows 上运行 Visual Studio Code](https://code.visualstudio.com/docs/setup/windows) 页面上的安装说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="53adb-125">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>
    - <span data-ttu-id="53adb-126">**macOS**：请按照[在 macOS 上运行 Visual Studio Code](https://code.visualstudio.com/docs/setup/mac) 页面上的安装说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="53adb-126">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>
    - <span data-ttu-id="53adb-127">**Linux**：请按照[在 Linux 上运行 Visual Studio Code](https://code.visualstudio.com/docs/setup/linux) 页面上的安装说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="53adb-127">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>

1. <span data-ttu-id="53adb-128">安装 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="53adb-128">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="53adb-129">通过在控制台中键入 `code` 或键入`code-insiders`（在安装 Visual Studio Code 预览体验成员的情况下）来启动 Visual Studio Code 应用。</span><span class="sxs-lookup"><span data-stu-id="53adb-129">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="53adb-130">通过按 <kbd>Ctrl</kbd>+<kbd>P</kbd>，在 Windows 或 Linux 上启动“Quick Open”。</span><span class="sxs-lookup"><span data-stu-id="53adb-130">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="53adb-131">在 macOS 上，按 <kbd>Cmd</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="53adb-131">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="53adb-132">在“Quick Open”中，键入 `ext install powershell`，然后按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="53adb-132">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="53adb-133">“扩展”视图随即在侧边栏上打开。</span><span class="sxs-lookup"><span data-stu-id="53adb-133">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="53adb-134">从 Microsoft 中选择 PowerShell 扩展。</span><span class="sxs-lookup"><span data-stu-id="53adb-134">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="53adb-135">应会看到类似于下图的 Visual Studio Code 屏幕：</span><span class="sxs-lookup"><span data-stu-id="53adb-135">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="53adb-137">在 Microsoft 下单击 PowerShell 扩展上的“安装”按钮。</span><span class="sxs-lookup"><span data-stu-id="53adb-137">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="53adb-138">安装后，如果看到“安装”按钮变为“重载”，则单击“重载”。</span><span class="sxs-lookup"><span data-stu-id="53adb-138">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="53adb-139">重载 Visual Studio Code 后即可开始编辑。</span><span class="sxs-lookup"><span data-stu-id="53adb-139">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="53adb-140">例如，若要创建新文件，请单击“文件”>“新建”。</span><span class="sxs-lookup"><span data-stu-id="53adb-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="53adb-141">若要保存，请单击“文件”>“保存”，然后提供文件名，例如 `HelloWorld.ps1`。</span><span class="sxs-lookup"><span data-stu-id="53adb-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="53adb-142">若要关闭文件，请单击文件名旁的 `X`。</span><span class="sxs-lookup"><span data-stu-id="53adb-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="53adb-143">若要退出 Visual Studio Code，请单击“文件”>“退出”。</span><span class="sxs-lookup"><span data-stu-id="53adb-143">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="53adb-144">在受限制的系统上安装 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="53adb-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="53adb-145">有些系统的设置要求检查所有代码签名，且需要手动批准 PowerShell 编辑器服务才能在系统上运行。</span><span class="sxs-lookup"><span data-stu-id="53adb-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="53adb-146">如果已经安装 PowerShell 扩展，但出现以下错误，那么更改执行策略的组策略更新可能是原因之一：</span><span class="sxs-lookup"><span data-stu-id="53adb-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="53adb-147">若要手动批准 PowerShell 编辑器服务和适用于 Visual Studio Code 的 PowerShell 扩展，则打开 PowerShell 提示符并运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="53adb-147">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="53adb-148">系统会提示你“是否要运行来自此不可信发布者的软件？”</span><span class="sxs-lookup"><span data-stu-id="53adb-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span>
<span data-ttu-id="53adb-149">键入 `A` 以运行该文件。</span><span class="sxs-lookup"><span data-stu-id="53adb-149">Type `A` to run the file.</span></span> <span data-ttu-id="53adb-150">然后打开 Visual Studio Code，并检查 PowerShell 扩展是否工作正常。</span><span class="sxs-lookup"><span data-stu-id="53adb-150">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="53adb-151">如果在开始使用时仍有问题，请在 [GitHub](https://github.com/PowerShell/vscode-powershell/issues) 上告诉我们。</span><span class="sxs-lookup"><span data-stu-id="53adb-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="53adb-152">适用于 Visual Studio Code 的 PowerShell 扩展不支持在约束语言模式下运行。</span><span class="sxs-lookup"><span data-stu-id="53adb-152">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="53adb-153">有关详细信息，请参阅[支持的 GitHub 问题跟踪](https://github.com/PowerShell/vscode-powershell/issues/606)。</span><span class="sxs-lookup"><span data-stu-id="53adb-153">Please see the [GitHub issue tracking that support](https://github.com/PowerShell/vscode-powershell/issues/606) for more information.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="53adb-154">对 Windows PowerShell v3 和 v4 使用旧版 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="53adb-154">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="53adb-155">尽管当前的 PowerShell 扩展[已停止支持 v3 和 v4](https://github.com/PowerShell/vscode-powershell/issues/1310)，但仍可以使用该扩展的最新版本。</span><span class="sxs-lookup"><span data-stu-id="53adb-155">Although the current PowerShell extension [stopped supporting v3 and v4](https://github.com/PowerShell/vscode-powershell/issues/1310), you can still use the last version of the extension that did.</span></span>

> [!NOTE]
> <span data-ttu-id="53adb-156">将不会为此扩展的较旧版本提供其他修补程序。</span><span class="sxs-lookup"><span data-stu-id="53adb-156">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="53adb-157">它“按原样”提供，但如果你仍在使用 Windows PowerShell v3 和 Windows PowerShell v4，则可以使用它。</span><span class="sxs-lookup"><span data-stu-id="53adb-157">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="53adb-158">首先，打开“扩展”窗格并搜索 `PowerShell`。</span><span class="sxs-lookup"><span data-stu-id="53adb-158">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="53adb-159">然后单击齿轮，选择“安装其他版本...”。</span><span class="sxs-lookup"><span data-stu-id="53adb-159">Then click the gear and select **Install another version...**.</span></span>

![安装其他版本...](media/using-vscode/install-another-version.png)

<span data-ttu-id="53adb-161">然后选择“`2020.1.0`”版本。</span><span class="sxs-lookup"><span data-stu-id="53adb-161">Then select the **`2020.1.0`** version.</span></span> <span data-ttu-id="53adb-162">此版本的扩展是支持 v3 和 v4 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="53adb-162">This version of the extension was the last version to support v3 and v4.</span></span>

<span data-ttu-id="53adb-163">另外，添加以下设置，以便不会自动更新扩展版本：</span><span class="sxs-lookup"><span data-stu-id="53adb-163">Also, add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="53adb-164">尽管这在可预见的将来是可行的，但是 Visual Studio Code 可以实现一个中断此扩展版本的更改。</span><span class="sxs-lookup"><span data-stu-id="53adb-164">Although this will work in the forseeable future, Visual Studio Code could implement a change that breaks this version of the extension.</span></span>
<span data-ttu-id="53adb-165">因此，由于缺乏支持，我们强烈建议执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="53adb-165">Because of this, and lack of support, we highly recommend either:</span></span>

- <span data-ttu-id="53adb-166">下载 PowerShell 7 - 这是 Windows PowerShell 的并行安装，与 PowerShell 扩展配合使用效果最佳</span><span class="sxs-lookup"><span data-stu-id="53adb-166">Downloading PowerShell 7 - which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>
- <span data-ttu-id="53adb-167">升级到 Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="53adb-167">Upgrading to Windows PowerShell 5.1</span></span>

<span data-ttu-id="53adb-168">本文中的[使用 Visual Studio Code 编辑](#editing-with-visual-studio-code)部分会链接到安装它们的位置。</span><span class="sxs-lookup"><span data-stu-id="53adb-168">The [Editing with Visual Studio Code](#editing-with-visual-studio-code) section in this article links to where to install these.</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="53adb-169">选择要与扩展一起使用的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="53adb-169">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="53adb-170">将 PowerShell Core 与 Windows PowerShell 并行安装后，现在可以将特定版本的 PowerShell 与 PowerShell 扩展一起使用。</span><span class="sxs-lookup"><span data-stu-id="53adb-170">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="53adb-171">使用以下步骤选择版本：</span><span class="sxs-lookup"><span data-stu-id="53adb-171">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="53adb-172">在 Windows 或 Linux 上，使用 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 打开“命令面板”。</span><span class="sxs-lookup"><span data-stu-id="53adb-172">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="53adb-173">在 macOS 上，使用 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>。</span><span class="sxs-lookup"><span data-stu-id="53adb-173">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="53adb-174">搜索“会话”。</span><span class="sxs-lookup"><span data-stu-id="53adb-174">Search for **Session**.</span></span>
1. <span data-ttu-id="53adb-175">单击“PowerShell:显示会话菜单”。</span><span class="sxs-lookup"><span data-stu-id="53adb-175">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="53adb-176">选择要从列表中使用的 PowerShell 版本，例如：PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="53adb-176">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53adb-177">此功能通过不同操作系统上的几个已知路径来发现 PowerShell 的安装位置。</span><span class="sxs-lookup"><span data-stu-id="53adb-177">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="53adb-178">如果已将 PowerShell 安装到非典型位置，则最初可能不会显示在会话菜单中。</span><span class="sxs-lookup"><span data-stu-id="53adb-178">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="53adb-179">可以按如下所述[添加你自己的自定义路径](#adding-your-own-powershell-paths-to-the-session-menu)来扩展会话菜单。</span><span class="sxs-lookup"><span data-stu-id="53adb-179">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="53adb-180">还有一种方法可以获取会话菜单。</span><span class="sxs-lookup"><span data-stu-id="53adb-180">There's another way to get to the session menu.</span></span> <span data-ttu-id="53adb-181">当 PowerShell 文件在编辑器中打开时，你会看到右下角的绿色版本号。</span><span class="sxs-lookup"><span data-stu-id="53adb-181">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="53adb-182">单击此版本号将为你提供会话菜单。</span><span class="sxs-lookup"><span data-stu-id="53adb-182">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="53adb-183">将你自己的 PowerShell 路径添加到会话菜单</span><span class="sxs-lookup"><span data-stu-id="53adb-183">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="53adb-184">可以通过 [Visual Studio Code 设置](https://code.visualstudio.com/docs/getstarted/settings)将其他 PowerShell 可执行文件路径添加到会话菜单：`powershell.powerShellAdditionalExePaths`。</span><span class="sxs-lookup"><span data-stu-id="53adb-184">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="53adb-185">向列表 `powershell.powerShellAdditionalExePaths` 添加项或创建该列表（如果它不存在于 `settings.json` 中）：</span><span class="sxs-lookup"><span data-stu-id="53adb-185">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="53adb-186">每个项必须具有：</span><span class="sxs-lookup"><span data-stu-id="53adb-186">Each item must have:</span></span>

- <span data-ttu-id="53adb-187">`exePath`设置用户帐户 ：`pwsh` 或 `powershell` 可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="53adb-187">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="53adb-188">`versionName`设置用户帐户 ：将显示在会话菜单中的文本。</span><span class="sxs-lookup"><span data-stu-id="53adb-188">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="53adb-189">可以将默认 PowerShell 版本设置为使用 `powershell.powerShellDefaultVersion` 设置，方法是将其设置为显示在会话菜单中的文本（也是最后一个设置中的 `versionName`）：</span><span class="sxs-lookup"><span data-stu-id="53adb-189">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="53adb-190">配置此设置后，请重启 Visual Studio Code 或从“命令面板”中重载当前 Visual Studio Code 窗口，键入“开发人员:重载窗口”。</span><span class="sxs-lookup"><span data-stu-id="53adb-190">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="53adb-191">如果打开会话菜单，你现在会看到其他 PowerShell 版本！</span><span class="sxs-lookup"><span data-stu-id="53adb-191">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="53adb-192">如果从源生成 PowerShell，则这是测试 PowerShell 的本地生成的好办法。</span><span class="sxs-lookup"><span data-stu-id="53adb-192">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="53adb-193">Visual Studio Code 的配置设置</span><span class="sxs-lookup"><span data-stu-id="53adb-193">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="53adb-194">首先，如果不熟悉如何更改 Visual Studio Code 中的设置，建议查看 [Visual Studio Code 的设置文档](https://code.visualstudio.com/docs/getstarted/settings)。</span><span class="sxs-lookup"><span data-stu-id="53adb-194">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend looking at [Visual Studio Code's settings documentation](https://code.visualstudio.com/docs/getstarted/settings).</span></span>

<span data-ttu-id="53adb-195">按照上一段落中的步骤可在 `settings.json` 中添加配置设置。</span><span class="sxs-lookup"><span data-stu-id="53adb-195">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="53adb-196">如果不希望这些设置影响所有文件类型，则 Visual Studio Code 还允许按语言进行配置。</span><span class="sxs-lookup"><span data-stu-id="53adb-196">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="53adb-197">创建在 `[<language-name>]` 字段中放置设置，可以配置特定于语言的设置。</span><span class="sxs-lookup"><span data-stu-id="53adb-197">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="53adb-198">例如：</span><span class="sxs-lookup"><span data-stu-id="53adb-198">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="53adb-199">有关 Visual Studio Code 中文件编码的详细信息，请参阅[了解文件编码](understanding-file-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="53adb-199">For more information about file encoding in Visual Studio Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>
>
> <span data-ttu-id="53adb-200">另外，请查看[如何在 Visual Studio Code 中复制 ISE 体验](How-To-Replicate-the-ISE-Experience-In-VSCode.md)，以获取有关如何配置 Visual Studio Code 以进行 PowerShell 编辑的其他提示。</span><span class="sxs-lookup"><span data-stu-id="53adb-200">Also check out the [How to replicate the ISE experience in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="53adb-201">使用 Visual Studio Code 进行调试</span><span class="sxs-lookup"><span data-stu-id="53adb-201">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="53adb-202">无工作区调试</span><span class="sxs-lookup"><span data-stu-id="53adb-202">No-workspace debugging</span></span>

<span data-ttu-id="53adb-203">从 Visual Studio Code 版本 1.9 开始，无需打开包含 PowerShell 脚本的文件夹即可调试 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="53adb-203">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="53adb-204">单击“文件”>“打开文件...”来打开 PowerShell 脚本文件，在行上设一个断点，按 <kbd>F9</kbd>，然后按 <kbd>F5</kbd> 即可开始调试。</span><span class="sxs-lookup"><span data-stu-id="53adb-204">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="53adb-205">此时应出现“调试”操作窗格，通过该窗格可以中断调试器、执行、继续和停止调试。</span><span class="sxs-lookup"><span data-stu-id="53adb-205">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="53adb-206">工作区调试</span><span class="sxs-lookup"><span data-stu-id="53adb-206">Workspace debugging</span></span>

<span data-ttu-id="53adb-207">工作区调试是指文件夹上下文中的调试，该文件夹是在 Visual Studio Code 中从“文件”菜单使用“打开文件夹...”打开的。打开的文件夹通常是 PowerShell 项目文件夹和/或 Git 存储库的根文件夹。</span><span class="sxs-lookup"><span data-stu-id="53adb-207">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="53adb-208">即使在此模式下，按 <kbd>F5</kbd> 也可开始调试当前所选的 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="53adb-208">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="53adb-209">但是，通过工作区调试可以定义多个调试配置，而不是只调试当前打开的文件。</span><span class="sxs-lookup"><span data-stu-id="53adb-209">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="53adb-210">稍后我们将对这些进行介绍。</span><span class="sxs-lookup"><span data-stu-id="53adb-210">We'll get to those in a moment.</span></span>

<span data-ttu-id="53adb-211">按照以下步骤创建调试配置文件：</span><span class="sxs-lookup"><span data-stu-id="53adb-211">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="53adb-212">通过按 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>，在 Windows 或 Linux 上打开“调试”视图。</span><span class="sxs-lookup"><span data-stu-id="53adb-212">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="53adb-213">在 macOS 上，按 <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>。</span><span class="sxs-lookup"><span data-stu-id="53adb-213">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="53adb-214">单击“创建 launch.json 文件”链接。</span><span class="sxs-lookup"><span data-stu-id="53adb-214">Click the "create a launch.json file" link.</span></span>
  1. <span data-ttu-id="53adb-215">Visual Studio Code 将提示“选择环境”。</span><span class="sxs-lookup"><span data-stu-id="53adb-215">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="53adb-216">选择“PowerShell”。</span><span class="sxs-lookup"><span data-stu-id="53adb-216">Choose **PowerShell**.</span></span>
  1. <span data-ttu-id="53adb-217">最后，选择要使用的调试类型：</span><span class="sxs-lookup"><span data-stu-id="53adb-217">Lastly, choose the type of debugging you'd like to use:</span></span>

- <span data-ttu-id="53adb-218">**启动当前文件** - 在当前活动的编辑器窗口中启动和调试文件</span><span class="sxs-lookup"><span data-stu-id="53adb-218">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
- <span data-ttu-id="53adb-219">**启动脚本** - 启动和调试指定的文件或命令</span><span class="sxs-lookup"><span data-stu-id="53adb-219">**Launch Script** - Launch and debug the specified file or command</span></span>
- <span data-ttu-id="53adb-220">**交互式会话** - 从集成控制台执行的调试命令</span><span class="sxs-lookup"><span data-stu-id="53adb-220">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
- <span data-ttu-id="53adb-221">**附加** - 将调试器附加到正在运行的 PowerShell 主机进程</span><span class="sxs-lookup"><span data-stu-id="53adb-221">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="53adb-222">结果是，Visual Studio Code 会在工作区文件夹的根目录中创建一个目录和一个 `.vscode\launch.json` 文件。</span><span class="sxs-lookup"><span data-stu-id="53adb-222">The result is that Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="53adb-223">这是调试配置的存储位置。</span><span class="sxs-lookup"><span data-stu-id="53adb-223">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="53adb-224">如果文件位于 Git 存储库中，则通常需要提交 `launch.json` 文件。</span><span class="sxs-lookup"><span data-stu-id="53adb-224">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="53adb-225">`launch.json` 文件的内容为：</span><span class="sxs-lookup"><span data-stu-id="53adb-225">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="53adb-226">此文件表示常见调试方案。</span><span class="sxs-lookup"><span data-stu-id="53adb-226">This file represents the common debug scenarios.</span></span> <span data-ttu-id="53adb-227">在编辑器中打开此文件时，会显示“添加配置...”按钮。</span><span class="sxs-lookup"><span data-stu-id="53adb-227">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="53adb-228">单击此按钮可添加更多 PowerShell 调试配置。</span><span class="sxs-lookup"><span data-stu-id="53adb-228">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="53adb-229">其中可添加的一个有用配置是“PowerShell:**Launch Script**。</span><span class="sxs-lookup"><span data-stu-id="53adb-229">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="53adb-230">通过此配置，可以使用可选参数指定文件，无论编辑器中哪个文件当前处于活动状态，无论何时按 <kbd>F5</kbd>，此文件都会启动。</span><span class="sxs-lookup"><span data-stu-id="53adb-230">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="53adb-231">建立调试配置后，可以选择要在调试会话期间使用的配置。</span><span class="sxs-lookup"><span data-stu-id="53adb-231">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="53adb-232">从“调试”视图工具栏的调试配置下拉菜单中选择配置。</span><span class="sxs-lookup"><span data-stu-id="53adb-232">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="53adb-233">以下博客提供有关将 PowerShell 扩展用于 Visual Studio Code 的有用入门帮助：</span><span class="sxs-lookup"><span data-stu-id="53adb-233">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="53adb-234">[PowerShell 扩展][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="53adb-234">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="53adb-235">[在 Visual Studio Code 中编写和调试 PowerShell 脚本][debug]</span><span class="sxs-lookup"><span data-stu-id="53adb-235">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="53adb-236">[Visual Studio Code 调试指南][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="53adb-236">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="53adb-237">[在 Visual Studio Code 中调试 PowerShell][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="53adb-237">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="53adb-238">[Visual Studio Code 中的 PowerShell 开发入门][getting-started]</span><span class="sxs-lookup"><span data-stu-id="53adb-238">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="53adb-239">[面向 PowerShell 开发的 Visual Studio Code 编辑功能 - 第 1 部分][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="53adb-239">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="53adb-240">[面向 PowerShell 开发的 Visual Studio Code 编辑功能 - 第 2 部分][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="53adb-240">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="53adb-241">[在 Visual Studio Code 中调试 PowerShell 脚本 - 第 1 部分][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="53adb-241">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="53adb-242">[在 Visual Studio Code 中调试 PowerShell 脚本 - 第 2 部分][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="53adb-242">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="53adb-243">适用于 Visual Studio Code 的 PowerShell 扩展</span><span class="sxs-lookup"><span data-stu-id="53adb-243">PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="53adb-244">可以在 [GitHub](https://github.com/PowerShell/vscode-powershell) 上找到 PowerShell 扩展的源代码。</span><span class="sxs-lookup"><span data-stu-id="53adb-244">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>

<span data-ttu-id="53adb-245">如果你有兴趣参与，将极大改进拉取请求。</span><span class="sxs-lookup"><span data-stu-id="53adb-245">If you're interested in contributing, Pull Request are greatly appreciated.</span></span> <span data-ttu-id="53adb-246">请遵循 [GitHub 上的开发人员文档](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md)来开始使用。</span><span class="sxs-lookup"><span data-stu-id="53adb-246">Follow along with the [developer documentation on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) to get started.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="53adb-247">适用于 Visual Studio Code 的 PowerShell 扩展故障排除</span><span class="sxs-lookup"><span data-stu-id="53adb-247">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="53adb-248">如果在使用 Visual Studio Code 进行 PowerShell 脚本开发时遇到任何问题，请查看 [GitHub 上的故障排除指南](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="53adb-248">If you experience any issues using Visual Studio Code for PowerShell script development, please take a look at the [troubleshooting guide on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span></span>
