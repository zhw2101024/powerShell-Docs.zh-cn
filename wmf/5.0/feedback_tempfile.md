# New-TemporaryFile
有时必须在脚本中创建临时文件。 可以使用 **New-TemporaryFile** cmdlet 轻松实现此操作：

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp


<!--HONumber=Jun16_HO4-->


