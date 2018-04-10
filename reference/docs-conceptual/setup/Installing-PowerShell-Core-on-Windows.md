# <a name="installing-powershell-core-on-windows"></a>在 Windows 上安装 PowerShell Core

## <a name="msi"></a>MSI

若要在 Windows 客户端或 Windows Server（适用于 Windows 7 SP1、Server 2008 R2 以及更高版本）上安装 PowerShell，请从 GitHub [版本][]页面下载 MSI 包。

MSI 文件类似于 `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

下载后，双击安装程序并按照提示进行操作。

安装后会向“开始”菜单添加快捷方式。

* 默认情况下，包安装位置为 `$env:ProgramFiles\PowerShell\`
* 可以通过“开始”菜单或 `$env:ProgramFiles\PowerShell\pwsh.exe` 启动 PowerShell

### <a name="prerequisites"></a>必备条件

若要通过 WSMan 启用 PowerShell 远程处理，需要满足以下先决条件：

* 在 Windows 10 之前的 Windows 版本上安装[通用 C 运行时](https://www.microsoft.com/download/details.aspx?id=50410)。
  可通过直接下载或 Windows 更新进行安装。
  经完全修补（含可选包）且受支持的系统中已安装有通用 C 运行时。
* 在 Windows 7 和 Windows Server 2008 R2 上安装 Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) 或更高版本([5.1](https://www.microsoft.com/download/details.aspx?id=54616))。

## <a name="zip"></a>ZIP

提供有 PowerShell 二进制 ZIP 存档，从而支持高级部署方案。
请注意，使用 ZIP 存档时，不同于使用 MSI，你无法获取 MSI 先决条件检查。
因此，为使通过 WSMan 进行的远程处理可在低于 Windows 10 的 Windows 版本上正常运行，则需确保满足[先决条件](#prerequisites)。

## <a name="deploying-on-nano-server"></a>在 Nano Server 上进行部署

这些说明假定某个 PowerShell 版本已在 Nano Server 映像上运行，并且其已经由 [Nano Server 映像生成器](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server)生成。
Nano Server 是“无外设”操作系统，PowerShell Core 二进制文件部署可以两种不同的方式进行：

1. 脱机 - 安装 Nano Server VHD，并将 zip 文件的内容解压到安装映像中的所选位置。
1. 联机 - 通过 PowerShell 会话传输 zip 文件，并在所需位置中将其解压。

这两种情况下皆需要 Windows 10 x64 Zip 发布包，且需要在“管理员”PowerShell 实例中运行命令。

### <a name="offline-deployment-of-powershell-core"></a>PowerShell Core 脱机部署

1. 使用常用 zip 实用工具将包解压到已安装的 Nano Server 映像中的目录。
1. 卸载映像并启动。
1. 连接到 Windows PowerShell 的收件箱实例。
1. 按照说明使用[另一种实例技术](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。

### <a name="online-deployment-of-powershell-core"></a>PowerShell Core 联机部署

以下步骤将指导将 PowerShell Core 部署到 Nano Server 运行的实例及其远程终结点的配置。

* 连接到 Windows PowerShell 的收件箱实例

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* 将文件复制到 Nano Server 实例

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* 输入会话

```powershell
Enter-PSSession $session
```

* 提取 Zip 文件

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* 如果需要基于 WSMan 的远程处理，请按照说明使用[另一种实例技术](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)创建远程处理终结点。

## <a name="instructions-to-create-a-remoting-endpoint"></a>有关创建远程处理终结点的说明

PowerShell Core 同时支持采用 WSMan 和 SSH 的 PowerShell 远程处理协议 (PSRP)。 有关更多信息，请参阅：

* [在 PowerShell Core 中进行 SSH 远程处理][ssh-remoting]
* [在 PowerShell Core 中进行 WSMan 远程处理][wsman-remoting]

## <a name="artifact-installation-instructions"></a>项目安装说明

我们使用 [AppVeyor][] 在每个 CI 版本上发布具有 CoreCLR 位的存档。

## <a name="coreclr-artifacts"></a>CoreCLR 项目

* 从特定版本的“项目”选项卡下载 zip 包。
* 解除阻止 zip 文件：右键单击“文件资源管理器”->“属性”->“检查‘解除阻止’框”->“应用”
* 将 zip 文件解压到 `bin` 目录
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[版本]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell