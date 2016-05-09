# 适用于 Linux 的 Desired State Configuration (DSC) 入门

本主题说明如何开始使用适用于 Linux 的 PowerShell Desired State Configuration (DSC)。 有关 DSC 的常规信息，请参阅 [Windows PowerShell Desired State Configuration 入门](overview.md)。

## 支持的 Linux 操作系统版本

适用于 Linux 的 DSC 支持以下 Linux 操作系统版本。
- CentOS 5、6 和 7 (x86/x64)
- Debian GNU/Linux 6 和 7 (x86/x64)
- Oracle Linux 5、6 和 7 (x86/x64)
- Red Hat Enterprise Linux Server 5、6 和 7 (x86/x64)
- SUSE Linux Enterprise Server 10、11 和 12 (x86/x64)
- Ubuntu Server 12.04 LTS 和 14.04 LTS (x86/x64)

下表说明了适用于 Linux 的 DSC 所需的程序包依赖项。

|  所需程序包 |  说明 |  最低版本 | 
|---|---|---|
| glibc| GNU 库| 2…4 – 31.30| 
| python| Python| 2.4 – 3.4| 
| omiserver| 开放式管理基础结构| 1.0.8.1| 
| openssl| OpenSSL 库| 0.9.8 或 1.0| 
| ctypes| Python CTypes 库| 必须与 Python 版本匹配| 
| libcurl| cURL http 客户端库| 7.15.1| 

## 安装适用于 Linux 的 DSC

必须先安装[开放式管理基础结构 (OMI)](https://collaboration.opengroup.org/omi/)，才能安装适用于 Linux 的 DSC。

### 安装 OMI

适用于 Linux 的 Desired State Configuration 需要开放式管理基础结构 (OMI) CIM 服务器 1.0.8.1 版。 可从 The Open Group：[Open Management Infrastructure (OMI)（开放式管理基础结构）](https://collaboration.opengroup.org/omi/)下载 OMI。

若要安装 OMI，请安装适用于 Linux 系统（.rpm 或.deb）和 OpenSSL 版本（ssl_098 或 ssl_100）以及体系结构 (x64/x86) 的程序包。 RPM 程序包适用于 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。 DEB 程序包适用于 Debian GNU/Linux 和 Ubuntu Server。 ssl_098 程序包适用于安装了 OpenSSL 0.9.8 的计算机，而 ssl_100 程序包适用于安装了 OpenSSL 1.0 的计算机。

> **注意**：若要确定安装的 OpenSSL 版本，请运行 `openssl version` 命令。

运行以下命令以在 CentOS 7 x64 系统上安装 OMI。

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### 安装 DSC

适用于 Linux 的 DSC 可在[此处](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest)下载。 

若要安装 DSC，请安装适用于 Linux 系统（.rpm 或.deb）和 OpenSSL 版本（ssl_098 或 ssl_100）以及体系结构 (x64/x86) 的程序包。 RPM 程序包适用于 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。 DEB 程序包适用于 Debian GNU/Linux 和 Ubuntu Server。 ssl_098 程序包适用于安装了 OpenSSL 0.9.8 的计算机，而 ssl_100 程序包适用于安装了 OpenSSL 1.0 的计算机。

> **注意**：若要确定安装的 OpenSSL 版本，请运行 openssl version 命令。
 
运行以下命令以在 CentOS 7 x64 系统上安装 DSC。

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## 使用适用于 Linux 的 DSC

以下章节说明了如何在 Linux 计算机上创建和运行 DSC 配置。

### 创建配置 MOF 文档

使用 Windows PowerShell Configuration 关键字为 Linux 计算机创建配置，与为 Windows 计算机创建配置类似。 以下步骤描述了如何使用 Windows PowerShell 为 Linux 计算机创建配置文档。

1. 导入 nx 模块。 此 nx Windows PowerShell 模块包含适用于 Linux 的 DSC 内置资源的架构，必须将其安装到本地计算机上并导入到配置中。

    -若要安装 nx 模块，请将 nx 模块目录复制到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 或 `$PSHOME\Modules` 中。 该 nx 模块包含在适用于 Linux 的 DSC 安装包 (MSI) 中。 若要在配置中导入 nx 模块，请使用 __Import-DSCResource__ 命令：
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. 定义配置并生成配置文档：

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### 将配置推送到 Linux 计算机

可使用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 将配置文档（MOF 文件）推送到 Linux 计算机。 若要将此 cmdlet 和 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379).aspx 或 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet 远程运用到 Linux 计算机，必须使用 CIMSession。 使用 [New-CimSession](https://technet.microsoft.com/en-us/library/jj590760.aspx) cmdlet 将 CIMSession 创建到 Linux 计算机中。

以下代码表明了如何创建适用于 Linux 的 DSC CIMSession。

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> **注意**：
* 对于“推送”模式，用户凭据必须是 Linux 计算机上的根用户。
* 适用于 Linux 的 DSC 仅支持 SSL/TLS 连接，使用 New-CimSession 时必须将 –UseSSL 参数设置为 $true。
* 在 `/opt/omi/etc/omiserver.conf` 文件中通过 pemfile 和 keyfile 属性指定（DSC 的）OMI 使用的 SSL 证书。
如果 [New-CimSession](https://technet.microsoft.com/en-us/library/jj590760.aspx) cmdlet 运行于的 Windows 计算机不信任此证书，你可以通过以下 CIMSession 选项选择忽略证书验证：`-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`。

运行以下命令以将 DSC 配置推送到 Linux 节点。

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### 使用请求服务器分发配置

可使用请求服务器将配置分发到 Linux 计算机，与分发到 Windows 计算机类似。 有关使用请求服务器的指南，请参阅 [Windows PowerShell Desired State Configuration 请求服务器](pullServer.md)。 有关通过请求服务器使用 Linux 计算机其他信息和限制条件，请参阅“适用于 Linux 的 Desired State Configuration 发行说明”。

### 从本地进行配置

适用于 Linux 的 DSC 包括用于从本地 Linux 计算机进行配置的脚本。 这些脚本位于 `/opt/microsoft/dsc/Scripts` 中，包括以下内容：
* GetDscConfiguration.py

 返回应用于此计算机的当前配置。 与 Windows PowerShell cmdlet Get-DscConfiguration cmdlet 类似。

`# sudo ./GetDscConfiguration.py`

* GetDscLocalConfigurationManager.py

 返回应用于此计算机的当前元配置。 与 cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet 类似。

`# sudo ./GetDscLocalConfigurationManager.py`

* InstallModule.py

 安装自定义 DSC 资源模块。 需要包含模块共享对象库和架构 MOF 文件的 .zip 文件的路径。

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 删除自定义 DSC 资源模块。 需要待删除模块的名称。

`# sudo ./RemoveModule.py cnx_Resource`

* StartDscLocalConfigurationManager.py 

 将配置 MOF 文件应用于计算机。 与 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 类似。 需要待应用的配置 MOF 的路径。

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* SetDscLocalConfigurationManager.py

 将元配置 MOF 文件应用于计算机。 与 [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet 类似。 需要待应用的元配置 MOF 的路径。

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## 适用于 Linux 的 PowerShell Desired State Configuration 日志文件

为适用于 Linux 的.DSC 生成了以下日志文件。

|日志文件|Directory|说明|
|---|---|---|
|omiserver.log|/opt/omi/var/log/|与 OMI CIM 服务器操作相关的消息。|
|dsc.log|/opt/omi/var/log/|与本地配置管理器 (LCM) 操作和 DSC 资源操作相关的消息。|


<!--HONumber=Apr16_HO2-->


