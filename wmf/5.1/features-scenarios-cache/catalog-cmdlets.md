
---
标题：目录 Cmdlet 作者：jaimeo 参与者：？
---
# 目录 Cmdlet  

我们在 [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) 模块中新增了两个新 cmdlet 来生成和验证 windows 目录文件。  

New-FileCatalog 
--------------------------------

New File 目录用于为文件夹和文件集合创建 windows 目录文件。 目录文件包含指定路径中的所有文件的哈希值。 用户可以分发文件夹集合以及代表这些文件夹的对应的目录文件。 内容接收方可通过这些来验证自目录创建以来是否对文件夹进行了任何更改。    

```PowerShell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
我们支持创建目录版本 1 和 2。 版本 1 使用 SHA1 哈希算法来创建文件哈希值，版本 2 则使用 SHA256。 Windows Server 2008 R2 和 Windows 7 不支持目录版本 2。 如果使用的平台为 Windows 8、Windows Server 2012 及更高版本，则建议使用目录版本 2。  

![](../../images/NewFileCatalog.jpg)

这将创建目录文件。 

![](../../images/CatalogFile1.jpg)  

![](../../images/CatalogFile2.jpg) 

若要验证目录文件（上面示例中的 Pester.cat 文件）的完整性，应使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet 对其进行签名。   


Test-FileCatalog 
--------------------------------

Test File 目录用于验证代表一组文件夹的目录。 

```PowerShell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../../images/TestFileCatalog.jpg)

此 cmdlet 将目录中找到的所有文件的哈希值及其相对路径与磁盘中的进行比较。 如果它检测到文件哈希值和路径之间存在任何不匹配，将给出状态 ValidationFailed。 用户可以使用 *-Detailed* 标志检索所有该信息。 它还在“签名”字段中显示目录的签名状态，该结果与针对目录文件调用 [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet 的结果相同。 用户也可以使用 -FilesToSkip 参数在验证过程中跳过任何文件。 



<!--HONumber=Jul16_HO3-->


