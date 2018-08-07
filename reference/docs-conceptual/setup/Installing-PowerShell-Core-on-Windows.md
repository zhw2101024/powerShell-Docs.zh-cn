# <a name="installing-powershell-core-on-windows"></a>在 Windows 上安装 PowerShell Core

## <a name="msi"></a>MSI

若要在 Windows 客户端或 Windows Server（适用于 Windows 7 SP1、Server 2008 R2 以及更高版本）上安装 PowerShell，请从 GitHub [版本][]页面下载 MSI 包。

MSI 文件类似于 `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

下载后，双击安装程序并按照提示进行操作。

安装后会向“开始”菜单添加快捷方式。

- 默认情况下，包安装位置为 `$env:ProgramFiles\PowerShell\<version>`
- 可以通过“开始”菜单或 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` 启动 PowerShell

### <a name="prerequisites"></a>必备条件

若要通过 WSMan 启用 PowerShell 远程处理，需要满足以下先决条件：

- 在 Windows 10 之前的 Windows 版本上安装[通用 C 运行时](https://www.microsoft.com/download/details.aspx?id=50410)。
  可通过直接下载或 Windows 更新进行安装。
  经完全修补（含可选包）且受支持的系统中已安装有通用 C 运行时。
- 在 Windows 7 和 Windows Server 2008 R2 上安装 Windows Management Framework (WMF) 4.0 或更高版本。

## <a name="zip"></a>ZIP

提供有 PowerShell 二进制 ZIP 存档，从而支持高级部署方案。
请注意，使用 ZIP 存档时，不同于使用 MSI，你无法获取 MSI 先决条件检查。
因此，为使通过 WSMan 进行的远程处理可在低于 Windows 10 的 Windows 版本上正常运行，则需确保满足[先决条件](#prerequisites)。

## <a name="deploying-on-windows-iot"></a>在 Windows IoT 上部署

Windows IoT 已经附带了 Windows PowerShell，我们将使用它来部署 PowerShell Core 6。

1. 在目标设备中创建 `PSSession`

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. 将 ZIP 包复制到设备

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. 连接到设备并展开存档

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. 在 PowerShell Core 6 中设置远程处理

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. 连接到设备上的 PowerShell Core 6 终结点

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a>在 Nano Server 上进行部署

这些说明假定某个 PowerShell 版本已在 Nano Server 映像上运行，并且其已经由 [Nano Server 映像生成器](/windows-server/get-started/deploy-nano-server)生成。
Nano Server 是“无外设”OS。 可以使用两种不同的方法部署核心二进制文件。

1. 脱机 - 安装 Nano Server VHD，并将 zip 文件的内容解压到安装映像中的所选位置。
2. 联机 - 通过 PowerShell 会话传输 zip 文件，并在所需位置中将其解压。

这两种情况下皆需要 Windows 10 x64 ZIP 发布包，且需要在“管理员”PowerShell 实例中运行命令。

### <a name="offline-deployment-of-powershell-core"></a>PowerShell Core 脱机部署

1. 使用常用 zip 实用工具将包解压到已安装的 Nano Server 映像中的目录。
2. 卸载映像并启动。
3. 连接到 Windows PowerShell 的收件箱实例。
4. 按照说明使用[“另一种实例技术”](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。

### <a name="online-deployment-of-powershell-core"></a>PowerShell Core 联机部署

以下步骤将指导你向 Nano Server 运行实例部署 PowerShell Core，并配置其远程终结点。

- 连接到 Windows PowerShell 的收件箱实例

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- 将文件复制到 Nano Server 实例

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- 输入会话

  ```powershell
  Enter-PSSession $session
  ```

- 提取 ZIP 文件

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- 如果需要基于 WSMan 的远程处理，请按照说明使用[“另一种实例技术”](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。

## <a name="instructions-to-create-a-remoting-endpoint"></a>有关创建远程处理终结点的说明

PowerShell Core 同时支持采用 WSMan 和 SSH 的 PowerShell 远程处理协议 (PSRP)。
有关更多信息，请参阅：

- [在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]
- [在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]

## <a name="artifact-installation-instructions"></a>项目安装说明

我们使用 [AppVeyor][] 在每个 CI 版本上发布具有 CoreCLR 位的存档。

若要从 CoreCLR 项目中安装 PowerShell Core：

1. 从特定版本的“项目”选项卡下载 ZIP 包。
2. 解除阻止 ZIP 文件：右键单击“文件资源管理器”->“属性”->“选中‘解除阻止’框”->“应用”
3. 将 zip 文件解压到 `bin` 目录
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[版本]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
