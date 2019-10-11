---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux nxFile 资源的 DSC
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954824"
---
# <a name="dsc-for-linux-nxfile-resource"></a>适用于 Linux nxFile 资源的 DSC

PowerShell Desired State Configuration (DSC) 中的 nxFile  资源提供了管理 Linux 节点上的文件和目录的机制。

## <a name="syntax"></a>语法

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>“属性”

|属性 |说明 |
|---|---|
|DestinationPath |指定你想确保其中文件或目录状态的位置。 |
|SourcePath |指定要从其中复制文件或文件夹资源的路径。 此路径可以是本地路径，或者 `http/https/ftp` URL。 只有在 **Type** 属性的值为 **file** 时，才支持远程 `http/https/ftp` URL。 |
|类型 |指定正在配置的资源是目录还是文件。 将此属性设置为 **directory** 可指示该资源是一个目录。 将其设置为 **file** 可指示该资源是一个文件。 默认值为 **file**。 |
|目录 |指定文件的内容，例如特定字符串。 |
|校验和 |定义当确定两个文件是否相同时使用的类型。 如果未指定**校验和**，则只是文件或目录名用于比较。 值为：**ctime**、**mtime** 或 **md5**。 |
|Recurse |指示是否包含子目录。 将此属性设置为 `$true` 以指示你想要包含子目录。 默认值为 `$false`。 只有将 **Type** 属性设置为 **directory** 时，此属性才有效。 |
|Force |某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。 使用 **Force** 属性覆盖此类错误。 默认值为 `$false`。 |
|链接 |指定符号链接的所需行为。 将此属性设置为 **follow** 可跟随符号链接，并对链接目标进行操作。 例如，复制文件而不是链接。 将此属性设置为 **manage** 可对此链接进行操作。 例如，复制链接本身。 将此属性设置为 **ignore** 可忽略符号链接。 |
|组 |拥有对文件或目录的权限的 **Group** 的名称。 |
|模式 |以八进制或符号表示法指定资源的所需权限。 例如，**777** 或 **rwxrwxrwx**。 如果使用符号表示法，不需提供指示文件或目录的第一个字符。 |
|所有者 |拥有文件或目录的组的名称。 |

## <a name="common-properties"></a>公共属性

|属性 |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |确定是否要检查该文件是否存在。 将此属性设置为 **Present** 可确保文件存在。 将其设置为 **Absent** 可确保文件不存在。 默认值为 **Present**。 |

## <a name="additional-information"></a>其他信息

Linux 和 Windows 在文本文件中默认使用不同的换行符，这可能会导致在 Linux 计算机上使用 **nxFile** 配置某些文件时产生意外结果。 有多种管理 Linux 文件内容，同时避免由意外换行符引起问题的方法：

1. 从远程源（http、https 或 ftp）中复制文件

   使用所需内容在 Linux 上创建一个文件，并将其暂存于能够访问将配置的节点的网页或 ftp 服务器上。 然后使用该文件的 Web 或 ftp URL 在 **nxFile** 资源中定义 **SourcePath** 属性。

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. 设置 **$OFS** 属性以使用 Linux 换行符后，通过 [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) 来读取 PowerShell 脚本的内容。

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. 使用 PowerShell 函数以将 Windows 换行符替换为 Linux 换行符。

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a>示例

以下示例可确保目录 `/opt/mydir` 存在，并且具有指定内容的文件存在于此目录中。

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```