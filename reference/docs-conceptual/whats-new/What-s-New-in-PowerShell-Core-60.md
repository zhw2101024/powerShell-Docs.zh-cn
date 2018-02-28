# <a name="whats-new-in-powershell-core-60"></a><span data-ttu-id="a3135-101">PowerShell Core 6.0 中的最近更新</span><span class="sxs-lookup"><span data-stu-id="a3135-101">What's New in PowerShell Core 6.0</span></span>

<span data-ttu-id="a3135-102">[PowerShell Core 6.0][github] 是为异类环境和混合云而构建的跨平台（Windows、macOS 和 Linux）且开源的新版 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a3135-102">[PowerShell Core 6.0][github] is a new edition of PowerShell that is cross-platform (Windows, macOS, and Linux), open-source, and built for heterogeneous environments and the hybrid cloud.</span></span>

## <a name="moved-from-net-framework-to-net-core"></a><span data-ttu-id="a3135-103">从 .NET Framework 移动到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="a3135-103">Moved from .NET Framework to .NET Core</span></span>

<span data-ttu-id="a3135-104">PowerShell Core 使用 [.NET Core 2.0][] 作为其运行时。</span><span class="sxs-lookup"><span data-stu-id="a3135-104">PowerShell Core uses [.NET Core 2.0][] as its runtime.</span></span>
<span data-ttu-id="a3135-105">.NET Core 2.0 支持 PowerShell Core 在多平台（Windows、macOS 和 Linux）上运行。</span><span class="sxs-lookup"><span data-stu-id="a3135-105">.NET Core 2.0 enables PowerShell Core to work on multiple platforms (Windows, macOS, and Linux).</span></span>
<span data-ttu-id="a3135-106">PowerShell Core 还公开 .NET Core 2.0 所提供以用于 PowerShell cmdlet 和脚本的 API 集合。</span><span class="sxs-lookup"><span data-stu-id="a3135-106">PowerShell Core also exposes the API set offered by .NET Core 2.0 to be used in PowerShell cmdlets and scripts.</span></span>

<span data-ttu-id="a3135-107">Windows PowerShell 使用 .NET Framework 运行时承载 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="a3135-107">Windows PowerShell used the .NET Framework runtime to host the PowerShell engine.</span></span>
<span data-ttu-id="a3135-108">这意味着 Windows PowerShell 公开由 .NET Framework 提供的 API 集。</span><span class="sxs-lookup"><span data-stu-id="a3135-108">This means that Windows PowerShell exposes the API set offered by .NET Framework.</span></span>

<span data-ttu-id="a3135-109">.NET Core 和 .NET Framework 之间共享的 API 定义为 [.NET Standard][] 的一部分。</span><span class="sxs-lookup"><span data-stu-id="a3135-109">The APIs shared between .NET Core and .NET Framework are defined as part of [.NET Standard][].</span></span>

