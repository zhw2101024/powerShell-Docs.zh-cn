# 存档 cmdlet

两个新的 cmdlet **Compress-Archive** 和 **Expand-Archive** 可用于压缩和展开 ZIP 文档。

## Compress-Archive
**Compress-Archive** cmdlet 从指定文件创建新存档文件。 存档文件允许将多个文件打包，还可选择性地将其压缩为单个文件以便处理和存储。 可以使用 **-CompressionLevel** 参数中指定的压缩算法来压缩存档文件。
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## Expand-Archive
**Expand-Archive** cmdlet 从指定存档文件提取文件。 存档文件允许将多个文件打包，还可选择性地将其压缩为单个文件以便处理和存储。
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
<!--HONumber=Mar16_HO2-->
