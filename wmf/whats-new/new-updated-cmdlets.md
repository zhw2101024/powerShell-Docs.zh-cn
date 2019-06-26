---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 新的和更新的 cmdlet
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298657"
---
# <a name="new-and-updated-cmdlets"></a>新的和更新的 cmdlet

我们根据社区反馈，添加了新的 cmdlet，并更新了现有 cmdlet。

## <a name="archive-cmdlets"></a>存档 cmdlet

通过 `Compress-Archive` 和 `Expand-Archive` 这两个新 cmdlet 可以压缩和展开 ZIP 文件。

有关详细信息，请参阅 [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) 模块文档。

## <a name="catalog-cmdlets"></a>目录 Cmdlet

在 Microsoft.PowerShell.Security 模块中新增了两个新 cmdlet。

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

这两个 cmdlet 可用于生成和验证 Windows 目录文件。

## <a name="clipboard-cmdlets"></a>剪贴板 cmdlet

通过 `Get-Clipboard` 和 `Set-Clipboard`，你可以更轻松地将内容传入和传出 Windows PowerShell 会话。 剪贴板 cmdlet 支持图像、音频文件、文件列表和文本。

有关更多信息，请参阅：

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>加密消息语法 (CMS) cmdlet

加密消息语法 cmdlet 对使用 IETF 标准格式加密保护消息的内容提供加密和解密支持，如 [RFC5652](https://tools.ietf.org/html/rfc5652.html).中所述。

CMS 加密标准采用公钥加密系统，其中用来加密内容的密钥（公钥  ）和用来解密内容的密钥（私钥  ）是分离的。

公钥可以广泛共享，它不是敏感数据。 只能使用私钥解密使用公钥加密的任何内容。 有关详细信息，请参阅 [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)（公钥加密）。

有关详细信息，请参阅：

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

证书需要唯一的密钥用法标识符 (EKU)（如“代码签名”或“加密邮件”）在 PowerShell 中将它们识别为数据加密证书。 若要在证书提供程序中查看文档加密证书，可以使用 `Get-ChildItem` 的 DocumentEncryptionCert  动态参数：

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>从字符串内容中提取并分析结构化对象

### <a name="convertfrom-string"></a>ConvertFrom-String

新 `ConvertFrom-String` cmdlet 支持两种模式：

- 基本分隔分析
- 自动生成的示例驱动的分析

默认情况下，分隔分析会在空格处将输入拆分，并为得到的组分配属性名称。

UpdateTemplate  参数将学习算法的结果保存到模板文件中的注释内。 这使得学习过程（速度最慢的阶段）成为一次性完成的过程。 使用包含已编码学习算法的模板来运行 `ConvertFrom-String` 现为近即时行为。

有关详细信息，请参阅 [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String)。

### <a name="convert-string"></a>Convert-String

`Convert-String` 可用于提供提供所需文本外观的前后对照示例。 该 cmdlet 将自动设置文本格式。

有关详细信息，请参阅 [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String)。

## <a name="updates-to-fileinfo-object"></a>对 FileInfo 对象的更新

文件版本信息可能会产生误导，尤其是在对文件进行了修补的情况下。 WMF 5.0 向 FileInfo 对象添加了新的 FileVersionRaw 和 ProductVersionRaw 脚本属性    。
以下是为 powershell.exe 显示的属性（假设 $pid 为 PowerShell 进程的 ID）：

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` 使你能够以十六进制格式查看文本或二进制数据。

有关详细信息，请参阅 [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex)。

## <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem 具有 -Depth 参数

`Get-ChildItem` 现在具有 Depth  参数，可以将其与 Recurse  一起使用来限制递归：

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>对声明版本范围的模块支持（1.* 等）

现在，可以组合 MinimumVersion 和 MaximumVersion，导入特定范围内的模块   。 这些参数还支持通配符。

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

还有许多需要唯一标识符的情况。 `New-GUID` cmdlet 提供了一种简单的方法来创建新的 GUID。

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>NoNewLine 参数

`Out-File`、`Add-Content` 和 `Set-Content` 现在具有新的 NoNewline  开关，它将在输出后省略新的行。 例如：

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

如果不指定 NoNewline  ，每个片段将出现在单独的行上：

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>使用改进的 Item cmdlet 与符号链接交互

为支持符号链接，扩展了 Item cmdlet 和几个相关 cmdlet。

### <a name="symbolic-link-files"></a>符号链接文件

在此示例中，我们在 C:\Temp 中创建一个名为 MySymLinkFile.txt 的新符号链接文件，该文件将链接到 $pshome\profile.ps1。 所有三个示例生成相同的结果。

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>符号链接目录

在此示例中，我们在 C:\Temp 中创建一个名为 MySymLinkDir 的新符号链接目录，该目录将链接到 $pshome 文件夹。 所有三个示例生成相同的结果。

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>硬链接

允许的路径  和名称  的相同组合如上所述。

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>目录联接

允许的路径  和名称  的相同组合如上所述。

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` 现在显示 Mode  属性中的“l”以指示符号链接文件或目录。

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Remove-Item

删除符号链接类似于删除任何其他项目类型。

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

使用 Force  参数可删除目标目录和符号链接中的文件。

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

有时必须在脚本中创建临时文件。 现在可以通过 `New-TemporaryFile` cmdlet 完成此操作：

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>PowerShell 网络交换机管理

在 WMF 5.0 中引入的网络交换机 cmdlet 让你能够将交换机、虚拟 LAN (VLAN) 和基本第 2 层网络交换机端口配置应用到 Windows Server 2012 R2 徽标认证的网络交换机。 通过使用这些 cmdlet，你可以执行：

- 全局交换机配置，如：
  - 设置主机名
  - 设置交换机横幅
  - 保留配置
  - 启用或禁用功能

- VLAN 配置：
  - 创建或删除 VLAN
  - 启用或禁用 VLAN
  - 枚举 VLAN
  - 为 VLAN 设置友好名称

- 第 2 层端口配置：
  - 枚举端口
  - 启用或禁用端口
  - 设置端口模式和属性
  - 添加或将 VLAN 关联到端口上的 Trunk 或 Access

有关详细信息，请参阅 [NetworkSwitchManager](/powershell/module/networkswitchmanager/) 文档。

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>基于 OData 终结点和 ODataUtils 生成 PowerShell cmdlet

ODataUtils 模块允许从支持 OData 的 REST 终结点生成 PowerShell cmdlet。 Microsoft.PowerShell.ODataUtils 模块包括以下功能：

- 将附加信息从服务器端终结点引导到客户端。
- 客户端分页支持
- 通过使用 -Select 参数进行的服务器端筛选
- 对 Web 请求标头的支持

由 `Export-ODataEndPointProxy` cmdlet 生成的代理 cmdlet 提供来自信息流上服务器端 OData 终结点的其他信息  。

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

在以下示例中，我们将检索热门产品并捕获 `$infoStream` 变量中的输出。

通过指定 IncludeTotalResponseCount  参数，我们将获得服务器上可用的所有产品  记录的总计数。

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

你可以使用客户端分页支持从服务器中分批获取记录。 当你必须通过网络从服务器获取大量数据时，这非常有用。

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

生成的代理 cmdlet 支持 Select  参数，你可以使用该参数作为筛选器以只接收客户端需要的记录属性。 在服务器端进行筛选，从而减少通过网络传输的数据量。

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

`Export-ODataEndpointProxy` cmdlet 以及由其生成的代理 cmdlet 现在支持 Headers  参数。 标头可用于通过通道传递 OData 终结点所需的其他信息。

在以下示例中，为 Headers  参数提供了包含订阅密钥的哈希表。 这是需要订阅密钥进行身份验证的服务的一个典型示例。

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