<span data-ttu-id="a3135-110">有关这将如何影响 PowerShell Core 和 Windows PowerShell 之间模块/脚本兼容性的详细信息，请参阅 [Windows PowerShell 向后兼容性](#backwards-compatibility-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="a3135-110">For more information on how this affects module/script compatibility between PowerShell Core and Windows PowerShell, see [Backwards compatibility with Windows PowerShell](#backwards-compatibility-with-windows-powershell).</span></span>

## <a name="support-for-macos-and-linux"></a><span data-ttu-id="a3135-111">支持 macOS 和 Linux</span><span class="sxs-lookup"><span data-stu-id="a3135-111">Support for macOS and Linux</span></span>

<span data-ttu-id="a3135-112">PowerShell 现在官方支持 macOS 和 Linux，包括：</span><span class="sxs-lookup"><span data-stu-id="a3135-112">PowerShell now officially supports macOS and Linux, including:</span></span>

- <span data-ttu-id="a3135-113">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="a3135-113">Windows 7, 8.1, and 10</span></span>
- <span data-ttu-id="a3135-114">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="a3135-114">Windows Server 2008 R2, 2012 R2, 2016</span></span>
- <span data-ttu-id="a3135-115">[Windows Server 半年频道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="a3135-115">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
- <span data-ttu-id="a3135-116">Ubuntu 14.04、16.04 和 17.04</span><span class="sxs-lookup"><span data-stu-id="a3135-116">Ubuntu 14.04, 16.04, and 17.04</span></span>
- <span data-ttu-id="a3135-117">Debian 8.7+ 和 9</span><span class="sxs-lookup"><span data-stu-id="a3135-117">Debian 8.7+, and 9</span></span>
- <span data-ttu-id="a3135-118">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a3135-118">CentOS 7</span></span>
- <span data-ttu-id="a3135-119">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="a3135-119">Red Hat Enterprise Linux 7</span></span>
- <span data-ttu-id="a3135-120">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="a3135-120">OpenSUSE 42.2</span></span>
- <span data-ttu-id="a3135-121">Fedora 25、26</span><span class="sxs-lookup"><span data-stu-id="a3135-121">Fedora 25, 26</span></span>
- <span data-ttu-id="a3135-122">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="a3135-122">macOS 10.12+</span></span>

<span data-ttu-id="a3135-123">我们社区也为以下平台提供包，但是它们不受正式支持：</span><span class="sxs-lookup"><span data-stu-id="a3135-123">Our community has also contributed packages for the following platforms, but they are not officially supported:</span></span>

- <span data-ttu-id="a3135-124">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="a3135-124">Arch Linux</span></span>
- <span data-ttu-id="a3135-125">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="a3135-125">Kali Linux</span></span>
- <span data-ttu-id="a3135-126">AppImage（可在多个 Linux 平台上运行）</span><span class="sxs-lookup"><span data-stu-id="a3135-126">AppImage (works on multiple Linux platforms)</span></span>

<span data-ttu-id="a3135-127">我们还对以下平台提供试验版本（不受支持）：</span><span class="sxs-lookup"><span data-stu-id="a3135-127">We also have experimental (unsupported) releases for the following platforms:</span></span>

- <span data-ttu-id="a3135-128">ARM32/ARM64 上的 Windows</span><span class="sxs-lookup"><span data-stu-id="a3135-128">Windows on ARM32/ARM64</span></span>
- <span data-ttu-id="a3135-129">Raspbian (Stretch)</span><span class="sxs-lookup"><span data-stu-id="a3135-129">Raspbian (Stretch)</span></span>

<span data-ttu-id="a3135-130">为提高在非 Windows 系统上上的运行性能，已对 PowerShell Core 6.0 作出众多更改。</span><span class="sxs-lookup"><span data-stu-id="a3135-130">A number of changes were made to in PowerShell Core 6.0 to make it work better on non-Windows systems.</span></span>
<span data-ttu-id="a3135-131">其中一些是重大更改，这些更改也会影响 Windows。</span><span class="sxs-lookup"><span data-stu-id="a3135-131">Some of these are breaking changes, which also affect Windows.</span></span>
<span data-ttu-id="a3135-132">其他更改仅存在或适用于非 Windows 版的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a3135-132">Others are only present or applicable in non-Windows installations of PowerShell Core.</span></span>

- <span data-ttu-id="a3135-133">添加对 Unix 平台上本机命令通配的支持。</span><span class="sxs-lookup"><span data-stu-id="a3135-133">Added support for native command globbing on Unix platforms.</span></span>
- <span data-ttu-id="a3135-134">`more` 功能适用于 Linux `$PAGER` 并默认为 `less`。</span><span class="sxs-lookup"><span data-stu-id="a3135-134">The `more` functionality respects the Linux `$PAGER` and defaults to `less`.</span></span>
  <span data-ttu-id="a3135-135">这意味着现可将通配符用于本机二进制文件/命令（例如 `ls *.txt`）。</span><span class="sxs-lookup"><span data-stu-id="a3135-135">This means you can now use wildcards with native binaries/commands (for example, `ls *.txt`).</span></span> <span data-ttu-id="a3135-136">(#3463)</span><span class="sxs-lookup"><span data-stu-id="a3135-136">(#3463)</span></span>
- <span data-ttu-id="a3135-137">处理本机 命令参数时，尾部反斜杠将自动转义。</span><span class="sxs-lookup"><span data-stu-id="a3135-137">Trailing backslash is automatically escaped when dealing with native command arguments.</span></span> <span data-ttu-id="a3135-138">(#4965)</span><span class="sxs-lookup"><span data-stu-id="a3135-138">(#4965)</span></span>
- <span data-ttu-id="a3135-139">在非 Windows 平台上运行 PowerShell 时，请忽略 `-ExecutionPolicy` 切换，因为当前不支持脚本签名。</span><span class="sxs-lookup"><span data-stu-id="a3135-139">Ignore the `-ExecutionPolicy` switch when running PowerShell on non-Windows platforms because script signing is not currently supported.</span></span> <span data-ttu-id="a3135-140">(#3481)</span><span class="sxs-lookup"><span data-stu-id="a3135-140">(#3481)</span></span>
- <span data-ttu-id="a3135-141">已修复 ConsoleHost，以支持 Unix 平台上的 `NoEcho`。</span><span class="sxs-lookup"><span data-stu-id="a3135-141">Fixed ConsoleHost to honor `NoEcho` on Unix platforms.</span></span> <span data-ttu-id="a3135-142">(#3801)</span><span class="sxs-lookup"><span data-stu-id="a3135-142">(#3801)</span></span>
- <span data-ttu-id="a3135-143">已修复 `Get-Help` 以支持 Unix 平台上的区分大小写模式匹配。</span><span class="sxs-lookup"><span data-stu-id="a3135-143">Fixed `Get-Help` to support case insensitive pattern matching on Unix platforms.</span></span> <span data-ttu-id="a3135-144">(#3852)</span><span class="sxs-lookup"><span data-stu-id="a3135-144">(#3852)</span></span>
- <span data-ttu-id="a3135-145">已向包添加 `powershell` 说明手册。</span><span class="sxs-lookup"><span data-stu-id="a3135-145">`powershell` man-page added to package</span></span>

### <a name="logging"></a><span data-ttu-id="a3135-146">日志记录</span><span class="sxs-lookup"><span data-stu-id="a3135-146">Logging</span></span>

<span data-ttu-id="a3135-147">在 macOS 上，PowerShell 使用本机 `os_log` API 登录到 Apple [统一登录系统][os_log]。</span><span class="sxs-lookup"><span data-stu-id="a3135-147">On macOS, PowerShell uses the native `os_log` APIs to log to Apple's [unified logging system][os_log].</span></span>
<span data-ttu-id="a3135-148">在 Linux 上，PowerShell 使用 [Syslog][] 这种通用登录解决方案。</span><span class="sxs-lookup"><span data-stu-id="a3135-148">On Linux, PowerShell uses [Syslog][], a ubiquitous logging solution.</span></span>

### <a name="filesystem"></a><span data-ttu-id="a3135-149">Filesystem</span><span class="sxs-lookup"><span data-stu-id="a3135-149">Filesystem</span></span>

<span data-ttu-id="a3135-150">已在 macOS 和 Linux 上作出众多更改，从而支持传统上不受 Windows 支持的文件名字符：</span><span class="sxs-lookup"><span data-stu-id="a3135-150">A number of changes have been made on macOS and Linux to support filename characters not traditionally supported on Windows:</span></span>

- <span data-ttu-id="a3135-151">cmdlet 的路径现已为斜杠不可知类型（/ 和 \ 皆用作目录分隔符）</span><span class="sxs-lookup"><span data-stu-id="a3135-151">Paths given to cmdlets are now slash-agnostic (both / and \ work as directory separator)</span></span>
- <span data-ttu-id="a3135-152">现已符合和默认使用 XDG 基目录规范：</span><span class="sxs-lookup"><span data-stu-id="a3135-152">XDG Base Directory Specification is now respected and used by default:</span></span>
  - <span data-ttu-id="a3135-153">Linux/macOS 配置文件路径位于 `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a3135-153">The Linux/macOS profile path is located at `~/.config/powershell/profile.ps1`</span></span>
  - <span data-ttu-id="a3135-154">历史记录保存路径位于 `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="a3135-154">The history save path is located at `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`</span></span>
  - <span data-ttu-id="a3135-155">用户模块路径位于 `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a3135-155">The user module path is located at `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="a3135-156">支持 Unix 上包含冒号的文件名称和文件夹名称。</span><span class="sxs-lookup"><span data-stu-id="a3135-156">Support for file and folder names containing the colon character on Unix.</span></span> <span data-ttu-id="a3135-157">(#4959)</span><span class="sxs-lookup"><span data-stu-id="a3135-157">(#4959)</span></span>
- <span data-ttu-id="a3135-158">支持具有逗号的脚本名称或完整路径。</span><span class="sxs-lookup"><span data-stu-id="a3135-158">Support for script names or full paths that have commas.</span></span> <span data-ttu-id="a3135-159">(#4136)（感谢 @TimCurwick！）</span><span class="sxs-lookup"><span data-stu-id="a3135-159">(#4136) (Thanks to @TimCurwick!)</span></span>
- <span data-ttu-id="a3135-160">检测何时使用 `-LiteralPath` 阻止导航 cmdlet 的通配符扩展。</span><span class="sxs-lookup"><span data-stu-id="a3135-160">Detect when `-LiteralPath` is used to suppress wildcard expansion for navigation cmdlets.</span></span> <span data-ttu-id="a3135-161">(#5038)</span><span class="sxs-lookup"><span data-stu-id="a3135-161">(#5038)</span></span>
- <span data-ttu-id="a3135-162">已更新 `Get-ChildItem`，使之更类似于 \*nix `ls -R` 和 Windows `DIR /S` 本机命令。</span><span class="sxs-lookup"><span data-stu-id="a3135-162">Updated `Get-ChildItem` to work more like the \*nix `ls -R` and the Windows `DIR /S` native commands.</span></span>
  <span data-ttu-id="a3135-163">`Get-ChildItem` 现在返回递归搜索期间遇到的符号链接，并且不会搜索这些链接指向的目录。</span><span class="sxs-lookup"><span data-stu-id="a3135-163">`Get-ChildItem` now returns the symbolic links encountered during a recursive search and does not search the directories that those links target.</span></span> <span data-ttu-id="a3135-164">(#3780)</span><span class="sxs-lookup"><span data-stu-id="a3135-164">(#3780)</span></span>

### <a name="case-sensitivity"></a><span data-ttu-id="a3135-165">区分大小写</span><span class="sxs-lookup"><span data-stu-id="a3135-165">Case sensitivity</span></span>

<span data-ttu-id="a3135-166">保留大小写时，Linux 和 macOS 通常区分大小写，而 Windows 不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a3135-166">Linux and macOS tend to be case-sensitive while Windows is case-insensitive while preserving case.</span></span>
<span data-ttu-id="a3135-167">PowerShell 通常不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a3135-167">In general, PowerShell is case insensitive.</span></span>

<span data-ttu-id="a3135-168">例如，环境变量在 macOS 和 Linux 上区分大小写，所以 `PSModulePath` 环境变量的大小写已被标准化。</span><span class="sxs-lookup"><span data-stu-id="a3135-168">For example, environment variables are case-sensitive on macOS and Linux, so the casing of the `PSModulePath` environment variable has been standardized.</span></span> <span data-ttu-id="a3135-169">(#3255) `Import-Module` 在使用文件路径确定模块名称时不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a3135-169">(#3255) `Import-Module` is case insensitive when it's using a file path to determine the module's name.</span></span> <span data-ttu-id="a3135-170">(#5097)</span><span class="sxs-lookup"><span data-stu-id="a3135-170">(#5097)</span></span>

## <a name="support-for-side-by-side-installations"></a><span data-ttu-id="a3135-171">支持并行安装</span><span class="sxs-lookup"><span data-stu-id="a3135-171">Support for side-by-side installations</span></span>

<span data-ttu-id="a3135-172">单独从 Windows PowerShell 安装、配置和执行 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="a3135-172">PowerShell Core is installed, configured, and executed separately from Windows PowerShell.</span></span>
<span data-ttu-id="a3135-173">PowerShell Core 具有一个“可移植”ZIP 包。</span><span class="sxs-lookup"><span data-stu-id="a3135-173">PowerShell Core has a "portable" ZIP package.</span></span>
<span data-ttu-id="a3135-174">使用 ZIP 包可在磁盘任意位置安装任意版本，包括将 PowerShell 作为依赖项的应用程序的本地位置。</span><span class="sxs-lookup"><span data-stu-id="a3135-174">Using the ZIP package, you can install any number of versions anywhere on disk, including local to an application that takes PowerShell as a dependency.</span></span>
<span data-ttu-id="a3135-175">并行安装使测试 PowerShell 新版本和随时间推移而迁移现有脚本变得更简单。</span><span class="sxs-lookup"><span data-stu-id="a3135-175">Side-by-side installation makes it easier to test new versions of PowerShell and migrating existing scripts over time.</span></span>
<span data-ttu-id="a3135-176">并行安装还支持向后兼容性，因为脚本可以固定到其所需的特定版本。</span><span class="sxs-lookup"><span data-stu-id="a3135-176">Side-by-side also enables backwards compatibility as scripts can be pinned to specific versions that they require.</span></span>

> [!NOTE]
> <span data-ttu-id="a3135-177">默认情况下，Windows 上基于 MSI 的安装程序执行就地更新安装。</span><span class="sxs-lookup"><span data-stu-id="a3135-177">By default, the MSI-based installer on Windows does an in-place update install.</span></span>
>

## <a name="renamed-powershellexe-to-pwshexe"></a><span data-ttu-id="a3135-178">已将 `powershell(.exe)` 重命名为 `pwsh(.exe)`</span><span class="sxs-lookup"><span data-stu-id="a3135-178">Renamed `powershell(.exe)` to `pwsh(.exe)`</span></span>

<span data-ttu-id="a3135-179">PowerShell Core 的二进制名称已从 `powershell(.exe)` 更改为 `pwsh(.exe)`。</span><span class="sxs-lookup"><span data-stu-id="a3135-179">The binary name for PowerShell Core has been changed from `powershell(.exe)` to `pwsh(.exe)`.</span></span>
<span data-ttu-id="a3135-180">此更改为用户提供一个决定性方法，从而可在计算机上运行 PowerShell Core 以支持并行 Windows PowerShell 和 PowerShell Core 安装。</span><span class="sxs-lookup"><span data-stu-id="a3135-180">This change provides a deterministic way for users to run PowerShell Core on machines to support side-by-side Windows PowerShell and PowerShell Core installations.</span></span>
<span data-ttu-id="a3135-181">`pwsh` 字符长度更短，且更容易输入。</span><span class="sxs-lookup"><span data-stu-id="a3135-181">`pwsh` is also much shorter and easier to type.</span></span>

<span data-ttu-id="a3135-182">将 `powershell.exe` 重命名为 `pwsh(.exe)` 后的其他更改：</span><span class="sxs-lookup"><span data-stu-id="a3135-182">Additional changes to `pwsh(.exe)` from `powershell.exe`:</span></span>

- <span data-ttu-id="a3135-183">已将第一个位置参数从 `-Command` 更改为 `-File`。</span><span class="sxs-lookup"><span data-stu-id="a3135-183">Changed the first positional parameter from `-Command` to `-File`.</span></span>
  <span data-ttu-id="a3135-184">此更改修复了 `#!`（亦称为 shebang）在非 Windows 平台上非 PowerShell shell 内执行的 PowerShell 脚本 中的使用问题。</span><span class="sxs-lookup"><span data-stu-id="a3135-184">This change fixes the usage of `#!` (aka as a shebang) in PowerShell scripts that are being executed from non-PowerShell shells on non-Windows platforms.</span></span>
  <span data-ttu-id="a3135-185">这还意味着无需指定 `-File` 即可运行 `pwsh foo.ps1` 或 `pwsh fooScript` 等命令。</span><span class="sxs-lookup"><span data-stu-id="a3135-185">It also means that you can run commands like `pwsh foo.ps1` or `pwsh fooScript` without specifying `-File`.</span></span>
  <span data-ttu-id="a3135-186">但是，尝试运行 `pwsh.exe -Command Get-Command` 等命令时，此更改会要求显示指定 `-c` 或 `-Command`。</span><span class="sxs-lookup"><span data-stu-id="a3135-186">However, this change requires that you explicitly specify `-c` or `-Command` when trying to run commands like `pwsh.exe -Command Get-Command`.</span></span> <span data-ttu-id="a3135-187">(#4019)</span><span class="sxs-lookup"><span data-stu-id="a3135-187">(#4019)</span></span>
- <span data-ttu-id="a3135-188">PowerShell Core 接受 `-i`（或 `-Interactive`）切换表示交互式 shell。</span><span class="sxs-lookup"><span data-stu-id="a3135-188">PowerShell Core accepts the `-i` (or `-Interactive`) switch to indicate an interactive shell.</span></span> <span data-ttu-id="a3135-189">(#3558) 这使 PowerShell 可用作 Unix 平台上的默认 shell。</span><span class="sxs-lookup"><span data-stu-id="a3135-189">(#3558) This allows PowerShell to be used as a default shell on Unix platforms.</span></span>
- <span data-ttu-id="a3135-190">已将参数 `-importsystemmodules` 和 `-psconsoleFile` 从 `pwsh.exe` 中删除。</span><span class="sxs-lookup"><span data-stu-id="a3135-190">Removed parameters `-importsystemmodules` and `-psconsoleFile` from `pwsh.exe`.</span></span> <span data-ttu-id="a3135-191">(#4995)</span><span class="sxs-lookup"><span data-stu-id="a3135-191">(#4995)</span></span>
- <span data-ttu-id="a3135-192">已更改 `pwsh -version` 和 `pwsh.exe` 内置帮助，以与其他本机工具保持统一。</span><span class="sxs-lookup"><span data-stu-id="a3135-192">Changed `pwsh -version` and built-in help for `pwsh.exe` to align with other native tools.</span></span> <span data-ttu-id="a3135-193">(#4958 & #4931)（感谢 @iSazonov）</span><span class="sxs-lookup"><span data-stu-id="a3135-193">(#4958 & #4931) (Thanks @iSazonov)</span></span>
- <span data-ttu-id="a3135-194">`-File` 和 `-Command` 的无效参数错误消息以及退出代码与 Unix 标准一致 (#4573)</span><span class="sxs-lookup"><span data-stu-id="a3135-194">Invalid argument error messages for `-File` and `-Command` and exit codes consistent with Unix standards (#4573)</span></span>
- <span data-ttu-id="a3135-195">已在 Windows 上添加 `-WindowStyle` 参数。</span><span class="sxs-lookup"><span data-stu-id="a3135-195">Added `-WindowStyle` parameter on Windows.</span></span> <span data-ttu-id="a3135-196">(#4573) 同样，非 Windows 平台上基于包的安装更新现为就地更新。</span><span class="sxs-lookup"><span data-stu-id="a3135-196">(#4573) Similarly, package-based installations updates on non-Windows platforms are in-place updates.</span></span>

## <a name="backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="a3135-197">Windows PowerShell 向后兼容</span><span class="sxs-lookup"><span data-stu-id="a3135-197">Backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="a3135-198">PowerShell Core 的目标是尽可能兼容 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a3135-198">The goal of PowerShell Core is to remain as compatible as possible with Windows PowerShell.</span></span>
<span data-ttu-id="a3135-199">PowerShell Core 使用 [.NET Standard][] 2.0 提供与现有 .NET 程序集的二进制兼容性。</span><span class="sxs-lookup"><span data-stu-id="a3135-199">PowerShell Core uses [.NET Standard][] 2.0 to provide binary compatibility with existing .NET assemblies.</span></span>
<span data-ttu-id="a3135-200">许多 PowerShell 模块依赖这些程序集（通常为 DLL），而 .NET Standard 可使这些模块继续适用于 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="a3135-200">Many PowerShell modules depend on these assemblies (often times DLLs), so .NET Standard allows them to continue working with .NET Core.</span></span>
<span data-ttu-id="a3135-201">PowerShell Core 还包含一个启发式方法，通过该方法可在常用文件夹（例如全局程序集缓存通常所位于的磁盘位置）中查找 .NET Framework DLL 依赖项。</span><span class="sxs-lookup"><span data-stu-id="a3135-201">PowerShell Core also includes a heuristic to look in well-known folders--like where the Global Assembly Cache typically resides on disk--to find .NET Framework DLL dependencies.</span></span>

<span data-ttu-id="a3135-202">如需详细了解 .NET Standard，请参阅 [.NET 博客][]、本 [YouTube][] 视频以及 GitHub 上的本篇[常见问题][]。</span><span class="sxs-lookup"><span data-stu-id="a3135-202">You can learn more about .NET Standard on the [.NET Blog][], in this [YouTube][] video, and via this [FAQ][] on GitHub.</span></span>

<span data-ttu-id="a3135-203">我们希望确保 PowerShell 语言和“内置”模块（例如 `Microsoft.PowerShell.Management`、`Microsoft.PowerShell.Utility` 等）与它们在 Windows PowerShell 中具有相同的作用，为此，我们已付出诸多努力。</span><span class="sxs-lookup"><span data-stu-id="a3135-203">Best efforts have been made to ensure that the PowerShell language and "built-in" modules (like `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, etc.) work the same as they do in Windows PowerShell.</span></span>
<span data-ttu-id="a3135-204">在许多情况下，通过社区的帮助，我们已添加了一些新功能和针对 cmdlet 的 bug 修补程序。</span><span class="sxs-lookup"><span data-stu-id="a3135-204">In many cases, with the help of the community, we've added new capabilities and bug fixes to those cmdlets.</span></span>
<span data-ttu-id="a3135-205">在某些情况下，由于基础 .NET 层中缺失依赖项，因此功能已被删除或者不可用。</span><span class="sxs-lookup"><span data-stu-id="a3135-205">In some cases, due to a missing dependency in underlying .NET layers, functionality was removed or is unavailable.</span></span>

<span data-ttu-id="a3135-206">大多随附 Windows 的模块（例如 `DnsClient`、`Hyper-V``NetTCPIP`、`Storage` 等）以及其他一些 Microsoft 产品（包括 Azure 和 Office）尚未显式移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="a3135-206">Most of the modules that ship as part of Windows (for example, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, etc.) and other Microsoft products including Azure and Office have not been *explicitly* ported to .NET Core yet.</span></span>
<span data-ttu-id="a3135-207">PowerShell 团队正与这些产品组以及团队开展协作，以验证并将现有模块迁移到 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="a3135-207">The PowerShell team is working with these product groups and teams to validate and port their existing modules to PowerShell Core.</span></span>
<span data-ttu-id="a3135-208">通过使用 .NET Standard 和 [CDXML][]，其中许多传统 Windows PowerShell 模块看似确实可在 PowerShell Core 中运行，但是它们尚未经过正式验证，且不受正式支持。</span><span class="sxs-lookup"><span data-stu-id="a3135-208">With .NET Standard and [CDXML][], many of these traditional Windows PowerShell modules do seem to work in PowerShell Core, but they have not been formally validated, and they are not formally supported.</span></span>

<span data-ttu-id="a3135-209">通过安装 [`WindowsPSModulePath`][windowspsmodulepath] 模块，可将 Windows PowerShell `PSModulePath` 附加到 PowerShell Core `PSModulePath`，从而可使用 Windows PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="a3135-209">By installing the [`WindowsPSModulePath`][windowspsmodulepath] module, you can use Windows PowerShell modules by appending the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="a3135-210">首先，从 PowerShell 库安装 `WindowsPSModulePath` 模块：</span><span class="sxs-lookup"><span data-stu-id="a3135-210">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="a3135-211">安装此模块后，运行 `Add-WindowsPSModulePath` cmdlet 以将 Windows PowerShell `PSModulePath` 添加到 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="a3135-211">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a><span data-ttu-id="a3135-212">Docker 支持</span><span class="sxs-lookup"><span data-stu-id="a3135-212">Docker support</span></span>

<span data-ttu-id="a3135-213">PowerShell Core 已对我们支持的所有主要平台（包括多个 Linux 发行版、Windows Server Core 和 Nano Server）添加了 Docker 容器支持。</span><span class="sxs-lookup"><span data-stu-id="a3135-213">PowerShell Core adds support for Docker containers for all the major platforms we support (including multiple Linux distros, Windows Server Core, and Nano Server).</span></span>

<span data-ttu-id="a3135-214">关于完整列表，请查看 [`microsoft/powershell` Docker Hub][docker-hub] 上对的标记。</span><span class="sxs-lookup"><span data-stu-id="a3135-214">For a complete list, check out the tags on [`microsoft/powershell` on Docker Hub][docker-hub].</span></span>
<span data-ttu-id="a3135-215">有关 Docker 和 PowerShell Core 的详细信息，请参阅 GitHub 上的 [Docker][]。</span><span class="sxs-lookup"><span data-stu-id="a3135-215">For more information on Docker and PowerShell Core, see [Docker][] on GitHub.</span></span>

## <a name="ssh-based-powershell-remoting"></a><span data-ttu-id="a3135-216">基于 SSH 的 PowerShell 远程处理</span><span class="sxs-lookup"><span data-stu-id="a3135-216">SSH-based PowerShell Remoting</span></span>

<span data-ttu-id="a3135-217">除基于 WinRM 的传统 PSRP 外，PowerShell 远程处理协议 (PSRP) 现在还使用安全外壳 (SSH) 协议。</span><span class="sxs-lookup"><span data-stu-id="a3135-217">The PowerShell Remoting Protocol (PSRP) now works with the Secure Shell (SSH) protocol in addition to the traditional WinRM-based PSRP.</span></span>

<span data-ttu-id="a3135-218">这意味着你可以使用 `Enter-PSSession` 和 `New-PSSession` 等 cmdlet，并可使用 SSH 进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="a3135-218">This means that you can use cmdlets like `Enter-PSSession` and `New-PSSession` and authenticate using SSH.</span></span>
<span data-ttu-id="a3135-219">仅需使用基于 OpenSSH 的 SSH 服务器将 PowerShell 注册为子系统即可，并且可以通过传统 `PSSession` 语义使用基于 SSH 的身份验证机制（例如密码或私钥）。</span><span class="sxs-lookup"><span data-stu-id="a3135-219">All you have to do is register PowerShell as a subsystem with an OpenSSH-based SSH server, and you can use your existing SSH-based authenticate mechanisms (like passwords or private keys) with the traditional `PSSession` semantics.</span></span>

<span data-ttu-id="a3135-220">如需详细了解如何配置和使用基于 SSH 的远程处理，请参阅[通过 SSH 进行 PowerShell 远程处理][ssh-remoting]。</span><span class="sxs-lookup"><span data-stu-id="a3135-220">For more information on configuring and using SSH-based remoting, see [PowerShell Remoting over SSH][ssh-remoting].</span></span>

## <a name="default-encoding-is-utf-8-without-a-bom"></a><span data-ttu-id="a3135-221">默认编码现为不具有 BOM 的 UTF-8</span><span class="sxs-lookup"><span data-stu-id="a3135-221">Default encoding is UTF-8 without a BOM</span></span>

<span data-ttu-id="a3135-222">以前，`Get-Content`、`Set-Content` 等 Windows PowerShell cmdlet 使用不同的编码，例如 ASCII 和 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="a3135-222">In the past, Windows PowerShell cmdlets like `Get-Content`, `Set-Content` used different encodings, such as ASCII and UTF-16.</span></span>
<span data-ttu-id="a3135-223">混合使用未指定编码的 cmdlet 时，编码默认的变动会导致问题。</span><span class="sxs-lookup"><span data-stu-id="a3135-223">The variance in encoding defaults created problems when mixing cmdlets without specifying an encoding.</span></span>

<span data-ttu-id="a3135-224">非 Windows 平台通常使用不具有字节顺序标记 (BOM) 的 UTF-8 作为文本文件的默认编码。</span><span class="sxs-lookup"><span data-stu-id="a3135-224">Non-Windows platforms traditionally use UTF-8 without a Byte Order Mark (BOM) as the default encoding for text files.</span></span>
<span data-ttu-id="a3135-225">目前越来越多的 Windows 应用程序和工具避免使用 UTF-16，而是趋向于采用无 BOM 式 的 UTF-8 编码。</span><span class="sxs-lookup"><span data-stu-id="a3135-225">More Windows applications and tools are moving away from UTF-16 and towards BOM-less UTF-8 encoding.</span></span>
<span data-ttu-id="a3135-226">PowerShell Core 更改默认编码以符合更广泛的生态系统。</span><span class="sxs-lookup"><span data-stu-id="a3135-226">PowerShell Core changes the default encoding to conform with the broader ecosystems.</span></span>

<span data-ttu-id="a3135-227">这意味着所有使用 `-Encoding` 参数的内置 cmdlet 均默认使用 `UTF8NoBOM` 值。</span><span class="sxs-lookup"><span data-stu-id="a3135-227">This means that all built-in cmdlets that use the `-Encoding` parameter use the `UTF8NoBOM` value by default.</span></span>
<span data-ttu-id="a3135-228">以下 cmdlet 受此更改影响：</span><span class="sxs-lookup"><span data-stu-id="a3135-228">The following cmdlets are affected by this change:</span></span>

- <span data-ttu-id="a3135-229">Add-Content</span><span class="sxs-lookup"><span data-stu-id="a3135-229">Add-Content</span></span>
- <span data-ttu-id="a3135-230">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="a3135-230">Export-Clixml</span></span>
- <span data-ttu-id="a3135-231">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="a3135-231">Export-Csv</span></span>
- <span data-ttu-id="a3135-232">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="a3135-232">Export-PSSession</span></span>
- <span data-ttu-id="a3135-233">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="a3135-233">Format-Hex</span></span>
- <span data-ttu-id="a3135-234">Get-Content</span><span class="sxs-lookup"><span data-stu-id="a3135-234">Get-Content</span></span>
- <span data-ttu-id="a3135-235">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="a3135-235">Import-Csv</span></span>
- <span data-ttu-id="a3135-236">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="a3135-236">New-ModuleManifest</span></span>
- <span data-ttu-id="a3135-237">Out-File</span><span class="sxs-lookup"><span data-stu-id="a3135-237">Out-File</span></span>
- <span data-ttu-id="a3135-238">Select-String</span><span class="sxs-lookup"><span data-stu-id="a3135-238">Select-String</span></span>
- <span data-ttu-id="a3135-239">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="a3135-239">Send-MailMessage</span></span>
- <span data-ttu-id="a3135-240">Set-Content</span><span class="sxs-lookup"><span data-stu-id="a3135-240">Set-Content</span></span>

<span data-ttu-id="a3135-241">以上 cmdlet 也已经过更新，因此 `-Encoding` 参数会普遍接受 `System.Text.Encoding`。</span><span class="sxs-lookup"><span data-stu-id="a3135-241">These cmdlets have also been updated so that the `-Encoding` parameter universally accepts `System.Text.Encoding`.</span></span>

<span data-ttu-id="a3135-242">`$OutputEncoding` 的默认值也已更改为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="a3135-242">The default value of `$OutputEncoding` has also been changed to UTF-8.</span></span>

<span data-ttu-id="a3135-243">作为最佳做法，应该使用 `-Encoding` 参数在脚本中显示设置编码以生成确定的跨平台行为。</span><span class="sxs-lookup"><span data-stu-id="a3135-243">As a best practice, you should explicitly set encodings in scripts using the `-Encoding` parameter to produce deterministic behavior across platforms.</span></span>

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a><span data-ttu-id="a3135-244">有 `&` 的管道的支持背景 (#3360)</span><span class="sxs-lookup"><span data-stu-id="a3135-244">Support backgrounding of pipelines with ampersand (`&`) (#3360)</span></span>

<span data-ttu-id="a3135-245">将 `&` 置于管道末尾会导致管道作为 PowerShell 作业运行。</span><span class="sxs-lookup"><span data-stu-id="a3135-245">Putting `&` at the end of a pipeline causes the pipeline to be run as a PowerShell job.</span></span>
<span data-ttu-id="a3135-246">管道在后台运行时会返回作业对象。</span><span class="sxs-lookup"><span data-stu-id="a3135-246">When a pipeline is backgrounded, a job object is returned.</span></span>
<span data-ttu-id="a3135-247">管道作为作业运行后，所有标准 `*-Job` cmdlet 均可以用来管理该作业。</span><span class="sxs-lookup"><span data-stu-id="a3135-247">Once the pipeline is running as a job, all of the standard `*-Job` cmdlets can be used to manage the job.</span></span>
<span data-ttu-id="a3135-248">此管道中使用的变量（特定于进程的变量除外）自动复制到该作业，从而使 `Copy-Item $foo $bar &` 正常运行。</span><span class="sxs-lookup"><span data-stu-id="a3135-248">Variables (ignoring process-specific variables) used in the pipeline are automatically copied to the job so `Copy-Item $foo $bar &` just works.</span></span>
<span data-ttu-id="a3135-249">该作业还会在当前目录而不是用户主目录中运行。</span><span class="sxs-lookup"><span data-stu-id="a3135-249">The job is also run in the current directory instead of the user's home directory.</span></span>
<span data-ttu-id="a3135-250">有关 PowerShell 作业的详细信息，请参阅 [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs)。</span><span class="sxs-lookup"><span data-stu-id="a3135-250">For more information about PowerShell jobs, see [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="a3135-251">语义化版本控制</span><span class="sxs-lookup"><span data-stu-id="a3135-251">Semantic versioning</span></span>

- <span data-ttu-id="a3135-252">已使 `SemanticVersion` 与 `SemVer 2.0` 兼容。</span><span class="sxs-lookup"><span data-stu-id="a3135-252">Made `SemanticVersion` compatible with `SemVer 2.0`.</span></span> <span data-ttu-id="a3135-253">(#5037)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="a3135-253">(#5037) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a3135-254">为与 SemVer 符合，已将 `New-ModuleManifest` 中的默认 `ModuleVersion` 更改为 `0.0.1`。</span><span class="sxs-lookup"><span data-stu-id="a3135-254">Changed default `ModuleVersion` in `New-ModuleManifest` to `0.0.1` to align with SemVer.</span></span> <span data-ttu-id="a3135-255">(#4842)（感谢 @LDSpits）</span><span class="sxs-lookup"><span data-stu-id="a3135-255">(#4842) (Thanks @LDSpits)</span></span>
- <span data-ttu-id="a3135-256">已添加 `semver` 作为 `System.Management.Automation.SemanticVersion` 的类型加速器。</span><span class="sxs-lookup"><span data-stu-id="a3135-256">Added `semver` as a type accelerator for `System.Management.Automation.SemanticVersion`.</span></span> <span data-ttu-id="a3135-257">(#4142)（感谢 @oising！）</span><span class="sxs-lookup"><span data-stu-id="a3135-257">(#4142) (Thanks to @oising!)</span></span>
- <span data-ttu-id="a3135-258">已支持比较 `SemanticVersion` 实例和仅使用 `Major` 和 `Minor` 版本值构建的 `Version` 实例。</span><span class="sxs-lookup"><span data-stu-id="a3135-258">Enabled comparison between a `SemanticVersion` instance and a `Version` instance that is constructed only with `Major` and `Minor` version values.</span></span>

## <a name="language-updates"></a><span data-ttu-id="a3135-259">语言更新</span><span class="sxs-lookup"><span data-stu-id="a3135-259">Language updates</span></span>

- <span data-ttu-id="a3135-260">实现 Unicode 转义分析，由此用户可使用 Unicode 字符作为参数、字符串或变量名称。</span><span class="sxs-lookup"><span data-stu-id="a3135-260">Implement Unicode escape parsing so that users can use Unicode characters as arguments, strings, or variable names.</span></span> <span data-ttu-id="a3135-261">(#3958)（感谢 @rkeithhill！）</span><span class="sxs-lookup"><span data-stu-id="a3135-261">(#3958) (Thanks to @rkeithhill!)</span></span>
- <span data-ttu-id="a3135-262">已为 ESC 添加新的转义字符：`` `e``</span><span class="sxs-lookup"><span data-stu-id="a3135-262">Added new escape character for ESC: `` `e``</span></span>
- <span data-ttu-id="a3135-263">已添加将枚举转换为字符串的支持 (#4318)（感谢 @KirkMunro！）</span><span class="sxs-lookup"><span data-stu-id="a3135-263">Added support for converting enums to string (#4318) (Thanks @KirkMunro)</span></span>
- <span data-ttu-id="a3135-264">已修复将单个元素数组转换为泛型集合的问题。</span><span class="sxs-lookup"><span data-stu-id="a3135-264">Fixed casting single element array to a generic collection.</span></span> <span data-ttu-id="a3135-265">(#3170)</span><span class="sxs-lookup"><span data-stu-id="a3135-265">(#3170)</span></span>
- <span data-ttu-id="a3135-266">已向 `..` 运算符添加字符范围重载，因此 `'a'..'z'` 会从“A”到“Z”返回字符。</span><span class="sxs-lookup"><span data-stu-id="a3135-266">Added character range overload to the `..` operator, so `'a'..'z'` returns characters from 'a' to 'z'.</span></span> <span data-ttu-id="a3135-267">(#5026)（感谢 @IISResetMe！）</span><span class="sxs-lookup"><span data-stu-id="a3135-267">(#5026) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="a3135-268">已修复变量赋值，从而避免覆盖只读变量</span><span class="sxs-lookup"><span data-stu-id="a3135-268">Fixed variable assignment to not overwrite read-only variables</span></span>
- <span data-ttu-id="a3135-269">对脚本 cmdlet 加点时会将自动变量的局部变量推送到“DottedScopes”(#4709)</span><span class="sxs-lookup"><span data-stu-id="a3135-269">Push locals of automatic variables to 'DottedScopes' when dotting script cmdlets (#4709)</span></span>
- <span data-ttu-id="a3135-270">支持在拆分运算符中使用“Singleline, Multiline”选项 (#4721)（感谢 @iSazonov）</span><span class="sxs-lookup"><span data-stu-id="a3135-270">Enable use of 'Singleline, Multiline' option in split operator (#4721) (Thanks @iSazonov)</span></span>

## <a name="engine-updates"></a><span data-ttu-id="a3135-271">引擎更新</span><span class="sxs-lookup"><span data-stu-id="a3135-271">Engine updates</span></span>

- <span data-ttu-id="a3135-272">`$PSVersionTable` 具有四个新属性：</span><span class="sxs-lookup"><span data-stu-id="a3135-272">`$PSVersionTable` has four new properties:</span></span>
  - <span data-ttu-id="a3135-273">`PSEdition`：该属性在 PowerShell Core 上设为 `Core`，在 Windows PowerShell 上设为 `Desktop`</span><span class="sxs-lookup"><span data-stu-id="a3135-273">`PSEdition`: This is set to `Core` on PowerShell Core and `Desktop` on Windows PowerShell</span></span>
  - <span data-ttu-id="a3135-274">`GitCommitId`：这是 Git 分支的 Git 提交 ID 或在其中生成 PowerShell 的标记。</span><span class="sxs-lookup"><span data-stu-id="a3135-274">`GitCommitId`: This is the Git commit ID of the Git branch or tag where PowerShell was built.</span></span>
    <span data-ttu-id="a3135-275">在已发布版本中，它可能与 `PSVersion` 相同。</span><span class="sxs-lookup"><span data-stu-id="a3135-275">On released builds, it will likely be the same as `PSVersion`.</span></span>
  - <span data-ttu-id="a3135-276">`OS`：这是 `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription` 返回的 OS 版本字符串</span><span class="sxs-lookup"><span data-stu-id="a3135-276">`OS`: This is an OS version string returned by `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`</span></span>
  - <span data-ttu-id="a3135-277">`Platform`：该属性由 `[System.Environment]::OSVersion.Platform` 返回。它在 Windows 上设置为 `Win32NT`，在 macOS 上为 `MacOSX`，在 Linux 上为 `Unix`。</span><span class="sxs-lookup"><span data-stu-id="a3135-277">`Platform`: This is returned by `[System.Environment]::OSVersion.Platform` It is set to `Win32NT` on Windows, `MacOSX` on macOS, and `Unix` on Linux.</span></span>
- <span data-ttu-id="a3135-278">已从 `$PSVersionTable` 删除 `BuildVersion` 属性。</span><span class="sxs-lookup"><span data-stu-id="a3135-278">Removed the `BuildVersion` property from `$PSVersionTable`.</span></span>
  <span data-ttu-id="a3135-279">此属性与 Windows 内部版本密切相关。</span><span class="sxs-lookup"><span data-stu-id="a3135-279">This property was strongly tied to the Windows build version.</span></span>
  <span data-ttu-id="a3135-280">我们建议使用 `GitCommitId` 检索 PowerShell Core 的确切内部版本。</span><span class="sxs-lookup"><span data-stu-id="a3135-280">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span> <span data-ttu-id="a3135-281">(#3877)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="a3135-281">(#3877) (Thanks to @iSazonov!)</span></span>
- <span data-ttu-id="a3135-282">已从 `$PSVersionTable` 删除 `ClrVersion` 属性。</span><span class="sxs-lookup"><span data-stu-id="a3135-282">Remove `ClrVersion` property from `$PSVersionTable`.</span></span>
  <span data-ttu-id="a3135-283">此属性与 .NET Core 不相关，.NET Core 中此前保留该属性仅是针对一些不适用于 PowerShell 的特定旧用途。</span><span class="sxs-lookup"><span data-stu-id="a3135-283">This property is irrelevant for .NET Core, and was only preserved in .NET Core for specific legacy purposes that are inapplicable to PowerShell.</span></span>
- <span data-ttu-id="a3135-284">已添加三个新自动变量，用以确定特定 OS 中是否正在运行 PowerShell：`$IsWindows`、`$IsMacOs` 和 `$IsLinux`。</span><span class="sxs-lookup"><span data-stu-id="a3135-284">Added three new automatic variables to determine whether PowerShell is running in a given OS: `$IsWindows`, `$IsMacOs`, and `$IsLinux`.</span></span>
- <span data-ttu-id="a3135-285">已将 `GitCommitId` 添加到 PowerShell Core 横幅。</span><span class="sxs-lookup"><span data-stu-id="a3135-285">Add `GitCommitId` to PowerShell Core banner.</span></span>
  <span data-ttu-id="a3135-286">现在启动 PowerShell 时无需运行 `$PSVersionTable` 即可获取版本！</span><span class="sxs-lookup"><span data-stu-id="a3135-286">Now you don't have to run `$PSVersionTable` as soon as you start PowerShell to get the version!</span></span> <span data-ttu-id="a3135-287">(#3916)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="a3135-287">(#3916) (Thanks to @iSazonov!)</span></span>
- <span data-ttu-id="a3135-288">已在 `$PSHome` 中添加名为 `powershell.config.json` 的 JSON 配置文件，用以存储某些启动之前所需的设置（例如 `ExecutionPolicy`）。</span><span class="sxs-lookup"><span data-stu-id="a3135-288">Add a JSON config file called `powershell.config.json` in `$PSHome` to store some settings required before startup time (e.g. `ExecutionPolicy`).</span></span>
- <span data-ttu-id="a3135-289">运行 Windows EXE 时请勿阻止管道</span><span class="sxs-lookup"><span data-stu-id="a3135-289">Don't block pipeline when running Windows EXE's</span></span>
- <span data-ttu-id="a3135-290">已支持 COM 集合的枚举。</span><span class="sxs-lookup"><span data-stu-id="a3135-290">Enabled enumeration of COM collections.</span></span> <span data-ttu-id="a3135-291">(#4553)</span><span class="sxs-lookup"><span data-stu-id="a3135-291">(#4553)</span></span>

## <a name="cmdlet-updates"></a><span data-ttu-id="a3135-292">Cmdlet 更新</span><span class="sxs-lookup"><span data-stu-id="a3135-292">Cmdlet updates</span></span>

### <a name="new-cmdlets"></a><span data-ttu-id="a3135-293">新 cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3135-293">New cmdlets</span></span>

- <span data-ttu-id="a3135-294">已将 `Get-Uptime` 添加到 `Microsoft.PowerShell.Utility`。</span><span class="sxs-lookup"><span data-stu-id="a3135-294">Add `Get-Uptime` to `Microsoft.PowerShell.Utility`.</span></span>
- <span data-ttu-id="a3135-295">添加 `Remove-Alias` 命令。</span><span class="sxs-lookup"><span data-stu-id="a3135-295">Add `Remove-Alias` Command.</span></span> <span data-ttu-id="a3135-296">(#5143)（感谢 @PowershellNinja！）</span><span class="sxs-lookup"><span data-stu-id="a3135-296">(#5143) (Thanks @PowershellNinja!)</span></span>
- <span data-ttu-id="a3135-297">已将 `Remove-Service` 添加到管理模块。</span><span class="sxs-lookup"><span data-stu-id="a3135-297">Add `Remove-Service` to Management module.</span></span> <span data-ttu-id="a3135-298">(#4858)（感谢 @joandrsn！）</span><span class="sxs-lookup"><span data-stu-id="a3135-298">(#4858) (Thanks @joandrsn!)</span></span>

### <a name="web-cmdlets"></a><span data-ttu-id="a3135-299">Web cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3135-299">Web cmdlets</span></span>

- <span data-ttu-id="a3135-300">已添加对 web cmdlet 的证书身份验证支持。</span><span class="sxs-lookup"><span data-stu-id="a3135-300">Add certificate authentication support for web cmdlets.</span></span> <span data-ttu-id="a3135-301">(#4646)（感谢 @markekraus）</span><span class="sxs-lookup"><span data-stu-id="a3135-301">(#4646) (Thanks @markekraus)</span></span>
- <span data-ttu-id="a3135-302">已将内容标头支持添加至 web cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a3135-302">Add support for content headers to web cmdlets.</span></span> <span data-ttu-id="a3135-303">(#4494 & #4640)（感谢 @markekraus）</span><span class="sxs-lookup"><span data-stu-id="a3135-303">(#4494 & #4640) (Thanks @markekraus)</span></span>
- <span data-ttu-id="a3135-304">已将多链接标头支持添加到 Web Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a3135-304">Add multiple link header support to Web Cmdlets.</span></span> <span data-ttu-id="a3135-305">(#5265) （感谢 @markekraus！）</span><span class="sxs-lookup"><span data-stu-id="a3135-305">(#5265) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="a3135-306">支持 web cmdlet 中的链接标头分页 (#3828)</span><span class="sxs-lookup"><span data-stu-id="a3135-306">Support Link header pagination in web cmdlets (#3828)</span></span>
  - <span data-ttu-id="a3135-307">对于 `Invoke-WebRequest`，当响应包括链接标头时，我们创建一个 RelationLink 属性作为表示 URL 和 `rel` 属性的字典，并确保 URL 是绝对的，从而使其更易于开发人员使用。</span><span class="sxs-lookup"><span data-stu-id="a3135-307">For `Invoke-WebRequest`, when the response includes a Link header we create a RelationLink property as a Dictionary representing the URLs and `rel` attributes and ensure the URLs are absolute to make it easier for the developer to use.</span></span>
  - <span data-ttu-id="a3135-308">对于 `Invoke-RestMethod`，当响应包括链接标头时，我们公开 `-FollowRelLink` 切换以自动跟踪 `next` `rel` 链接，直至其不再存在或者选中可选的 `-MaximumFollowRelLink` 参数值。</span><span class="sxs-lookup"><span data-stu-id="a3135-308">For `Invoke-RestMethod`, when the response includes a Link header we expose a `-FollowRelLink` switch to automatically follow `next` `rel` links until they no longer exist or once we hit the optional `-MaximumFollowRelLink` parameter value.</span></span>
- <span data-ttu-id="a3135-309">已向 web cmdlet 添加 `-CustomMethod` 参数，从而支持非标准方法谓词。</span><span class="sxs-lookup"><span data-stu-id="a3135-309">Add `-CustomMethod` parameter to web cmdlets to allow for non-standard method verbs.</span></span> <span data-ttu-id="a3135-310">(#3142)（感谢 @Lee303！）</span><span class="sxs-lookup"><span data-stu-id="a3135-310">(#3142) (Thanks to @Lee303!)</span></span>
- <span data-ttu-id="a3135-311">已向 Web Cmdlet 添加 `SslProtocol` 支持。</span><span class="sxs-lookup"><span data-stu-id="a3135-311">Add `SslProtocol` support to Web Cmdlets.</span></span> <span data-ttu-id="a3135-312">(#5329)（感谢 @markekraus！）</span><span class="sxs-lookup"><span data-stu-id="a3135-312">(#5329) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="a3135-313">已向 web cmdlet 添加 Multipart 支持。</span><span class="sxs-lookup"><span data-stu-id="a3135-313">Add Multipart support to web cmdlets.</span></span> <span data-ttu-id="a3135-314">(#4782)（感谢 @markekraus）</span><span class="sxs-lookup"><span data-stu-id="a3135-314">(#4782) (Thanks @markekraus)</span></span>
- <span data-ttu-id="a3135-315">已向 web cmdlet 添加 `-NoProxy`，从而使其忽略系统范围的代理设置。</span><span class="sxs-lookup"><span data-stu-id="a3135-315">Add `-NoProxy` to web cmdlets so that they ignore the system-wide proxy setting.</span></span> <span data-ttu-id="a3135-316">(#3447)（感谢 @TheFlyingCorpse）</span><span class="sxs-lookup"><span data-stu-id="a3135-316">(#3447) (Thanks to @TheFlyingCorpse!)</span></span>
- <span data-ttu-id="a3135-317">Web Cmdlet 的用户代理现在会报告 OS 平台 (#4937)（感谢 @LDSpits）</span><span class="sxs-lookup"><span data-stu-id="a3135-317">User Agent of Web Cmdlets now reports the OS platform (#4937) (Thanks @LDSpits)</span></span>
- <span data-ttu-id="a3135-318">已将 `-SkipHeaderValidation` 切换添加至 web cmdlet，无需验证标头值即可添加标头。</span><span class="sxs-lookup"><span data-stu-id="a3135-318">Add `-SkipHeaderValidation` switch to web cmdlets to support adding headers without validating the header value.</span></span> <span data-ttu-id="a3135-319">(#4085)</span><span class="sxs-lookup"><span data-stu-id="a3135-319">(#4085)</span></span>
- <span data-ttu-id="a3135-320">现支持 web cmdlet 不必验证服务器的 HTTPS 证书（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="a3135-320">Enable web cmdlets to not validate the HTTPS certificate of the server if required.</span></span>
- <span data-ttu-id="a3135-321">已将身份验证参数添加到 web cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a3135-321">Add authentication parameters to web cmdlets.</span></span> <span data-ttu-id="a3135-322">(#5052)（感谢 @markekraus）</span><span class="sxs-lookup"><span data-stu-id="a3135-322">(#5052) (Thanks @markekraus)</span></span>
  - <span data-ttu-id="a3135-323">已添加可提供如下三个选项的 `-Authentication`：Basic、OAuth和 Bearer。</span><span class="sxs-lookup"><span data-stu-id="a3135-323">Add `-Authentication` that provides three options: Basic, OAuth, and Bearer.</span></span>
  - <span data-ttu-id="a3135-324">已添加 `-Token`，以便获取 OAuth 和 Bearer 选项的持有者令牌。</span><span class="sxs-lookup"><span data-stu-id="a3135-324">Add `-Token` to get the bearer token for OAuth and Bearer options.</span></span>
  - <span data-ttu-id="a3135-325">已添加 `-AllowUnencryptedAuthentication`，以便绕过对除 HTTPS 以外的任何传输方案所提供的身份验证。</span><span class="sxs-lookup"><span data-stu-id="a3135-325">Add `-AllowUnencryptedAuthentication` to bypass authentication that is provided for any transport scheme other than HTTPS.</span></span>
- <span data-ttu-id="a3135-326">已将 `-ResponseHeadersVariable` 添加至 `Invoke-RestMethod`以便支持捕获响应标头。</span><span class="sxs-lookup"><span data-stu-id="a3135-326">Add `-ResponseHeadersVariable` to `Invoke-RestMethod` to enable the capture of response headers.</span></span> <span data-ttu-id="a3135-327">(#4888)（感谢 @markekraus）</span><span class="sxs-lookup"><span data-stu-id="a3135-327">(#4888) (Thanks @markekraus)</span></span>
- <span data-ttu-id="a3135-328">修复 web cmdlet，以在响应状态代码不成功时将 HTTP 响应包含在异常中。</span><span class="sxs-lookup"><span data-stu-id="a3135-328">Fix web cmdlets to include the HTTP response in the exception when the response status code is not success.</span></span> <span data-ttu-id="a3135-329">(#3201)</span><span class="sxs-lookup"><span data-stu-id="a3135-329">(#3201)</span></span>
- <span data-ttu-id="a3135-330">已将 web cmdlet `UserAgent` 从 `WindowsPowerShell` 更改为 `PowerShell`。</span><span class="sxs-lookup"><span data-stu-id="a3135-330">Change web cmdlets `UserAgent` from `WindowsPowerShell` to `PowerShell`.</span></span> <span data-ttu-id="a3135-331">(#4914)（感谢 @markekraus）</span><span class="sxs-lookup"><span data-stu-id="a3135-331">(#4914) (Thanks @markekraus)</span></span>
- <span data-ttu-id="a3135-332">已将显式 `ContentType` 检测添加到 `Invoke-RestMethod` (#4692)</span><span class="sxs-lookup"><span data-stu-id="a3135-332">Add explicit `ContentType` detection to `Invoke-RestMethod` (#4692)</span></span>
- <span data-ttu-id="a3135-333">已修复 web cmdlet `-SkipHeaderValidation`，以便可适用于非标准用户代理标头。</span><span class="sxs-lookup"><span data-stu-id="a3135-333">Fix web cmdlets `-SkipHeaderValidation` to work with non-standard User-Agent headers.</span></span> <span data-ttu-id="a3135-334">(#4479 & #4512)（感谢 @markekraus）</span><span class="sxs-lookup"><span data-stu-id="a3135-334">(#4479 & #4512) (Thanks @markekraus)</span></span>

### <a name="json-cmdlets"></a><span data-ttu-id="a3135-335">JSON cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3135-335">JSON cmdlets</span></span>

- <span data-ttu-id="a3135-336">已将 `-AsHashtable` 添加到 `ConvertFrom-Json` 以返回 `Hashtable`。</span><span class="sxs-lookup"><span data-stu-id="a3135-336">Add `-AsHashtable` to `ConvertFrom-Json` to return a `Hashtable` instead.</span></span> <span data-ttu-id="a3135-337">(#5043)（感谢 @bergmeister！）</span><span class="sxs-lookup"><span data-stu-id="a3135-337">(#5043) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="a3135-338">使用具有 `ConvertTo-Json` 输出的更美观的格式化程序。</span><span class="sxs-lookup"><span data-stu-id="a3135-338">Use prettier formatter with `ConvertTo-Json` output.</span></span> <span data-ttu-id="a3135-339">(#2787)（感谢 @kittholland！）</span><span class="sxs-lookup"><span data-stu-id="a3135-339">(#2787) (Thanks to @kittholland!)</span></span>
- <span data-ttu-id="a3135-340">已将 `Jobject` 序列化支持添加到 `ConvertTo-Json`。</span><span class="sxs-lookup"><span data-stu-id="a3135-340">Add `Jobject` serialization support to `ConvertTo-Json`.</span></span> <span data-ttu-id="a3135-341">(#5141)</span><span class="sxs-lookup"><span data-stu-id="a3135-341">(#5141)</span></span>
- <span data-ttu-id="a3135-342">已修复 `ConvertFrom-Json`，以便从管道对共同构建完整 JSON 字符串的字符数组进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="a3135-342">Fix `ConvertFrom-Json` to deserialize an array of strings from the pipeline that together construct a complete JSON string.</span></span>
  <span data-ttu-id="a3135-343">这修复了某些情况下换行符中断 JSON 分析的问题。</span><span class="sxs-lookup"><span data-stu-id="a3135-343">This fixes some cases where newlines would break JSON parsing.</span></span> <span data-ttu-id="a3135-344">(#3823)</span><span class="sxs-lookup"><span data-stu-id="a3135-344">(#3823)</span></span>
- <span data-ttu-id="a3135-345">已删除为 `System.Array` 定义的 `AliasProperty "Count"`。</span><span class="sxs-lookup"><span data-stu-id="a3135-345">Remove the `AliasProperty "Count"` defined for `System.Array`.</span></span>
  <span data-ttu-id="a3135-346">这删除了某些 `ConvertFrom-Json` 输出上的外部 `Count` 属性。</span><span class="sxs-lookup"><span data-stu-id="a3135-346">This removes the extraneous `Count` property on some `ConvertFrom-Json` output.</span></span> <span data-ttu-id="a3135-347">(#3231)（感谢 @PetSerAl！）</span><span class="sxs-lookup"><span data-stu-id="a3135-347">(#3231) (Thanks to @PetSerAl!)</span></span>

### <a name="csv-cmdlets"></a><span data-ttu-id="a3135-348">CSV cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3135-348">CSV cmdlets</span></span>

- <span data-ttu-id="a3135-349">添加了对 `Import-Csv` 和 `ConvertFrom-Csv` 的 `PSTypeName` 支持。</span><span class="sxs-lookup"><span data-stu-id="a3135-349">Add `PSTypeName` Support for `Import-Csv` and `ConvertFrom-Csv`.</span></span> <span data-ttu-id="a3135-350">(#5389)（感谢 @markekraus！）</span><span class="sxs-lookup"><span data-stu-id="a3135-350">(#5389) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="a3135-351">`Import-Csv` 现已支持将 `CR`、`LF` 和 `CRLF` 作为行分隔符。</span><span class="sxs-lookup"><span data-stu-id="a3135-351">Make `Import-Csv` support `CR`, `LF`, and `CRLF` as line delimiters.</span></span> <span data-ttu-id="a3135-352">(#5363)（感谢 @iSazonov）</span><span class="sxs-lookup"><span data-stu-id="a3135-352">(#5363) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a3135-353">`-NoTypeInformation` 现在作为 `Export-Csv` 和 `ConvertTo-Csv` 上的默认值。</span><span class="sxs-lookup"><span data-stu-id="a3135-353">Make `-NoTypeInformation` the default on `Export-Csv` and `ConvertTo-Csv`.</span></span> <span data-ttu-id="a3135-354">(#5164)（感谢 @markekraus）</span><span class="sxs-lookup"><span data-stu-id="a3135-354">(#5164) (Thanks @markekraus)</span></span>

### <a name="service-cmdlets"></a><span data-ttu-id="a3135-355">服务 cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3135-355">Service cmdlets</span></span>

- <span data-ttu-id="a3135-356">将属性 `UserName`、`Description`、`DelayedAutoStart`、`BinaryPathName` 和 `StartupType` 添加到 `Get-Service` 返回的 `ServiceController` 对象。</span><span class="sxs-lookup"><span data-stu-id="a3135-356">Add properties `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, and `StartupType` to the `ServiceController` objects returned by `Get-Service`.</span></span> <span data-ttu-id="a3135-357">(#4907)（感谢 @joandrsn）</span><span class="sxs-lookup"><span data-stu-id="a3135-357">(#4907) (Thanks @joandrsn)</span></span>
- <span data-ttu-id="a3135-358">添加了在 `Set-Service` 命令上设置属性的功能。</span><span class="sxs-lookup"><span data-stu-id="a3135-358">Add functionality to set credentials on `Set-Service` command.</span></span> <span data-ttu-id="a3135-359">(#4844)（感谢 @joandrsn）</span><span class="sxs-lookup"><span data-stu-id="a3135-359">(#4844) (Thanks @joandrsn)</span></span>

### <a name="other-cmdlets"></a><span data-ttu-id="a3135-360">其他 cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3135-360">Other cmdlets</span></span>

- <span data-ttu-id="a3135-361">已将参数添加到 `Get-ChildItem` 所调用的 `-FollowSymlink` 中，它按需遍历 symlink，并检查链接循环。</span><span class="sxs-lookup"><span data-stu-id="a3135-361">Add a parameter to `Get-ChildItem` called `-FollowSymlink` that traverses symlinks on demand, with checks for link loops.</span></span> <span data-ttu-id="a3135-362">(#4020)</span><span class="sxs-lookup"><span data-stu-id="a3135-362">(#4020)</span></span>
- <span data-ttu-id="a3135-363">更新 `Add-Type` 以支持 `CSharpVersion7`。</span><span class="sxs-lookup"><span data-stu-id="a3135-363">Update `Add-Type` to support `CSharpVersion7`.</span></span> <span data-ttu-id="a3135-364">(#3933)（感谢 @iSazonov）</span><span class="sxs-lookup"><span data-stu-id="a3135-364">(#3933) (Thanks to @iSazonov)</span></span>
- <span data-ttu-id="a3135-365">删除由于使用不受支持的 API 而产生的 `Microsoft.PowerShell.LocalAccounts` 模块，直至找到更佳解决方案。</span><span class="sxs-lookup"><span data-stu-id="a3135-365">Remove the `Microsoft.PowerShell.LocalAccounts` module due to the use of unsupported APIs until a better solution is found.</span></span> <span data-ttu-id="a3135-366">(#4302)</span><span class="sxs-lookup"><span data-stu-id="a3135-366">(#4302)</span></span>
- <span data-ttu-id="a3135-367">删除由于使用不受支持的 API 而在 `Microsoft.PowerShell.Diagnostics` 中产生的 `*-Counter`，直至找到更佳解决方案。</span><span class="sxs-lookup"><span data-stu-id="a3135-367">Remove the `*-Counter` cmdlets in `Microsoft.PowerShell.Diagnostics` due to the use of unsupported APIs until a better solution is found.</span></span> <span data-ttu-id="a3135-368">(#4303)</span><span class="sxs-lookup"><span data-stu-id="a3135-368">(#4303)</span></span>
- <span data-ttu-id="a3135-369">添加对 `Invoke-Item -Path <folder>` 的支持。</span><span class="sxs-lookup"><span data-stu-id="a3135-369">Add support for `Invoke-Item -Path <folder>`.</span></span> <span data-ttu-id="a3135-370">(#4262)</span><span class="sxs-lookup"><span data-stu-id="a3135-370">(#4262)</span></span>
- <span data-ttu-id="a3135-371">将 `-Extension` 和 `-LeafBase` 切换添加到 `Split-Path`，从而可拆分文件名扩展名和文件名其余部分之间的路径。</span><span class="sxs-lookup"><span data-stu-id="a3135-371">Add `-Extension` and `-LeafBase` switches to `Split-Path` so that you can split paths between the filename extension and the rest of the filename.</span></span> <span data-ttu-id="a3135-372">(#2721)（感谢 @powercode！）</span><span class="sxs-lookup"><span data-stu-id="a3135-372">(#2721) (Thanks to @powercode!)</span></span>
- <span data-ttu-id="a3135-373">已将参数 `-Top` 和 `-Bottom` 添加到顶部/底部 N 排序的 `Sort-Object`</span><span class="sxs-lookup"><span data-stu-id="a3135-373">Add parameters `-Top` and `-Bottom` to `Sort-Object` for Top/Bottom N sort</span></span>
- <span data-ttu-id="a3135-374">通过将 `CodeProperty "Parent"` 添加到 `System.Diagnostics.Process` 公开进程的父进程。</span><span class="sxs-lookup"><span data-stu-id="a3135-374">Expose a process' parent process by adding the `CodeProperty "Parent"` to `System.Diagnostics.Process`.</span></span> <span data-ttu-id="a3135-375">(#2850)（感谢 @powercode！）</span><span class="sxs-lookup"><span data-stu-id="a3135-375">(#2850) (Thanks to @powercode!)</span></span>
- <span data-ttu-id="a3135-376">对于 `Get-Process` 的内存列使用 MB 而不是 KB</span><span class="sxs-lookup"><span data-stu-id="a3135-376">Use MB instead of KB for memory columns of `Get-Process`</span></span>
- <span data-ttu-id="a3135-377">为 `Out-String` 添加了 `-NoNewLine` 切换。</span><span class="sxs-lookup"><span data-stu-id="a3135-377">Add `-NoNewLine` switch for `Out-String`.</span></span> <span data-ttu-id="a3135-378">(#5056)（感谢 @raghav710）</span><span class="sxs-lookup"><span data-stu-id="a3135-378">(#5056) (Thanks @raghav710)</span></span>
- <span data-ttu-id="a3135-379">`Move-Item` cmdlet 遵循 `-Include`、`-Exclude` 和 `-Filter` 参数。</span><span class="sxs-lookup"><span data-stu-id="a3135-379">`Move-Item` cmdlet honors `-Include`, `-Exclude`, and `-Filter` parameters.</span></span> <span data-ttu-id="a3135-380">(#3878)</span><span class="sxs-lookup"><span data-stu-id="a3135-380">(#3878)</span></span>
- <span data-ttu-id="a3135-381">允许将 `*` 用于 `Remove-Item` 的注册表路径中。</span><span class="sxs-lookup"><span data-stu-id="a3135-381">Allow `*` to be used in registry path for `Remove-Item`.</span></span> <span data-ttu-id="a3135-382">(#4866)</span><span class="sxs-lookup"><span data-stu-id="a3135-382">(#4866)</span></span>
- <span data-ttu-id="a3135-383">已将 `-Title` 添加到 `Get-Credential`，并统一化跨平台之间的提示体验。</span><span class="sxs-lookup"><span data-stu-id="a3135-383">Add `-Title` to `Get-Credential` and unify the prompt experience across platforms.</span></span>
- <span data-ttu-id="a3135-384">已将 `-TimeOut` 参数添加到 `Test-Connection`。</span><span class="sxs-lookup"><span data-stu-id="a3135-384">Add the `-TimeOut` parameter to `Test-Connection`.</span></span> <span data-ttu-id="a3135-385">(#2492)</span><span class="sxs-lookup"><span data-stu-id="a3135-385">(#2492)</span></span>
- <span data-ttu-id="a3135-386">`Get-AuthenticodeSignature` cmdlet 现可获取文件签名时间戳。</span><span class="sxs-lookup"><span data-stu-id="a3135-386">`Get-AuthenticodeSignature` cmdlets can now get file signature timestamp.</span></span> <span data-ttu-id="a3135-387">(#4061)</span><span class="sxs-lookup"><span data-stu-id="a3135-387">(#4061)</span></span>
- <span data-ttu-id="a3135-388">已从 `Get-Help` 中删除不受支持的 `-ShowWindow` 切换。</span><span class="sxs-lookup"><span data-stu-id="a3135-388">Remove unsupported `-ShowWindow` switch from `Get-Help`.</span></span> <span data-ttu-id="a3135-389">(#4903)</span><span class="sxs-lookup"><span data-stu-id="a3135-389">(#4903)</span></span>
- <span data-ttu-id="a3135-390">修复了 `Get-Content -Delimiter`，使得所返回的数组元素中不包含分隔符 (#3706)（感谢 @mklement0）</span><span class="sxs-lookup"><span data-stu-id="a3135-390">Fix `Get-Content -Delimiter` to not include the delimiter in the array elements returned (#3706) (Thanks @mklement0)</span></span>
- <span data-ttu-id="a3135-391">将 `Meta`、`Charset` 和 `Transitional` 参数添加到 `ConvertTo-HTML` (#4184)（感谢 @ergo3114）</span><span class="sxs-lookup"><span data-stu-id="a3135-391">Add `Meta`, `Charset`, and `Transitional` parameters to `ConvertTo-HTML` (#4184) (Thanks @ergo3114)</span></span>
- <span data-ttu-id="a3135-392">将 `WindowsUBR` 和 `WindowsVersion` 属性添加到 `Get-ComputerInfo` 结果</span><span class="sxs-lookup"><span data-stu-id="a3135-392">Add `WindowsUBR` and `WindowsVersion` properties to `Get-ComputerInfo` result</span></span>
- <span data-ttu-id="a3135-393">将 `-Group` 参数添加到 `Get-Verb`</span><span class="sxs-lookup"><span data-stu-id="a3135-393">Add `-Group` parameter to `Get-Verb`</span></span>
- <span data-ttu-id="a3135-394">将 `ShouldProcess` 支持添加到 `New-FileCatalog` 和 `Test-FileCatalog`（修复了 `-WhatIf` 和 `-Confirm`）。</span><span class="sxs-lookup"><span data-stu-id="a3135-394">Add `ShouldProcess` support to `New-FileCatalog` and `Test-FileCatalog` (fixes `-WhatIf` and `-Confirm`).</span></span> <span data-ttu-id="a3135-395">(#3074)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="a3135-395">(#3074) (Thanks to @iSazonov!)</span></span>
- <span data-ttu-id="a3135-396">将 `-WhatIf` 切换添加到 `Start-Process` cmdlet (#4735)（感谢 @sarithsutha）</span><span class="sxs-lookup"><span data-stu-id="a3135-396">Add `-WhatIf` switch to `Start-Process` cmdlet (#4735) (Thanks @sarithsutha)</span></span>
- <span data-ttu-id="a3135-397">将 `ValidateNotNullOrEmpty` 添加到多个现有参数。</span><span class="sxs-lookup"><span data-stu-id="a3135-397">Add `ValidateNotNullOrEmpty` too many existing parameters.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="a3135-398">Tab 自动补全</span><span class="sxs-lookup"><span data-stu-id="a3135-398">Tab completion</span></span>

- <span data-ttu-id="a3135-399">改进了基于运行时变量值的 tab 自动补全中的类型推理。</span><span class="sxs-lookup"><span data-stu-id="a3135-399">Enhanced the type inference in tab completion based on runtime variable values.</span></span> <span data-ttu-id="a3135-400">(#2744)（感谢 @powercode！）这支持在类似如下的情况中进行 tab 自动补全：</span><span class="sxs-lookup"><span data-stu-id="a3135-400">(#2744) (Thanks to @powercode!) This enables tab completion in situations like:</span></span>

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- <span data-ttu-id="a3135-401">为 `Select-Object` 的 `-Property` 添加了 Hashtable tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="a3135-401">Add Hashtable tab completion for `-Property` of `Select-Object`.</span></span> <span data-ttu-id="a3135-402">(#3625)（感谢 @powercode）</span><span class="sxs-lookup"><span data-stu-id="a3135-402">(#3625) (Thanks to @powercode)</span></span>
- <span data-ttu-id="a3135-403">对 `-ExcludeProperty` 和 `Select-Object` 的 `-ExpandProperty` 支持参数自动补全。</span><span class="sxs-lookup"><span data-stu-id="a3135-403">Enable argument auto-completion for `-ExcludeProperty` and `-ExpandProperty` of `Select-Object`.</span></span> <span data-ttu-id="a3135-404">(#3443)（感谢 @iSazonov！）</span><span class="sxs-lookup"><span data-stu-id="a3135-404">(#3443) (Thanks to @iSazonov!)</span></span>
- <span data-ttu-id="a3135-405">修复了 tab 自动补全中的 bug，以使 `native.exe --<tab>` 调用到本机完成程序。</span><span class="sxs-lookup"><span data-stu-id="a3135-405">Fix a bug in tab completion to make `native.exe --<tab>` call into native completer.</span></span> <span data-ttu-id="a3135-406">(#3633)（感谢 @powercode！）</span><span class="sxs-lookup"><span data-stu-id="a3135-406">(#3633) (Thanks to @powercode!)</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="a3135-407">重大更改</span><span class="sxs-lookup"><span data-stu-id="a3135-407">Breaking changes</span></span>

<span data-ttu-id="a3135-408">我们在 PowerShell Core 6.0 中引入大量重大更改。</span><span class="sxs-lookup"><span data-stu-id="a3135-408">We've introduced a number of breaking changes in PowerShell Core 6.0.</span></span>
<span data-ttu-id="a3135-409">若要了解其详细信息，请参阅 [PowerShell Core 6.0 中的重大更改][breaking-changes]。</span><span class="sxs-lookup"><span data-stu-id="a3135-409">To read more about them in detail, see [Breaking Changes in PowerShell Core 6.0][breaking-changes].</span></span>

## <a name="debugging"></a><span data-ttu-id="a3135-410">调试</span><span class="sxs-lookup"><span data-stu-id="a3135-410">Debugging</span></span>

- <span data-ttu-id="a3135-411">支持 `Invoke-Command -ComputerName` 的远程步进调试。</span><span class="sxs-lookup"><span data-stu-id="a3135-411">Support for remote step-in debugging for `Invoke-Command -ComputerName`.</span></span> <span data-ttu-id="a3135-412">(#3015)</span><span class="sxs-lookup"><span data-stu-id="a3135-412">(#3015)</span></span>
- <span data-ttu-id="a3135-413">在 PowerShell Core 中启用绑定器调试登录</span><span class="sxs-lookup"><span data-stu-id="a3135-413">Enable binder debug logging in PowerShell Core</span></span>

## <a name="filesystem-updates"></a><span data-ttu-id="a3135-414">Filesystem 更新</span><span class="sxs-lookup"><span data-stu-id="a3135-414">Filesystem updates</span></span>

- <span data-ttu-id="a3135-415">支持从 UNC 路径使用 Filesystem 提供程序。</span><span class="sxs-lookup"><span data-stu-id="a3135-415">Enable usage of the Filesystem provider from a UNC path.</span></span> <span data-ttu-id="a3135-416">($4998)</span><span class="sxs-lookup"><span data-stu-id="a3135-416">($4998)</span></span>
- <span data-ttu-id="a3135-417">`Split-Path` 现在适用于 UNC 根</span><span class="sxs-lookup"><span data-stu-id="a3135-417">`Split-Path` now works with UNC roots</span></span>
- <span data-ttu-id="a3135-418">没有参数的 `cd` 现在表现为 `cd ~`</span><span class="sxs-lookup"><span data-stu-id="a3135-418">`cd` with no arguments now behaves as `cd ~`</span></span>
- <span data-ttu-id="a3135-419">修复了 PowerShell Core，以允许使用长度超过 260 字符的路径。</span><span class="sxs-lookup"><span data-stu-id="a3135-419">Fixed PowerShell Core to allow use of paths that are more than 260 characters long.</span></span> <span data-ttu-id="a3135-420">(#3960)</span><span class="sxs-lookup"><span data-stu-id="a3135-420">(#3960)</span></span>

## <a name="bug-fixes-and-performance-improvements"></a><span data-ttu-id="a3135-421">Bug 修复和性能改进</span><span class="sxs-lookup"><span data-stu-id="a3135-421">Bug fixes and performance improvements</span></span>

<span data-ttu-id="a3135-422">我们已对 PowerShell 多方面作出众多性能改进，涉及方面包含启动时间、各种内置 cmdlet以及与本机二进制文件的交互。</span><span class="sxs-lookup"><span data-stu-id="a3135-422">We've made *many* improvements to performance across PowerShell, including in startup time, various built-in cmdlets, and interaction with native binaries.</span></span>

<span data-ttu-id="a3135-423">我们还修复 PowerShell Core 中的众多 bug。</span><span class="sxs-lookup"><span data-stu-id="a3135-423">We've also fixed a number of bugs within PowerShell Core.</span></span>
<span data-ttu-id="a3135-424">有关修复和更改的完整列表，请查看 GitHub 上的 [changelog][]。</span><span class="sxs-lookup"><span data-stu-id="a3135-424">For a complete list of fixes and changes, check out our [changelog][] on GitHub.</span></span>

## <a name="telemetry"></a><span data-ttu-id="a3135-425">遥测</span><span class="sxs-lookup"><span data-stu-id="a3135-425">Telemetry</span></span>

- <span data-ttu-id="a3135-426">PowerShell Core 6.0 将遥测添加到控制台主机以报告两个值 (#3620)：</span><span class="sxs-lookup"><span data-stu-id="a3135-426">PowerShell Core 6.0 added telemetry to the console host to report two values (#3620):</span></span>
  - <span data-ttu-id="a3135-427">OS 平台 (`$PSVersionTable.OSDescription`)</span><span class="sxs-lookup"><span data-stu-id="a3135-427">the OS platform (`$PSVersionTable.OSDescription`)</span></span>
  - <span data-ttu-id="a3135-428">PowerShell 确切版本 (`$PSVersionTable.GitCommitId`)</span><span class="sxs-lookup"><span data-stu-id="a3135-428">the exact version of PowerShell (`$PSVersionTable.GitCommitId`)</span></span>

<span data-ttu-id="a3135-429">如果你想选择退出此遥测，只需删除 `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` 或使用以下值之一创建 `POWERSHELL_TELEMETRY_OPTOUT` 环境变量：`true`、`1` 或 `yes`。</span><span class="sxs-lookup"><span data-stu-id="a3135-429">If you want to opt-out of this telemetry, simply delete `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` or create `POWERSHELL_TELEMETRY_OPTOUT` environment variable with one of the following values: `true`, `1` or `yes`.</span></span>
<span data-ttu-id="a3135-430">删除此文件或创建变量将免除所有遥测，即便是首次运行 PowerShell 也不例外。</span><span class="sxs-lookup"><span data-stu-id="a3135-430">Deleting this file or creating the variable bypasses all telemetry even before the first run of PowerShell.</span></span>
<span data-ttu-id="a3135-431">我们还计划将此遥测数据和从遥测中收集的见解公开在[社区仪表盘][community-dashboard]中。</span><span class="sxs-lookup"><span data-stu-id="a3135-431">We also plan on exposing this telemetry data and the insights we glean from the telemetry in the [community dashboard][community-dashboard].</span></span>
<span data-ttu-id="a3135-432">如需详细了解我们如何使用此数据，请阅读本[博客文章][telemetry-blog]。</span><span class="sxs-lookup"><span data-stu-id="a3135-432">You can find out more about how we use this data in this [blog post][telemetry-blog].</span></span>

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/en-us/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET 博客]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[常见问题]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/en-us/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
