# 适用于 Linux nxArchive 资源的 DSC

PowerShell Desired State Configuration (DSC) 中的 **nxArchive** 资源提供了在 Linux 节点上特定路径中解压存档（.tar、.zip）文件的机制。

## 语法

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## “属性”

|  属性 |  说明 | 
|---|---|
| SourcePath| 指定存档文件的源路径。 这应该是 .tar、.zip 或 .tar.gz 文件。 | 
| DestinationPath| 指定你想将存档内容提取至哪个位置。| 
| 校验和| 定义在确定是否已更新源存档时要使用的类型。 值为：“ctime”、“mtime”或“md5”。 默认值为“md5”。| 
| Force| 某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。 使用 **Force** 属性覆盖此类错误。 默认值为 **$false**。| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 
| Ensure| 确定是否要检查存档的内容是否位于**目标**上。 将此属性设置为“Present”可确保内容存在。 将其设置为“Absent”可确保内容不存在。 默认值为“Present”。| 

## 示例

以下示例表明如何使用 **nxArchive** 资源来确保名为 `website.tar` 的存档文件的内容存在，并将内容提取到指定的目标位置。

```
Import-DSCResource -Module nx 

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
} 
```
<!--HONumber=Feb16_HO4-->
